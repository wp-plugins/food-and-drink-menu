Simple Admin Pages for WordPress
================================

Simple Admin Pages is a very small utility library to easily add new admin
pages to the WordPress admin interface. It simply collects WordPress' useful
Settings API into reuseable classes and implements a set of simple controls.

## General Controls Supported

- Text field
- Textarea field
- Checkbox (single option to enable/disable setting)
- Select dropdown with custom options
- Select dropdown of any post type
- Select dropdown of any taxonomy type

## Controls Supported for Special Use Cases

- Business Opening Hours

## Usage

```
	// Instantiate the Simple Admin Library
	$sap = sap_initialize_library(
		array(
			'version'		=> '1.0', // Version of the library
			'lib_url'		=> PLUGIN_URL . '/lib/simple-admin-pages/', // URL path to sap library
		)
	);

	// Create a page for the options under the Settings (options) menu
	$sap->add_page(
		'options', 				// Admin menu which this page should be added to
		array(					// Array of key/value pairs matching the AdminPage class constructor variables
			'id'			=> 'basic-settings',
			'title'			=> __( 'Page Title', TEXTDOMAIN ),
			'menu_title'	=> __( 'menu Title', TEXTDOMAIN ),
			'description'	=> '',
			'capability'	=> 'manage_options' // User permissions access level
		)
	);

	// Create a basic details section
	$sap->add_section(
		'basic-settings',	// Page to add this section to
		array(								// Array of key/value pairs matching the AdminPageSection class constructor variables
			'id'			=> 'basic-details',
			'title'			=> __( 'Basic Details', TEXTDOMAIN )
		)
	);

	// Create the options fields
	$sap->add_setting(
		'basic-settings',	// Page to add this setting to
		'basic-details',				// Section to add this setting to
		'select',							// Type of setting
		array(
			'id'			=> 'select-field',
			'title'			=> __( 'Select Field', TEXTDOMAIN ),
			'description'	=> __( 'A demonstration of the select field type.', TEXTDOMAIN ),
			'options'		=> array(
				'one' => __( 'Option 1', TEXTDOMAIN ),
				'two' => __( 'Option 2', TEXTDOMAIN ),
				'three' => __( 'Option 3', TEXTDOMAIN )
			)
		)
	);

	// Register all admin pages and settings with WordPress
	$sap->add_admin_menus();
```

## License

Simple Admin Pages is released under the GNU GPL 2 or later.

## Requirements

Simple Admin Pages has been tested with WordPress versions 3.5 and above, but it
will probably work with much earlier versions.

## Changelog

- 1.0 - 2013-11-20
	- Initial release
