pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), meson.project_name())
moduledir = join_paths(pkgdatadir, meson.project_name())
gnome = import('gnome')

gnome.compile_resources(meson.project_name(),
	meson.project_name() + '.gresource.xml',
	gresource_bundle: true,
	install: true,
	install_dir: pkgdatadir,
)

python3 = import('python3')

conf = configuration_data()
conf.set('PYTHON', python3.find_python().path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', join_paths(get_option('prefix'), get_option('localedir')))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
	input: meson.project_name() + '.in',
	output: meson.project_name(),
	configuration: conf,
	install: true,
	install_dir: get_option('bindir')
)

drawing_sources = [
	'__init__.py',
	'main.py',

	'window.py',
	'deco_manager.py',
	'options_manager.py',
	'minimap.py',

	'image.py',
	'selection_manager.py',

	'utilities.py',
	'properties.py',
	'preferences.py',
	'message_dialog.py',
	'new_image_dialog.py',

	'optionsbars/abstract_optionsbar.py',
	'optionsbars/classic/optionsbar_classic.py',
	'optionsbars/classic/optionsbar_color_popover.py',
	'optionsbars/selection/optionsbar_selection.py',
	'optionsbars/canvas/optionsbar_crop.py',
	'optionsbars/canvas/optionsbar_filters.py',
	'optionsbars/canvas/optionsbar_rotate.py',
	'optionsbars/canvas/optionsbar_scale.py',
	'optionsbars/canvas/optionsbar_skew.py',

	'tools/abstract_tool.py',
	'tools/utilities_blur.py',
	'tools/utilities_overlay.py',
	'tools/utilities_paths.py',

	'tools/classic_tools/abstract_classic_tool.py',
	'tools/classic_tools/tool_arc.py',
	'tools/classic_tools/tool_eraser.py',
	'tools/classic_tools/tool_experiment.py',
	'tools/classic_tools/tool_highlight.py',
	'tools/classic_tools/tool_line.py',
	'tools/classic_tools/tool_paint.py',
	'tools/classic_tools/tool_pencil.py',
	'tools/classic_tools/tool_picker.py',
	'tools/classic_tools/tool_shape.py',
	'tools/classic_tools/tool_text.py',

	'tools/selection_tools/abstract_select.py',
	'tools/selection_tools/select_rect.py',
	'tools/selection_tools/select_free.py',
	'tools/selection_tools/select_color.py',

	'tools/canvas_tools/abstract_canvas_tool.py',
	'tools/canvas_tools/tool_crop.py',
	'tools/canvas_tools/tool_filters.py',
	'tools/canvas_tools/tool_rotate.py',
	'tools/canvas_tools/tool_scale.py',
	'tools/canvas_tools/tool_skew.py'
]

install_data(drawing_sources, install_dir: moduledir)
