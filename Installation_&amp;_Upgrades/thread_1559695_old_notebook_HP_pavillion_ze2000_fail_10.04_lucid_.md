---
title: "old notebook HP pavillion ze2000 fail 10.04 lucid install"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by igorsky on 2010-08-23
Greetings

Searching for one week at the forum, sorry if i missed any posts about my issue,

My specs:

                                 **Microprocessor**1.4 GHz Intel® Celeron® M Processor 360
 **Microprocessor Cache**1MB L2 Cache, 400MHz FSB
 **Memory**256MB 400MHz DDR2 System Memory (1 Dimm)
 **Video Graphics**Intel® Extreme Graphics 2 (shared)
 **Video Memory**256mb: up to 64mb shared
 **Hard Drive**40GB (4200RPM) Hard Drive
 **Multimedia Drive**24X CD-R read/24X CD-RW read and write /24X CD read/8X DVD read
 **Display**15.0" XGA TFT Display (1024 x 768)
 
Issue:

The old Blank screen after booting from liveCD. Any boot parameters like =vga771, vga=778 , nolapic, etc doesn't work.

Today i used the mini CD command-line install, got the system running at the terminal, but installing xorg or gnome and rebooting results again in fail. Tried to edit xorg.conf through nano, after sudo apt-get install but before reboot, but was fail again (couldn't open the file).

I dont know exactly if its the gnome or the X the issue, because i tried at the same notebook the  ubuntu 8.04, the wallpaper pops up but it freezes after, i cannot use the X.

Both cd's are checksum valid originals from canonical

is there any ways to install gnome and x in the terminal, edit the xorg.conf with anything that solve the problem and reboot?

best regards

update 23:11PM: I found it, its a issue with old intel graphic cards. i915.modeset=0 xforcevesa in the boot parameters and i could use the installer in the lucid live cd. but now i need to edit the grub to always boot with this parameter... any help?

---

### Post by spcwingo on 2010-08-23
To make that permanent just open the file /etc/default/grub in your favorite test editor.  At the second:

```
GRUB_CMDLINE_LINUX=""
```

Between the quotation marks input your parameter.  After that save, exit, and then run this command:

```
sudo update-grub
```

Finally, reboot and you should be golden.  :)

---

