---
title: "Dual-Boot Questions"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by HamCoder on 2006-11-13
When I first installed Ubuntu, I hit the wrong key, formatted my C: drive and toasted windows.  Oh, well.  Live and Learn.

So now I've got a P3 with 512mb ram a single HD running 6.10.  I've got a 2nd HD but it's not plugged in (yet).

I want to install Windows on the 2nd HD and make a dual boot system.  In case you're interested the reason, the Ham Radio apps I run on windows are better integrated than those on Linux.  I've scanned the forums and most of the dual-boot topics address installing windows first, then ubuntu.  I don't want to re-install Ubuntu unless absolutely necessary.  The forums also discuss how to move NTFS files around so you can partition a single windows HD to support Ubuntu.

I want to...
Make a single partition on HDb
Put Windows XP on HDb by itself
Make the MBR on HDa point to GRUB
and Have GRUB give me a choice between Ubuntu (default) and Windows).

How do I make this happen?

Thanks for your help

---

### Post by earobinson on 2006-11-13
> **HamCoder said:**
> When I first installed Ubuntu, I hit the wrong key, formatted my C: drive and toasted windows.  Oh, well.  Live and Learn.

So now I've got a P3 with 512mb ram a single HD running 6.10.  I've got a 2nd HD but it's not plugged in (yet).

I want to install Windows on the 2nd HD and make a dual boot system.  In case you're interested the reason, the Ham Radio apps I run on windows are better integrated than those on Linux.  I've scanned the forums and most of the dual-boot topics address installing windows first, then ubuntu.  I don't want to re-install Ubuntu unless absolutely necessary.  The forums also discuss how to move NTFS files around so you can partition a single windows HD to support Ubuntu.

I want to...
Make a single partition on HDb
Put Windows XP on HDb by itself
Make the MBR on HDa point to GRUB
and Have GRUB give me a choice between Ubuntu (default) and Windows).

How do I make this happen?

Thanks for your help
You should be able to plug in the second hd then install win xp, after that using a live cd you should be able to repair the mbr using a live cd ([http://www.daniweb.com/blogs/entry708.html](http://www.daniweb.com/blogs/entry708.html))

---

### Post by HamCoder on 2006-11-13
Thanks.  I'll give it a try tonight when I get home.

---

### Post by bulldog on 2006-11-13
Unplug the Ubuntu hdd,plugin the new hdd and install windows,unplug the windows hdd,plugin the Ubuntu hdd as master and plugin windows hdd as slave.

Now you should see GRUB at startup without windows listed.
Boot Ubuntu and```
gksu gedit /boot/grub/menu.lst
```

Add the following lines at the end of your menu.lst
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

Save the file and close it.
Type in your terminal,
```
sudo update-grub
```

Reboot and GRUB should have your windows listed.
Try to boot into windows,if you have troubles with that,post back please.

---

### Post by HamCoder on 2006-11-14
When I started, I had Ubuntu on the 12gig master and no slave.  The 8gig slave was disconnected.  

I learned that windows would not install unless it was the first OS installed.  So I disconnected Ubuntu and connected the 8gig drive.  Then installed windows.  But the drive would not boot.  I installed Ubuntu to the 8gig and it still wouldn't boot.  Master/slave wasn't an issue.  My guess is that Windows didn't put a MBR on the drive.

So I put the 12 gig on master and the 8gig on slave.  Installed Windows on the master (destroying Ubuntu) and then installed Ubuntu on the 8gig.  Everything seems to be working, dual-booting, etc.  I just wanted Ubuntu to be on the larger (faster?) drive.

Thanks to all for your help.

---

