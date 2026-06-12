---
title: "Gkrellm FMonitor install (make install)"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by p.becks on 2008-11-04
Hello all,

I am running ubuntu 8.10 (unetbootin-windows-282 install on a usb-stick, persistent home dir.). Linux 2.6.27-7-generic.

Now i am tring to make/make install a  File Monitor plugin for GKrellM. (gkrellm-fmonitor-2.0.4) To install i have to:

# to install fmonitor.so 
make
make install

When i make (as root) i get these errors:
******************************************************************
root@ubuntu:/home/ubuntu/Bureaublad/gkrellm-fmonitor-2.0.4# make

’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:284: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:285: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:288: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_scale_pixbuf_to_pixmap’
/usr/include/gkrellm2/gkrellm-public-proto.h:291: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:293: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_scale_piximage_to_pixmap’
/usr/include/gkrellm2/gkrellm-public-proto.h:296: error: expected declaration specifiers or ‘...’ before ‘GdkDrawable’
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:297: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:298: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:300: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_scale_theme_background’
/usr/include/gkrellm2/gkrellm-public-proto.h:305: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_clone_pixmap’
/usr/include/gkrellm2/gkrellm-public-proto.h:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_clone_bitmap’
/usr/include/gkrellm2/gkrellm-public-proto.h:307: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:308: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:313: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:314: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_set_gkrellmrc_piximage_border’
/usr/include/gkrellm2/gkrellm-public-proto.h:316: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_get_gkrellmrc_integer’
/usr/include/gkrellm2/gkrellm-public-proto.h:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:318: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_get_gkrellmrc_piximage_border’
/usr/include/gkrellm2/gkrellm-public-proto.h:323: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:325: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:327: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:329: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:330: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:339: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_using_default_theme’
/usr/include/gkrellm2/gkrellm-public-proto.h:340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_get_theme_scale’
/usr/include/gkrellm2/gkrellm-public-proto.h:342: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_config_window_shown’
/usr/include/gkrellm2/gkrellm-public-proto.h:347: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:347: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:348: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_style_is_themed’
/usr/include/gkrellm2/gkrellm-public-proto.h:349: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:350: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:351: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:351: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:356: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:361: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:361: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:362: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:362: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:362: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:363: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:366: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:372: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_alert_is_activated’
/usr/include/gkrellm2/gkrellm-public-proto.h:374: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:374: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:376: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gkrellm2/gkrellm-public-proto.h:378: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gkrellm2/gkrellm-public-proto.h:380: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gkrellm2/gkrellm-public-proto.h:382: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gkrellm2/gkrellm-public-proto.h:384: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gkrellm2/gkrellm-public-proto.h:386: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_alert_decal_visible’
/usr/include/gkrellm2/gkrellm-public-proto.h:389: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:389: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:390: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:392: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:392: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:393: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:393: error: expected declaration specifiers or ‘...’ before ‘gfloat’
/usr/include/gkrellm2/gkrellm-public-proto.h:394: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:395: error: expected declaration specifiers or ‘...’ before ‘gint’

/usr/include/gkrellm2/gkrellm-public-proto.h:396: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:396: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:398: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:398: error: expected declaration specifiers or ‘...’ before ‘gboolean’
/usr/include/gkrellm2/gkrellm-public-proto.h:402: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:408: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:411: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:413: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gkrellm2/gkrellm-public-proto.h:416: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_alert_plugin_get_data’
/usr/include/gkrellm2/gkrellm-public-proto.h:419: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:419: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:419: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_add_chart_style’
/usr/include/gkrellm2/gkrellm-public-proto.h:425: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_add_meter_style’
/usr/include/gkrellm2/gkrellm-public-proto.h:426: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_lookup_chart_style_id’
/usr/include/gkrellm2/gkrellm-public-proto.h:427: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_lookup_meter_style_id’
/usr/include/gkrellm2/gkrellm-public-proto.h:431: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:432: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:433: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:454: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:455: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:456: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:457: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:458: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:459: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:460: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:461: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:466: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:467: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:468: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:469: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:470: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:471: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:472: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:473: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_demo_mode’
/usr/include/gkrellm2/gkrellm-public-proto.h:474: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_update_HZ’
/usr/include/gkrellm2/gkrellm-public-proto.h:475: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:476: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_get_timer_ticks’
/usr/include/gkrellm2/gkrellm-public-proto.h:478: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_plugin_debug’
/usr/include/gkrellm2/gkrellm-public-proto.h:484: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_plugin_export_label’
/usr/include/gkrellm2/gkrellm-public-proto.h:487: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/gkrellm2/gkrellm-public-proto.h:488: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:496: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:497: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:499: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:500: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:503: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:505: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:508: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:510: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:515: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:517: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:519: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:522: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:524: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:525: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:527: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:535: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_dup_string’
/usr/include/gkrellm2/gkrellm-public-proto.h:537: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_locale_dup_string’
/usr/include/gkrellm2/gkrellm-public-proto.h:538: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:539: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:542: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_125_sequence’
/usr/include/gkrellm2/gkrellm-public-proto.h:552: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_smp_cpus’
/usr/include/gkrellm2/gkrellm-public-proto.h:553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_cpu_stats’
/usr/include/gkrellm2/gkrellm-public-proto.h:558: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_disk_temperature_display’
/usr/include/gkrellm2/gkrellm-public-proto.h:560: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:565: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_net_routes’
/usr/include/gkrellm2/gkrellm-public-proto.h:566: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_net_stats’
/usr/include/gkrellm2/gkrellm-public-proto.h:567: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_get_mail_mute_mode’
/usr/include/gkrellm2/gkrellm-public-proto.h:574: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_add_external_mbox’
/usr/include/gkrellm2/gkrellm-public-proto.h:577: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:582: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_client_mode’
/usr/include/gkrellm2/gkrellm-public-proto.h:583: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:586: error: expected declaration specifiers or ‘...’ before ‘gchar’
/usr/include/gkrellm2/gkrellm-public-proto.h:586: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:587: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:589: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_client_send_to_server’
/usr/include/gkrellm2/gkrellm-public-proto.h:590: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_client_check_server_version’
/usr/include/gkrellm2/gkrellm-public-proto.h:594: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:597: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_gdk_string_width’
/usr/include/gkrellm2/gkrellm-public-proto.h:602: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_gdk_string_markup_width’
/usr/include/gkrellm2/gkrellm-public-proto.h:603: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_gdk_text_width’
/usr/include/gkrellm2/gkrellm-public-proto.h:605: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gkrellm_gdk_text_markup_width’
/usr/include/gkrellm2/gkrellm-public-proto.h:607: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:610: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:613: error: expected ‘)’ before ‘*’ token
/usr/include/gkrellm2/gkrellm-public-proto.h:616: error: expected ‘)’ before ‘*’ token
fmonitor.c:90: error: expected specifier-qualifier-list before ‘gchar’
fmonitor.c:115: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘style_id’
fmonitor.c:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_update’
fmonitor.c:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
fmonitor.c:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
fmonitor.c:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
fmonitor.c:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
fmonitor.c:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
fmonitor.c:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘panel_expose_event’
fmonitor.c:155: error: expected ‘)’ before ‘*’ token
fmonitor.c: In function ‘destroy_decal’:
fmonitor.c:173: error: ‘GkrellmPanel’ has no member named ‘decal_list’
fmonitor.c:173: warning: implicit declaration of function ‘g_list_remove’
fmonitor.c:173: error: ‘GkrellmPanel’ has no member named ‘decal_list’
fmonitor.c: In function ‘update_plugin’:
fmonitor.c:189: error: ‘FALSE’ undeclared (first use in this function)
fmonitor.c:189: error: (Each undeclared identifier is reported only once
fmonitor.c:189: error: for each function it appears in.)
fmonitor.c:192: error: ‘GkrellmTicks’ has no member named ‘timer_ticks’
fmonitor.c:193: error: too many arguments to function ‘gkrellm_draw_decal_pixmap’
fmonitor.c:194: error: ‘TRUE’ undeclared (first use in this function)
fmonitor.c:201: error: ‘GkrellmTicks’ has no member named ‘second_tick’
fmonitor.c:205: error: ‘force_update’ undeclared (first use in this function)
fmonitor.c:206: error: ‘style_id’ undeclared (first use in this function)
fmonitor.c:211: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:214: error: ‘fm_data’ has no member named ‘ticker’
fmonitor.c:215: error: ‘fm_data’ has no member named ‘ticker’
fmonitor.c:220: error: ‘GkrellmPanel’ has no member named ‘h’
fmonitor.c:222: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:224: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:226: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:261: error: ‘ledp’ undeclared (first use in this function)
fmonitor.c:261: error: ‘ledm’ undeclared (first use in this function)
fmonitor.c:261: error: too many arguments to function ‘gkrellm_create_decal_pixmap’
fmonitor.c:262: error: ‘GkrellmStyle’ has no member named ‘margin’
fmonitor.c:264: warning: passing argument 2 of ‘gkrellm_create_decal_text’ from incompatible pointer type
fmonitor.c:264: warning: passing argument 3 of ‘gkrellm_create_decal_text’ from incompatible pointer type
fmonitor.c:264: error: too many arguments to function ‘gkrellm_create_decal_text’
fmonitor.c:270: warning: passing argument 2 of ‘gkrellm_create_decal_text’ from incompatible pointer type
fmonitor.c:270: warning: passing argument 3 of ‘gkrellm_create_decal_text’ from incompatible pointer type
fmonitor.c:270: error: too many arguments to function ‘gkrellm_create_decal_text’
fmonitor.c:271: error: ‘GkrellmDecal’ has no member named ‘x’
fmonitor.c:271: warning: implicit declaration of function ‘gkrellm_chart_width’
fmonitor.c:272: error: ‘GkrellmDecal’ has no member named ‘w’
fmonitor.c:272: error: ‘GkrellmStyle’ has no member named ‘margin’
fmonitor.c:274: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:275: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:276: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:277: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:278: error: ‘GkrellmDecal’ has no member named ‘y’
fmonitor.c:278: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:294: error: too many arguments to function ‘gkrellm_draw_decal_pixmap’
fmonitor.c:296: error: too many arguments to function ‘gkrellm_draw_decal_text’
fmonitor.c:297: error: too many arguments to function ‘gkrellm_draw_decal_text’
fmonitor.c:300: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:309: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:310: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:311: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:321: error: too many arguments to function ‘gkrellm_panel_configure’
fmonitor.c:322: warning: implicit declaration of function ‘gkrellm_panel_create’
fmonitor.c:322: error: ‘fm_vbox’ undeclared (first use in this function)
fmonitor.c:323: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:325: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:325: error: too many arguments to function ‘gkrellm_draw_decal_text’
fmonitor.c:329: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:331: error: ‘fm_data’ has no member named ‘text’
fmonitor.c: At top level:
fmonitor.c:342: error: expected ‘)’ before ‘*’ token
fmonitor.c: In function ‘create_fm_panels’:
fmonitor.c:375: error: ‘style_id’ undeclared (first use in this function)
fmonitor.c:380: warning: implicit declaration of function ‘gkrellm_load_piximage’
fmonitor.c:381: warning: implicit declaration of function ‘gkrellm_scale_piximage_to_pixmap’
fmonitor.c:381: error: ‘ledp’ undeclared (first use in this function)
fmonitor.c:381: error: ‘ledm’ undeclared (first use in this function)
fmonitor.c:393: error: ‘GkrellmPanel’ has no member named ‘textstyle’
fmonitor.c:396: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:398: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:398: warning: passing argument 3 of ‘gkrellm_create_decal_text’ from incompatible pointer type
fmonitor.c:398: error: too many arguments to function ‘gkrellm_create_decal_text’
fmonitor.c:399: error: ‘GkrellmDecal’ has no member named ‘y’
fmonitor.c:399: error: ‘GkrellmDecal’ has no member named ‘h’
fmonitor.c:402: error: too many arguments to function ‘gkrellm_get_top_bottom_margins’
fmonitor.c:404: error: too many arguments to function ‘gkrellm_panel_configure’
fmonitor.c:406: error: ‘fm_vbox’ undeclared (first use in this function)
fmonitor.c:408: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:410: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:410: error: too many arguments to function ‘gkrellm_draw_decal_text’
fmonitor.c:413: warning: implicit declaration of function ‘gtk_signal_connect’
fmonitor.c:413: warning: implicit declaration of function ‘GTK_OBJECT’
fmonitor.c:413: error: ‘GkrellmPanel’ has no member named ‘drawing_area’
fmonitor.c:414: error: ‘GtkSignalFunc’ undeclared (first use in this function)
fmonitor.c:414: error: expected ‘)’ before ‘panel_expose_event’
fmonitor.c: At top level:
fmonitor.c:425: error: expected ‘)’ before ‘*’ token
fmonitor.c:447: error: expected ‘)’ before ‘*’ token
fmonitor.c:462: error: expected ‘)’ before ‘*’ token
fmonitor.c:507: error: expected ‘)’ before ‘*’ token
fmonitor.c:517: error: expected ‘)’ before ‘*’ token
fmonitor.c: In function ‘save_config’:
fmonitor.c:662: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:662: error: ‘fm_data’ has no member named ‘text’
fmonitor.c: At top level:
fmonitor.c:669: error: expected ‘)’ before ‘*’ token
fmonitor.c: In function ‘del_fmc_entries’:
fmonitor.c:708: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:708: warning: implicit declaration of function ‘g_free’
fmonitor.c:708: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:708: error: ‘fm_data’ has no member named ‘text’
fmonitor.c: In function ‘run_update_cmds’:
fmonitor.c:723: warning: implicit declaration of function ‘g_strdup’
fmonitor.c:723: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:723: warning: assignment makes pointer from integer without a cast
fmonitor.c:732: error: ‘fm_data’ has no member named ‘pid’
fmonitor.c:737: error: ‘fm_data’ has no member named ‘text’
fmonitor.c: In function ‘kill_update_cmds’:
fmonitor.c:752: error: ‘fm_data’ has no member named ‘pid’
fmonitor.c:754: error: ‘fm_data’ has no member named ‘pid’
fmonitor.c: In function ‘apply_config’:
fmonitor.c:770: warning: implicit declaration of function ‘item_unsel’
fmonitor.c:770: warning: implicit declaration of function ‘GTK_WIDGET’
fmonitor.c:770: error: ‘config_list’ undeclared (first use in this function)
fmonitor.c:776: warning: implicit declaration of function ‘gtk_clist_get_text’
fmonitor.c:776: warning: implicit declaration of function ‘GTK_CLIST’
fmonitor.c:779: error: ‘fm_data’ has no member named ‘text’
fmonitor.c:781: error: ‘fm_data’ has no member named ‘ticker’
fmonitor.c:788: error: ‘force_update’ undeclared (first use in this function)
fmonitor.c:788: error: ‘TRUE’ undeclared (first use in this function)
fmonitor.c: At top level:
fmonitor.c:803: warning: excess elements in struct initializer
fmonitor.c:803: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:804: warning: excess elements in struct initializer
fmonitor.c:804: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:805: error: ‘create_plugin’ undeclared here (not in a function)
fmonitor.c:805: warning: excess elements in struct initializer
fmonitor.c:805: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:806: warning: excess elements in struct initializer
fmonitor.c:806: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:807: error: ‘create_config_tab’ undeclared here (not in a function)
fmonitor.c:807: warning: excess elements in struct initializer
fmonitor.c:807: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:808: warning: excess elements in struct initializer
fmonitor.c:808: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:810: warning: excess elements in struct initializer
fmonitor.c:810: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:811: error: ‘load_config’ undeclared here (not in a function)
fmonitor.c:811: warning: excess elements in struct initializer
fmonitor.c:811: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:812: warning: excess elements in struct initializer
fmonitor.c:812: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:814: warning: excess elements in struct initializer
fmonitor.c:814: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:815: warning: excess elements in struct initializer
fmonitor.c:815: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:816: warning: excess elements in struct initializer
fmonitor.c:816: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:818: warning: excess elements in struct initializer
fmonitor.c:818: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:820: warning: excess elements in struct initializer
fmonitor.c:820: warning: (near initialization for ‘plugin_mon’)
fmonitor.c:822: warning: excess elements in struct initializer
fmonitor.c:822: warning: (near initialization for ‘plugin_mon’)
fmonitor.c: In function ‘gkrellm_init_plugin’:
fmonitor.c:832: error: ‘style_id’ undeclared (first use in this function)
fmonitor.c:832: warning: implicit declaration of function ‘gkrellm_add_meter_style’
make: *** [fmonitor.o] Error 1
root@ubuntu:/home/ubuntu/Bureaublad/gkrellm-fmonitor-2.0.4# 

********************************************************************

When i make install i get this:

********************************************************************

root@ubuntu:/home/ubuntu/Bureaublad/gkrellm-fmonitor-2.0.4# make install
cp fmonitor.so /usr/local/lib/gkrellm2/plugins
cp: cannot stat `fmonitor.so': No such file or directory
make: *** [install] Error 1
root@ubuntu:/home/ubuntu/Bureaublad/gkrellm-fmonitor-2.0.4# 
************************************************************************

Anyone any ideas?

---

### Post by spiderbatdad on 2008-11-04
First, get out of the root session. Don't run make as root in Ubuntu, and avoid root sessions unless you have a good reason. Instead use sudo in front of command that require administrative privileges...in this case 'make install' but not make. So...```
make
sudo make install
```Obviously it isn't making correctly, and I'm not sure why, but assume you don't have all the tools for the job...like build-essential? So I would try ```
sudo apt-get install build-essential
```Then proceed with compiling the source code.

---

### Post by p.becks on 2008-11-04
I do have the essentials installed and i followed your guideline but with the same results..

:-(

---

