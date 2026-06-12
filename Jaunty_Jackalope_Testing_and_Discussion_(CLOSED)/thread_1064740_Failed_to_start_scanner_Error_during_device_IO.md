---
title: "Failed to start scanner: Error during device I/O"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-02-09
When I first started Jaunty, it recognized my CX8400 and worked fine. Now I don't know what changed but I get the above error when I try to scan in XSANE. With Alpha 4 I did re-format to try ext4 so I don't know if I'm missing somethhing or now. Any help would be appreciated.

---

### Post by knarf on 2009-02-09
Let me guess: it works if you try to scan as root? If so you should check for the presence of this file:
```
/etc/udev/rules.d/45-libsane.rules
```Is it present? If not you've got the most likely culprit right there. It used to be that udev took care of setting device file ownership and mode but the responsibility for this task seems to be in Limbo in Jaunty. The solution is to copy that file from a previous version of Ubuntu to the correct directory (see above).

Even with the file in place it might still not work. In my case I had to edit the file a bit:

```

--- 45-libsane.rules.org    2009-02-09 14:29:47.000000000 +0100
+++ 45-libsane.rules    2009-02-09 14:29:28.000000000 +0100
@@ -15,7 +15,7 @@
 #
 
 ACTION!="add", GOTO="libsane_rules_end"
-SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
+#SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
 
 # Hewlett-Packard ScanJet 4100C
 SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="0101", MODE="664", GROUP="scanner"

```As you see I had to comment out the line which makes udev skip this file if it happens to be called in the process of adding a usb device.

---

### Post by theozzlives on 2009-02-09
> **knarf said:**
> Let me guess: it works if you try to scan as root? If so you should check for the presence of this file:
```
/etc/udev/rules.d/45-libsane.rules
```Is it present? If not you've got the most likely culprit right there. It used to be that udev took care of setting device file ownership and mode but the responsibility for this task seems to be in Limbo in Jaunty. The solution is to copy that file from a previous version of Ubuntu to the correct directory (see above).

Even with the file in place it might still not work. In my case I had to edit the file a bit:

```

--- 45-libsane.rules.org    2009-02-09 14:29:47.000000000 +0100
+++ 45-libsane.rules    2009-02-09 14:29:28.000000000 +0100
@@ -15,7 +15,7 @@
 #
 
 ACTION!="add", GOTO="libsane_rules_end"
-SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
+#SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
 
 # Hewlett-Packard ScanJet 4100C
 SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="0101", MODE="664", GROUP="scanner"

```As you see I had to comment out the line which makes udev skip this file if it happens to be called in the process of adding a usb device.

I can scan once as root, and I have 3 different versions of Ubuntu and none of them have that file (8.04, 8.10, and 9.04 Alpha 4).

Re-burned Alpha 2 live and couldn't find that file.

---

### Post by knarf on 2009-02-10
The 'scan once' problem might be related to the USB bus suspending while the device is not used. While this in itself is a feature, it gets annoying when it refuses to come back to life. To see whether this is part of the problem reload the usbcore module with the autosuspend parameter set to -1 and try again. Depending on what you have attached to the USB bus you can either try this on the fly by unloading all modules using usbcore followed by usbcore itself, then reload usbcore with usb autosuspend disabled:

```
sudo modprobe usbcore autosuspend=-1
```OR (if you can not unload usbcore for some reason, eg. your keyboard is attached to USB) add the following line to /etc/modprobe.d/options-local (create the file if it does not exist)

```
options usbcore autosuspend=-1
```Try to scan again (as normal user or root, depending on whether device file permissions and ownership are correct). If it now works and keeps on working you should add or keep that line in /etc/modprobe.d/options-local. Several printers/scanners/???? seem to have problems with USB suspend, just search for 'linux autosuspend' on $search_engine.

As far as Ubuntu packages not containing the udev rules file for libsane:

> $ grep DESC /etc/lsb-release
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
$ apt-cache policy libsane
libsane:
  Installed: 1.0.19-1ubuntu3
  Candidate: 1.0.19-1ubuntu3
  Version table:
 *** 1.0.19-1ubuntu3 0
        500 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status
$ dpkg -L libsane|grep udev
/etc/udev
/etc/udev/rules.d
/etc/udev/rules.d/45-libsane.rules

---

### Post by theozzlives on 2009-02-10
I get:
FATAL: module usbcore not found

---

### Post by knarf on 2009-02-10
When do you get that? What is the command that produced that output, and how did you enter it?

Try with 'sudo modprobe usbcore autosuspend=-1' instead

I do have to add that I'm running a custom (2.6.29-rc2) kernel which is fully modularized... if the current Jaunty kernel has a non-modular usbcore then this command obviously won't work... Not having a recent Ubuntu-provided kernel around I can not check this but they have been moving modules in and out of the kernel image to speed up booting (move them in) and to fix problems caused by the former (by moving them out again). If usbcore happens to be built into the current Jaunty kernel you should use the following boot parameter instead (add it to /boot/grub/menu.lst or try it by editing the grub boot stanza when booting the system):

```
 usbcore.autosuspend=-1
```

---

### Post by Statik on 2009-03-23
statik@statik-desktop:~$ dpkg -L libsane|grep udev
/etc/udev
/etc/udev/rules.d
statik@statik-desktop:~$ 


How do I replace the file?

Statik

---

### Post by rburkartjo on 2009-03-23
i have been downloading all the updates and have no problems

---

### Post by paul079 on 2009-04-12
If your problem's related to what mine was, the file you need to find in 8.04 and later is '/etc/udev/rules.d/40-basic-permissions.rules'.  Open it in a text editor as root and change the mode in both lines of the 'USB devices' section from "0664" to "0666." This allows you to scan as a normal (non-root) user.

---

