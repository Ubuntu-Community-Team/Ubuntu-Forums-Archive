---
title: "Ubuntu Software application not working"
date: 2016-11-17
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2016-11-17
I have just done a fresh install of 16.04 AMD64bit on an AMD cpu machine with an A8 processor and Radeon graphics. I have updated fully. I have transferred all my files from another hard disc into my home directory on the new machine. 

Everything appears to be working fine except Ubuntu Software (Centre) application. When I open the application I get the usual window but with no data population. After a second or so the window closes down automatically.

Any clues?

Many thanks for looking.

---

### Post by myromance123 on 2016-11-17
You can run it from a Terminal, that will give us more information.

To do so, open a Terminal and just copy paste the following and then hit Enter:
```
ubuntu-software
```

Now we should be able to know why it's crashing, if it gives that information that is.

---

### Post by robert48 on 2016-11-17
ubuntu-software

(ubuntu-software:2114): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:2114): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:2114): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:2114): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:2114): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/stellarium_stellarium.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/stellarium_stellarium.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/simple-scan_scanner.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/simple-scan_scanner.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/shutter_shutter.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/shutter_shutter.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/scribus_scribus.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-updates-universe/64x64/scribus_scribus.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/pdfmod_pdfmod.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/pdfmod_pdfmod.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/musique_musique.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/musique_musique.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/gtg_gtg.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/gtg_gtg.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/gnucash_gnucash-icon.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/gnucash_gnucash-icon.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/geary_geary.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/geary_geary.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/calibre_calibre-gui.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/calibre_calibre-gui.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/bijiben_bijiben.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/bijiben_bijiben.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/simple-scan_scanner.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/simple-scan_scanner.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/shotwell-common_shotwell.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/shotwell-common_shotwell.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/scribus_scribus.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-updates-universe/64x64/scribus_scribus.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/gnome-font-viewer_preferences-desktop-font.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/gnome-font-viewer_preferences-desktop-font.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/libreoffice-draw_libreoffice-draw.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-security-main/64x64/libreoffice-draw_libreoffice-draw.png': Too many open files

(ubuntu-software:2114): GsPlugin-WARNING **: failed to load cached icon 64x64/darktable_darktable.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/darktable_darktable.png': Too many open files
[https://myaccount.talktalk.co.uk/home/dashboard](https://myaccount.talktalk.co.uk/home/dashboard)
(ubuntu-software:2114): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed

(ubuntu-software:2114): Gs-WARNING **: hiding recommended applications: found only 4 to show, need at least 8

(ubuntu-software:2114): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-maps.png': Error opening file: Too many open files

(ubuntu-software:2114): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-maps-bg.png': Error opening file: Too many open files

(ubuntu-software:2114): GLib-ERROR **: Creating pipes for GWakeup: Too many open files

Trace/breakpoint trap (core dumped)

Could it have something to do with copying files over from another system? I copied over all files in the home folder including dot files.

EDIT
Fixed it!

---

### Post by robert48 on 2016-11-17
Fixed with
```
sudo apt-get install ubuntu-software -f
```

Thanks for the steer!

---

