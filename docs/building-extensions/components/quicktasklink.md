Quicktask Link
=======================

In general, a component has has one or more links to its views. They are defined in the manifest file and added to the menu during installation.

```xml title="A link to your component "
<administration>
	<menu>
		COM_EXAMPLE
	</menu>
	
	[..]
</administration>
```
For the main entries in the menu you can define an icon by including it in the language string. eg `COM_EXAMPLE="<i class='icon-address-book'></i> Example Component"`

Sometimes it is useful to add a so called <strong>quicktask link</strong> which enables an action calling from the menu without first visiting the Overview. It appears as an icon justified to the right hand side of the menu block. In general you should use an icon that clearly indicates the action relating to the view referenced by the main menu entry. It can also have a title which appears on mouseover. 

You can see this for Joomla core components, for example articles in com_content, here the quicktask is the plus icon and lets you add a new article in a single click.

Your menu link is added in the manfest file during installation.

## Quicktask Link and Title

A quicktask link and title are added as params to a menu item.

```xml title="Quicktask Link and icon"
	<menu link="option=com_example&amp;view=examples">
		COM_EXAMPLE
		<params>
			<menu-quicktask-title>COM_EXAMPLE_MENU_QUICKTASK_TITLE</menu-quicktask-title>
			<menu-quicktask>index.php?option=com_example&amp;view=example&amp;layout=edit</menu-quicktask>
		</params>
	</menu>

```
NB the title translation string needs to appear in the language `.sys.ini` file for the extension

## Quicktask Icon

The default icon is the '+' sign indicating create a new item as this is the most common usage in the built-in compponents. 

You can specify a different icon, either as a simple name for the built in common aliased icons (the `icon-` prefix will be automatically added), or as the font-awesome specification. 

```xml title="Qicktask Link and icon"
	<menu link="option=com_example&amp;view=examples">
		COM_EXAMPLE
		<params>
			<menu-quicktask-title>COM_EXAMPLE_MENU_QUICKTASK_TITLE</menu-quicktask-title>
			<menu-quicktask-icon>eye</menu-quicktask-icon>
			<menu-quicktask>index.php?option=com_example&amp;view=example&amp;layout=view</menu-quicktask>
		</params>
	</menu>
```

## Example 

This example shows a complete menu entry with dashboard, submenu and a two quicktasks. The first quicktask will use the default +plus icon. 
The second quicktask includes a fontawesome icon that has not been aliased as `icon-name` so is specified using the full fontawesome code.

```xml
		<menu>
			COM_EXAMPLE
			<params>
				<dashboard>example</dashboard>
			</params>
		</menu>
		<submenu>
			<menu link="option=com_example">
				COM_EXAMPLE_MENU
				<params>
					<menu-quicktask-title>COM_EXAMPLE_MENU_QUICKTASK_TITLE</menu-quicktask-title>
					<menu-quicktask>index.php?option=com_example&amp;view=example&amp;layout=edit</menu-quicktask>
				</params>
			</menu>
			<menu link="option=com_categories&amp;extension=com_example">
				COM_EXAMPLE_MENU_CATEGORIES
				<params>
					<menu-quicktask-title>COM_EXAMPLE_MENU_CATEGORIES</menu-quicktask-title>
					<menu-quicktask>index.php?option=com_categories&amp;view=category&amp;layout=edit&amp;extension=com_example</menu-quicktask>
				</params>
			</menu>
			<menu link="option=com_fields&amp;view=fields&amp;context=com_example,example">COM_EXAMPLE_MENU_FIELDS</menu>
			<menu-quicktask-icon>fas fa-person-hiking</menu-quicktask-icon>
			<menu link="option=com_fields&amp;view=groups&amp;context=com_example,example">COM_EXAMPLE_MENU_FIELDS_GROUP</menu>
		</submenu>

```
