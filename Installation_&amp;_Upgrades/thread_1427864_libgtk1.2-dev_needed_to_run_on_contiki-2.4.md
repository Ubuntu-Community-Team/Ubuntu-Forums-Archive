---
title: "libgtk1.2-dev needed to run on contiki-2.4"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by Kavkaz86 on 2010-03-12
Hi i am using contiki-2.4 on ubuntu 9.10. however I need libgtk1.2-dev. I have libgtk2.0-dev ... I get the following error. is there a possible solution for this? 

--
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/net/ethernode-uip.c -o obj_netsim/ethernode-uip.o
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/dev/lpm.c -o obj_netsim/lpm.o
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/dev/rs232.c -o obj_netsim/rs232.o
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/dev/flash.c -o obj_netsim/flash.o
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/./node.c -o obj_netsim/node.o
../../platform/netsim/./node.c: In function ‘node_log’:
../../platform/netsim/./node.c:149: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/./nodes.c -o obj_netsim/nodes.o
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/./sensor.c -o obj_netsim/sensor.o
make: gtk-config: Command not found
gcc -DCONTIKI_TARGET_NETSIM -Wall -g -I/usr/local/include  -O  -DNETSIM=1  -I. -I../../platform/netsim/. -I../../platform/netsim/dev -I../../platform/netsim/apps -I../../platform/netsim/net -I../../cpu/native/. -I../../cpu/native/net -I../../core/dev -I../../core/lib -I../../core/net -I../../core/net/mac -I../../core/net/rime -I../../core/net/routing -I../../core/sys -I../../core/cfs -I../../core/ctk -I../../core/lib/ctk -I../../core/loader -I../../core/. -MMD -c ../../platform/netsim/./display.c -o obj_netsim/display.o
../../platform/netsim/./display.c:42:21: warning: gtk/gtk.h: No such file or directory
../../platform/netsim/./display.c:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:84: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c: In function ‘display_redraw’:
../../platform/netsim/./display.c:105: warning: implicit declaration of function ‘gdk_draw_rectangle’
../../platform/netsim/./display.c:105: error: ‘pixmap’ undeclared (first use in this function)
../../platform/netsim/./display.c:105: error: (Each undeclared identifier is reported only once
../../platform/netsim/./display.c:105: error: for each function it appears in.)
../../platform/netsim/./display.c:106: error: ‘white’ undeclared (first use in this function)
../../platform/netsim/./display.c:107: error: ‘TRUE’ undeclared (first use in this function)
../../platform/netsim/./display.c:109: error: ‘drawing_area’ undeclared (first use in this function)
../../platform/netsim/./display.c:129: warning: implicit declaration of function ‘gdk_draw_arc’
../../platform/netsim/./display.c:130: error: ‘red’ undeclared (first use in this function)
../../platform/netsim/./display.c:131: error: ‘FALSE’ undeclared (first use in this function)
../../platform/netsim/./display.c:170: warning: implicit declaration of function ‘gdk_draw_string’
../../platform/netsim/./display.c:171: error: ‘font’ undeclared (first use in this function)
../../platform/netsim/./display.c:172: error: ‘black’ undeclared (first use in this function)
../../platform/netsim/./display.c:192: error: ‘green’ undeclared (first use in this function)
../../platform/netsim/./display.c:200: error: ‘yellow’ undeclared (first use in this function)
../../platform/netsim/./display.c:215: warning: implicit declaration of function ‘gdk_draw_line’
../../platform/netsim/./display.c:246: error: ‘intensity_gcs’ undeclared (first use in this function)
../../platform/netsim/./display.c:255: warning: implicit declaration of function ‘gtk_widget_draw’
../../platform/netsim/./display.c: At top level:
../../platform/netsim/./display.c:313: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘configure_event’
../../platform/netsim/./display.c:340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘expose_event’
../../platform/netsim/./display.c:353: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘key_press_event’
../../platform/netsim/./display.c:376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘key_release_event’
../../platform/netsim/./display.c:382: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘button_press_event’
../../platform/netsim/./display.c:431: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pointer_motion_event’
../../platform/netsim/./display.c: In function ‘quit’:
../../platform/netsim/./display.c:490: warning: implicit declaration of function ‘gtk_exit’
../../platform/netsim/./display.c: At top level:
../../platform/netsim/./display.c:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘idle_callback’
../../platform/netsim/./display.c:501: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../platform/netsim/./display.c:524: error: expected ‘)’ before ‘data’
../../platform/netsim/./display.c: In function ‘display_init’:
../../platform/netsim/./display.c:538: error: ‘GtkWidget’ undeclared (first use in this function)
../../platform/netsim/./display.c:538: error: ‘window’ undeclared (first use in this function)
../../platform/netsim/./display.c:539: error: ‘vbox’ undeclared (first use in this function)
../../platform/netsim/./display.c:540: error: ‘GdkGCValues’ undeclared (first use in this function)
../../platform/netsim/./display.c:540: error: expected ‘;’ before ‘values’
../../platform/netsim/./display.c:541: error: ‘GdkColor’ undeclared (first use in this function)
../../platform/netsim/./display.c:541: error: expected ‘;’ before ‘color’
../../platform/netsim/./display.c:547: warning: implicit declaration of function ‘gtk_init’
../../platform/netsim/./display.c:549: warning: implicit declaration of function ‘gtk_window_new’
../../platform/netsim/./display.c:549: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
../../platform/netsim/./display.c:550: warning: implicit declaration of function ‘gtk_window_set_title’
../../platform/netsim/./display.c:550: warning: implicit declaration of function ‘GTK_WINDOW’
../../platform/netsim/./display.c:552: warning: implicit declaration of function ‘gtk_vbox_new’
../../platform/netsim/./display.c:552: error: ‘FALSE’ undeclared (first use in this function)
../../platform/netsim/./display.c:553: warning: implicit declaration of function ‘gtk_container_add’
../../platform/netsim/./display.c:553: warning: implicit declaration of function ‘GTK_CONTAINER’
../../platform/netsim/./display.c:554: warning: implicit declaration of function ‘gtk_widget_show’
../../platform/netsim/./display.c:556: warning: implicit declaration of function ‘gtk_signal_connect’
../../platform/netsim/./display.c:556: warning: implicit declaration of function ‘GTK_OBJECT’
../../platform/netsim/./display.c:557: warning: implicit declaration of function ‘GTK_SIGNAL_FUNC’
../../platform/netsim/./display.c:559: error: ‘font’ undeclared (first use in this function)
../../platform/netsim/./display.c:559: warning: implicit declaration of function ‘gdk_font_load’
../../platform/netsim/./display.c:563: error: ‘drawing_area’ undeclared (first use in this function)
../../platform/netsim/./display.c:563: warning: implicit declaration of function ‘gtk_drawing_area_new’
../../platform/netsim/./display.c:564: warning: implicit declaration of function ‘gtk_drawing_area_size’
../../platform/netsim/./display.c:564: warning: implicit declaration of function ‘GTK_DRAWING_AREA’
../../platform/netsim/./display.c:567: warning: implicit declaration of function ‘gtk_box_pack_start’
../../platform/netsim/./display.c:567: warning: implicit declaration of function ‘GTK_BOX’
../../platform/netsim/./display.c:567: error: ‘TRUE’ undeclared (first use in this function)
../../platform/netsim/./display.c:574: error: ‘GtkSignalFunc’ undeclared (first use in this function)
../../platform/netsim/./display.c:574: error: expected ‘)’ before ‘expose_event’
../../platform/netsim/./display.c:576: error: expected ‘)’ before ‘configure_event’
../../platform/netsim/./display.c:581: error: expected ‘)’ before ‘key_press_event’
../../platform/netsim/./display.c:583: error: expected ‘)’ before ‘key_release_event’
../../platform/netsim/./display.c:586: error: expected ‘)’ before ‘button_press_event’
../../platform/netsim/./display.c:589: error: expected ‘)’ before ‘pointer_motion_event’
../../platform/netsim/./display.c:591: warning: implicit declaration of function ‘gtk_widget_set_events’
../../platform/netsim/./display.c:591: error: ‘GDK_KEY_PRESS_MASK’ undeclared (first use in this function)
../../platform/netsim/./display.c:592: error: ‘GDK_KEY_RELEASE_MASK’ undeclared (first use in this function)
../../platform/netsim/./display.c:592: error: ‘GDK_BUTTON_PRESS_MASK’ undeclared (first use in this function)
../../platform/netsim/./display.c:593: error: ‘GDK_POINTER_MOTION_MASK’ undeclared (first use in this function)
../../platform/netsim/./display.c:603: warning: implicit declaration of function ‘gtk_timeout_add’
../../platform/netsim/./display.c:603: error: ‘idle_callback’ undeclared (first use in this function)
../../platform/netsim/./display.c:608: error: ‘color’ undeclared (first use in this function)
../../platform/netsim/./display.c:613: warning: implicit declaration of function ‘gdk_colormap_alloc_color’
../../platform/netsim/./display.c:613: warning: implicit declaration of function ‘gdk_colormap_get_system’
../../platform/netsim/./display.c:617: error: ‘values’ undeclared (first use in this function)
../../platform/netsim/./display.c:619: error: ‘intensity_gcs’ undeclared (first use in this function)
../../platform/netsim/./display.c:619: warning: implicit declaration of function ‘gdk_gc_new_with_values’
../../platform/netsim/./display.c:620: error: ‘GDK_GC_FOREGROUND’ undeclared (first use in this function)
../../platform/netsim/./display.c:634: error: ‘intensity_clusterhead’ undeclared (first use in this function)
../../platform/netsim/./display.c:648: error: ‘intensity_clusterhead_lightgray’ undeclared (first use in this function)
../../platform/netsim/./display.c:662: error: ‘intensity_clusterhead_red’ undeclared (first use in this function)
../../platform/netsim/./display.c:666: error: ‘red’ undeclared (first use in this function)
../../platform/netsim/./display.c:666: warning: implicit declaration of function ‘get_color’
../../platform/netsim/./display.c:667: error: ‘green’ undeclared (first use in this function)
../../platform/netsim/./display.c:668: error: ‘yellow’ undeclared (first use in this function)
../../platform/netsim/./display.c:669: error: ‘black’ undeclared (first use in this function)
../../platform/netsim/./display.c:670: error: ‘white’ undeclared (first use in this function)
../../platform/netsim/./display.c:673: warning: implicit declaration of function ‘gdk_input_add’
../../platform/netsim/./display.c:673: error: ‘GDK_INPUT_READ’ undeclared (first use in this function)
../../platform/netsim/./display.c:673: error: ‘stdin_callback’ undeclared (first use in this function)
../../platform/netsim/./display.c: In function ‘display_run’:
../../platform/netsim/./display.c:679: warning: implicit declaration of function ‘gtk_main’
make: *** [obj_netsim/display.o] Error 1
--

Thank you
A.Q

---

### Post by mcgalactor on 2010-05-14
I have the same Problem.

---

### Post by NSKhairi on 2011-07-25
Hi all. Right now I'm having the same problem.. Did anyone of you solved it? Can you help me pls??:confused:

---

