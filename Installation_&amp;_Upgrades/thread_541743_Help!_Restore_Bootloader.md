---
title: "Help! Restore Bootloader"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by rob_botch on 2007-09-03
Hi

I have a really bad problem with my computer. I attempted to install ubuntu as a dual boot with XP, however, the installer failed. Whenever I turn on the computer, I get a GRUB error 17 and neither OS will start. I can use the ubuntu Live CD (this is how I'm typing this), and I can see all of my Windows files on the hard drive.

My plea for help is this: from ubuntu Live CD, how can I either repair GRUB to allow me to use Windows, or (preferable) restore the normal Windows XP bootloader?

I don't have Windows XP CD, because my computer came with a recovery partition. I really don't want to reinstall Windows if possible, because this is a shared computer.

Any help would be warmly appreciated!!

Thanks

Robert

---

### Post by forestpixie on 2007-09-03
Have a llok at these two pages - download and burn supergrub to a disk as an iso - you should be able to use that. [This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") page is aimed at restoring grub after reinstallation of windows - but it might help you 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you're new to linux - you might be better of posting to Absolute Beginners 

haven't been here long myself and just passing through 

But you should be able to restore grub from within the livecd to make you feel better :)

---

### Post by rob_botch on 2007-09-03
Thanks

I have used supergrub, and that allowed me to boot windows. Can SuperGrub actually restore GRUB? I tried reinstalling GRUB from within the LiveCD, but the same error appeared. Since I'm in Windows now, can I restore the Windows bootloader?

---

### Post by forestpixie on 2007-09-03
I assume that as you're in windows - the bootloader is now ok, try rebooting if that's ok - use the live cd and the links I gave to restore grub -then you should be fine

---

### Post by rob_botch on 2007-09-03
Thank you very much for your advice. I'll certainly give that a go.

---

