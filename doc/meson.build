subdir('xml')

private_headers = [
    'config.h',
    'nbis-helpers.h',
    'fprint.h',

    # Subdirectories to ignore
    'drivers',
    'nbis',
]

html_images = [
]

content_files = [
  'intro.xml'
]

expand_content_files = content_files

glib_prefix = dependency('glib-2.0').get_variable(pkgconfig: 'prefix')
glib_docpath = join_paths(glib_prefix, 'share', 'gtk-doc', 'html')
docpath = join_paths(get_option('datadir'), 'gtk-doc', 'html')

gnome.gtkdoc(versioned_libname,
    main_xml: 'libfprint-docs.xml',
    src_dir: join_paths(meson.project_source_root(), 'libfprint'),
    include_directories: include_directories('../libfprint'),
    dependencies: libfprint_dep,
    content_files: content_files,
    expand_content_files: expand_content_files,
    ignore_headers: private_headers,
    gobject_typesfile: 'libfprint-2.types',
    fixxref_args: [
        '--html-dir=@0@'.format(docpath),
        '--extra-dir=@0@'.format(join_paths(glib_docpath, 'glib')),
        '--extra-dir=@0@'.format(join_paths(glib_docpath, 'gobject')),
    ],
    html_assets: html_images,
    install: true)
