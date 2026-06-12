---
title: "Nautilus folder view customizations lost"
date: 2009-07-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-18
Lately nautilus no longer remembers a folder's view (i.e icon, list, compact). Also when selecting View > Visible Columns.. Any changes made are ignored and not applied.

No files are being created or modified in ~/.nautilus/metafiles. I backed this folder up, deleted it and logged out. Logged back in and let nautilus recreate it. No metafiles subdirectory is created.

Also reinstalled nautilus to see if that would nudge it to start saving metadata to no avail?  Recent changelog shows the following:

> nautilus (1:2.27.4-0ubuntu1) karmic; urgency=low

  * New upstream release: (LP: #399131)
  
    - Use the new GVfs metadata framework

Could this change be related to the issue?. I am not really familiar with the workings of GVfs. Any one else seeing this issue or just me?

---

### Post by tekstr1der on 2009-07-18
Looking into this further, I see there are some major changes to nautilus concerning metadata relying on GVfs.

> gvfs (1.3.2-0ubuntu1) karmic; urgency=low

  [ Robert Ancell ]
  * New upstream release: (LP: #399142)
    - metadata-store: initial implementation
    - gvfs-ls: add a -n option to gvfs-ls for nofollow-symlinks
    - gvfsd-computer: better handling of PC floppy drives
    - ftp: EPTR support
    - cdda: Support gudev (and prefer it instead of hal)
    - Add support user interaction when unmounting mounts (gdu, gphoto2)
    - Add support starting/stopping drives (gdu monitor)
    - Fix 'make distcheck'
    - Bugs fixed: 582175, 516704, 586280, 585853, 582772, 585591, 587484
  * debian/patches/02-cdda-backend-support-and-prefer-gudev.patch:
  * debian/patches/05-conditionalize-hal-support-in-obexftp-backend.patch:
  * debian/patches/90_git_change_fix_computer_crash.patch:
    - Applied upstream
  * debian/patches/01_maintainer_mode.patch
  * debian/patches/90_relibtoolize.patch
    - Refreshed


```
+#include <config.h>
+#include "nautilus-metadata.h"
+#include <glib.h>
+
+static char *used_metadata_names[] = {
+ NAUTILUS_METADATA_KEY_DEFAULT_COMPONENT,
+ NAUTILUS_METADATA_KEY_LOCATION_BACKGROUND_COLOR,
+ NAUTILUS_METADATA_KEY_LOCATION_BACKGROUND_IMAGE,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_ZOOM_LEVEL,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_AUTO_LAYOUT,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_TIGHTER_LAYOUT,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_SORT_BY,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_SORT_REVERSED,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_KEEP_ALIGNED,
+ NAUTILUS_METADATA_KEY_ICON_VIEW_LAYOUT_TIMESTAMP,
+ NAUTILUS_METADATA_KEY_LIST_VIEW_ZOOM_LEVEL,
+ NAUTILUS_METADATA_KEY_LIST_VIEW_SORT_COLUMN,
+ NAUTILUS_METADATA_KEY_LIST_VIEW_SORT_REVERSED,
+ NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS,
+ NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER,
+ NAUTILUS_METADATA_KEY_COMPACT_VIEW_ZOOM_LEVEL,
+ NAUTILUS_METADATA_KEY_WINDOW_GEOMETRY,
+ NAUTILUS_METADATA_KEY_WINDOW_SCROLL_POSITION,
+ NAUTILUS_METADATA_KEY_WINDOW_SHOW_HIDDEN_FILES,
+ NAUTILUS_METADATA_KEY_WINDOW_MAXIMIZED,
+ NAUTILUS_METADATA_KEY_WINDOW_STICKY,
+ NAUTILUS_METADATA_KEY_WINDOW_KEEP_ABOVE,
+ NAUTILUS_METADATA_KEY_SIDEBAR_BACKGROUND_COLOR,
+ NAUTILUS_METADATA_KEY_SIDEBAR_BACKGROUND_IMAGE,
+ NAUTILUS_METADATA_KEY_SIDEBAR_BUTTONS,
+ NAUTILUS_METADATA_KEY_ANNOTATION,
+ NAUTILUS_METADATA_KEY_ICON_POSITION,
+ NAUTILUS_METADATA_KEY_ICON_POSITION_TIMESTAMP,
+ NAUTILUS_METADATA_KEY_ICON_SCALE,
+ NAUTILUS_METADATA_KEY_CUSTOM_ICON,
+ NAUTILUS_METADATA_KEY_SCREEN,
+ NAUTILUS_METADATA_KEY_KEYWORD,
+ NULL
+};
+
+guint
+nautilus_metadata_get_id (const char *metadata)
+{
+ static GHashTable *hash;
+ int i;
+
+ if (hash == NULL)
+ {
+ hash = g_hash_table_new (g_str_hash, g_str_equal);
+ for (i = 0; used_metadata_names[i] != NULL; i++)
+ g_hash_table_insert (hash,
+ used_metadata_names[i],
+ GINT_TO_POINTER (i + 1));
+ }
+
+ return GPOINTER_TO_INT (g_hash_table_lookup (hash, metadata));
+}
diff --git a/libnautilus-private/nautilus-metadata.h
b/libnautilus-private/nautilus-metadata.h
index be19f7c..ffebddb 100644
--- a/libnautilus-private/nautilus-metadata.h
+++ b/libnautilus-private/nautilus-metadata.h
@@ -27,11 +27,12 @@

/* Keys for getting/setting Nautilus metadata. All metadata used in Nautilus
* should define its key here, so we can keep track of the whole set easily.
+ * Any updates here needs to be added in nautilus-metadata.c too.
*/

-/* Per-file */
+#include <glib.h>

-#define NAUTILUS_METADATA_KEY_CONTENT_VIEWS "content_views"
+/* Per-file */

#define NAUTILUS_METADATA_KEY_DEFAULT_COMPONENT
"default_component"

@@ -51,7 +52,6 @@
#define NAUTILUS_METADATA_KEY_LIST_VIEW_SORT_REVERSED
"list_view_sort_reversed"
#define NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS
"list_view_visible_columns"
#define NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER
"list_view_column_order"
-#define NAUTILUS_METADATA_SUBKEY_COLUMNS "columns"

#define NAUTILUS_METADATA_KEY_COMPACT_VIEW_ZOOM_LEVEL
"compact_view_zoom_level"

@@ -65,8 +65,6 @@
#define NAUTILUS_METADATA_KEY_SIDEBAR_BACKGROUND_COLOR
"sidebar_background_color"
#define NAUTILUS_METADATA_KEY_SIDEBAR_BACKGROUND_IMAGE
"sidebar_background_tile_image"
#define NAUTILUS_METADATA_KEY_SIDEBAR_BUTTONS
"sidebar_buttons"
-#define NAUTILUS_METADATA_KEY_SIDEBAR_TAB_COLOR
"sidebar_tab_color"
-#define NAUTILUS_METADATA_KEY_SIDEBAR_TITLE_TAB_COLOR
"sidebar_title_tab_color"

#define NAUTILUS_METADATA_KEY_ANNOTATION "annotation"
#define NAUTILUS_METADATA_KEY_ICON_POSITION "icon_position"
@@ -74,9 +72,9 @@
#define NAUTILUS_METADATA_KEY_ICON_SCALE "icon_scale"
#define NAUTILUS_METADATA_KEY_CUSTOM_ICON "custom_icon"
#define NAUTILUS_METADATA_KEY_SCREEN "screen"
+#define NAUTILUS_METADATA_KEY_KEYWORD "keyword"

-/* per link file */

-#define NAUTILUS_METADATA_KEY_EXTRA_TEXT "extra_text"
+guint nautilus_metadata_get_id (const char *metadata);

#endif /* NAUTILUS_METADATA_H */
diff --git a/src/file-manager/fm-list-view.c b/src/file-manager/fm-list-view.c
index 86f6ebd..c82de19 100644
--- a/src/file-manager/fm-list-view.c
+++ b/src/file-manager/fm-list-view.c
@@ -1533,8 +1533,7 @@ get_visible_columns (FMListView *list_view)

visible_columns = nautilus_file_get_metadata_list
(file,
- NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS,
- NAUTILUS_METADATA_SUBKEY_COLUMNS);
+ NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS);

if (visible_columns) {
GPtrArray *res;
@@ -1565,8 +1564,7 @@ get_column_order (FMListView *list_view)

column_order = nautilus_file_get_metadata_list
(file,
- NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER,
- NAUTILUS_METADATA_SUBKEY_COLUMNS);
+ NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER);

if (column_order) {
GPtrArray *res;
@@ -2051,7 +2049,6 @@ column_chooser_changed_callback (NautilusColumnChooser
*chooser,
list = g_list_reverse (list);
nautilus_file_set_metadata_list (file,

NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS,
- NAUTILUS_METADATA_SUBKEY_COLUMNS,
list);
g_list_free (list);

@@ -2062,7 +2059,6 @@ column_chooser_changed_callback (NautilusColumnChooser
*chooser,
list = g_list_reverse (list);
nautilus_file_set_metadata_list (file,

NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER,
- NAUTILUS_METADATA_SUBKEY_COLUMNS,
list);
g_list_free (list);

@@ -2105,8 +2101,8 @@ column_chooser_use_default_callback
(NautilusColumnChooser *chooser,
file = fm_directory_view_get_directory_as_file
(FM_DIRECTORY_VIEW (view));

- nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER, NAUTILUS_METADATA_SUBKEY_COLUMNS,
NULL);
- nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS,
NAUTILUS_METADATA_SUBKEY_COLUMNS, NULL);
+ nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER, NULL);
+ nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS, NULL);

set_columns_settings_from_metadata_and_preferences (FM_LIST_VIEW
(view));
column_chooser_set_from_settings (chooser, view);
@@ -2279,8 +2275,8 @@ fm_list_view_reset_to_defaults (FMDirectoryView *view)
nautilus_file_set_metadata (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_SORT_COLUMN, NULL, NULL);
nautilus_file_set_metadata (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_SORT_REVERSED, NULL, NULL);
nautilus_file_set_metadata (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_ZOOM_LEVEL, NULL, NULL);
- nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER, NAUTILUS_METADATA_SUBKEY_COLUMNS,
NULL);
- nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS,
NAUTILUS_METADATA_SUBKEY_COLUMNS, NULL);
+ nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_COLUMN_ORDER, NULL);
+ nautilus_file_set_metadata_list (file,
NAUTILUS_METADATA_KEY_LIST_VIEW_VISIBLE_COLUMNS, NULL);

gtk_tree_sortable_set_sort_column_id
(GTK_TREE_SORTABLE (FM_LIST_VIEW (view)->details->model),
```

I am not seeing any metadata for any of my files:

```
$ gvfs-info -a "metadata::*" ~/testfile
attributes:
```

Can someone please confirm that they can get nautilus to successfully apply and retain column view changes? I don't see any bug filed on this, so I suspect it's something local to my system.

---

### Post by nIRV on 2009-07-18
Since my laptop got updated to latest version of nautlius & gvfs in Karmic:
- Position of icons on my desktop are lost when logging out of session or rebooting
- Emblems of icons set prior to update lost
- Emblems can't be applied to icons

I've searched around (both on bugzilla.gnome.org and launchpad) but did not find any relevant bug(s) to problems listed above.

---

### Post by tekstr1der on 2009-07-19
Popped in a daily build live CD and experienced all the same nautilus behavior I originally reported. Folder view settings are ignored and/or lost. Columns headers cannot be changed.

Anyone here running Karmic with Gnome? Maybe someone could confirm the issues listed in the first post so I can submit a bug to launchpad?

---

### Post by taavikko on 2009-07-19
> **tekstr1der said:**
> 
Anyone here running Karmic with Gnome? Maybe someone could confirm the issues listed in the first post so I can submit a bug to launchpad?

You don't need confirmation on other users to report a bug.
Please do so immediately.

EDIT: Tried to add few visible columns to view, didn't stick.
Tried to change the size of nautilus window, didn't stick (after restarting browser-window).

---

### Post by tekstr1der on 2009-07-19
Thanks anyway for confirming. Appreciate it. Filed [Bug #401414: Nautilus visible columns cannot be modified]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/401414").

Testing a lot of prerelease software, I find it best to be sure an apparant bug affects others and is not a result of local bustage. Knowing that a bug is indeed a bug before filing will help the process along without creating yet more noise for triagers who sort through tons of bug reports every day.

---

### Post by tekstr1der on 2009-07-20
While the specific bug I filed is not yet fixed, the other issues mentioned in this thread seem to be resolved with the latest gvfs updates:

Nautilus remembers view (icon, list, compact) per folder.
Nautilus remembers window size after closing and reopening.

---

### Post by tekstr1der on 2009-07-20
It's good to see this working. Much nicer solution than adding all those xml files in your home directory.

```

$ gvfs-info ~/Videos | grep metadata
  metadata::annotation: 
  metadata::default_component: OAFIID:Nautilus_File_Manager_Icon_View
  metadata::icon_view_auto_layout: true
  metadata::icon_view_tighter_layout: false
  metadata::keyword: [videos]
  metadata::list_view_sort_column: name
  metadata::list_view_sort_reversed: false
  metadata::list_view_zoom_level: 0
```

@nIRV: emblems are sticking again as well

---

