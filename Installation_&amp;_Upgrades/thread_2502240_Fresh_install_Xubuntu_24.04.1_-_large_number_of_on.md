---
title: "Fresh install Xubuntu 24.04.1 - large number of ongoing crashes"
date: 2024-11-06
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2024-11-06
I made a fresh install alongside Windows 11 a few days ago and I seem to be plagued with crashes. Affected are those listed below and the OS itself, a selection of which will occur on just about every boot.

```

makem@makem-22:/var/crash$ ls -lh
total 11M
-rw-r----- 1 makem    whoopsie  80K Nov  1 13:02 _usr_bin_blueman-applet.1000.crash
-rw-rw-r-- 1 makem    whoopsie    0 Nov  1 13:00 _usr_bin_blueman-applet.1000.upload
-rw------- 1 whoopsie whoopsie   37 Nov  1 13:00 _usr_bin_blueman-applet.1000.uploaded
-rw-r----- 1 makem    whoopsie 6.0M Nov  2 15:21 _usr_bin_mousepad.1000.crash
-rw-rw-r-- 1 makem    whoopsie    0 Nov  2 15:21 _usr_bin_mousepad.1000.upload
-rw------- 1 whoopsie whoopsie   37 Nov  2 15:21 _usr_bin_mousepad.1000.uploaded
-rw-r----- 1 makem    whoopsie  80K Nov  5 20:48 _usr_bin_syncthing-gtk.1000.crash
-rw-rw-r-- 1 makem    whoopsie    0 Oct 30 10:41 _usr_bin_syncthing-gtk.1000.upload
-rw------- 1 whoopsie whoopsie   37 Oct 30 10:41 _usr_bin_syncthing-gtk.1000.uploaded
-rw-r----- 1 makem    whoopsie 2.4M Nov  6 14:32 _usr_bin_xfce4-panel.1000.crash
-rw-rw-r-- 1 makem    whoopsie    0 Nov  6 14:35 _usr_bin_xfce4-panel.1000.upload
-rw------- 1 whoopsie whoopsie   37 Nov  6 14:35 _usr_bin_xfce4-panel.1000.uploaded
-rw-r----- 1 makem    whoopsie 2.2M Nov  6 14:35 _usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.crash
-rw-rw-r-- 1 makem    whoopsie    0 Nov  6 14:35 _usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.upload
-rw------- 1 whoopsie whoopsie   37 Nov  6 14:35 _usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.uploaded
makem@makem-22:/var/crash$ 

```

I have also noticed that on occasions there is a noticeably long delay when for example I right click on the desktop and select, 'open new window'. Sometimes I will get two windows when I think I may not have actually clicked. Apps such as Catfish can take many seconds to appear at times too. I have posted my dmesg output to pastebinit.

[https://dpaste.com/942AXCWAE](https://dpaste.com/942AXCWAE)

I have never ever had so many crashes and it is ongoing. Can anyone help diagnose the reason, hopefully just one to cover all.

---

