---
title: "Grub error"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by luisamfonseca on 2012-01-09
Hi!
I have a computer only with ubuntu and I had a boot problem and tried to solve reinstalling the grub.
Now when I restart it gaves me error:file not found. grub rescue> and  it gaves always unknown command when I try to do something.
How can I solve this problem?

thanks

---

### Post by oldfred on 2012-01-09
Welcome to the forum.

grub rescue has limited commands that it can run.

You have several options, you can try to manual boot, you can reinstall grub, you can download boot repair to fix grub automatically or Supergrub to boot and then you can fix grub from inside yourinstall.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

# is comment do not copy or type. Configfile only works if grub.cfg is ok.
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
# if that does not work use this & again use hdX,Y and sdXY that is where your install is.
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

---

### Post by drs305 on 2012-01-09
luisamfonseca,

Welcome to the Ubuntu Forums.

*oldfred* has given you some good links. The easiest to try is probably the Boot Repair tool. It can fix many of the problems related to Grub. Click the link in *oldfred's* post or the "Boot Repair" link in my signature line.

If Boot Repair can't fix it, it has an option to run the boot info script. If you still need help, run the script and post the contents of the RESULTS.txt file it generates here so we can take a look.

---

