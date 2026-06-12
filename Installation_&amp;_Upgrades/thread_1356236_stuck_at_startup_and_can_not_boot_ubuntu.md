---
title: "stuck at startup and can not boot ubuntu"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by gopal4tech on 2009-12-15
hello after upgrading my ubuntu 8.10 i am getting following prob at mystartup and i can to go for os and I haven't been able to boot into my machine.
 
Pressing f1, then places me on a shell screen which shows me the following error.
 
Quote:
Gave up waiting for the root device. Common problems:
-Boot args(cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Chech root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dv)
 
ALERT! /dev/disk/by-uuid/----big-no---- does not exist. Dropping to a shell.
 
BusyBox v 1.13.3 (Ubuntu ...) built in shell ash.
 
(**[COLOR=#ff0000]initramfs[/COLOR]**):
 
Upon listing in the **[COLOR=#ff0000]initramfs[/COLOR]** prompt, the standard root folders weren't present. As far as i can recollect the following were the folders.
/dev
/bin
/proc
/cat
/lib and a few more. There was no /boot.
 
Can someone please help.

---

### Post by presence1960 on 2009-12-15
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

