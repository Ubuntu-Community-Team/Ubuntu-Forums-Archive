---
title: "start up disk creator"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by DannyJohansson on 2010-06-25
hello

i was trying to create a start up usb drive.

when i choose from system-admin-startup disk creator, the machine freezes.

i tried to uninstall usb creator and all dependencies, but it wouldn't, it said "E: usb-creator-gtk: subprocess installed pre-removal script returned error exit status 2", etc.

it also seems as if these are not configured, whatever that means.

any ideas?  what's my next step?

---

### Post by C.S.Cameron on 2010-06-26
Does it also freeze if you type in terminal "usb-creator".

Have you updated with Update Manager lately?

---

### Post by DannyJohansson on 2010-06-26
i use update-manager compulsively.

usb-creator in terminal returns "command not found"

it appears that usb-creator is not configured.  if i enter "sudo apt-get install -f", i get back the following:



dan@dan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up usb-creator-common (0.2.22) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing usb-creator-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of usb-creator-gtk:
 usb-creator-gtk depends on usb-creator-common (= 0.2.22); however:
  Package usb-creator-common is not configured yet.
dpkg: error processing usb-creator-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 usb-creator-common
 usb-creator-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
dan@dan-desktop:~$ usb-creator
usb-creator: command not found
dan@dan-desktop:~$ sudo dpkg --configure -a
dan@dan-desktop:~$ sudo dpkg --configure usb-creator
dpkg: error processing usb-creator (--configure):
 no package named `usb-creator' is installed, cannot configure
Errors were encountered while processing:
 usb-creator
dan@dan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up usb-creator-common (0.2.22) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing usb-creator-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of usb-creator-gtk:
 usb-creator-gtk depends on usb-creator-common (= 0.2.22); however:
  Package usb-creator-common is not configured yet.
dpkg: error processing usb-creator-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                    Errors were encountered while processing:
 usb-creator-common
 usb-creator-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by C.S.Cameron on 2010-06-27
Oops, I guess nowadays the command is usb-creator-gtk.
But it looks like your problems go beyond that.
How about using UNetbootin or LinuxLive USB Creator?

---

### Post by DannyJohansson on 2010-06-27
i don't mind doing that, but i'd really like to get this fixed.  anyone?  am i even posting to the right forum?  thanks for listening!

---

