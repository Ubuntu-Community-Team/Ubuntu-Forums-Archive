---
title: "BIOS doesn't allow boot from cd-rom drive.  Bootable diskette?"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by petunia50 on 2006-07-29
I have a system (500MHz Intel & 256MB RAM).  I would like to install Ubuntu 5.10 from CD, but BIOS won't allow me to set the cd-rom drive as the first drive to boot.  Is there a way to create a bootable floppy & then install the OS?

---

### Post by Ziox on 2006-07-29
there usually is a button that you can press that allow you to boot straight to CD.  Mine's ESC, which takes me to a menu, and from there i can boot to cd, harddrive, or enter setup...all without changing by bios...As for a floppy...i doubt there are any...

hope this helps..

---

### Post by meng on 2006-07-29
I wonder if your BIOS could be upgraded.

---

### Post by Swab on 2006-07-29
Try Smart Boot Manager, you can install it to a floppy, then boot from the floppy and it should give you the option to boot from your ubuntu CD.  I haven't actually tried it, but worth a go. 

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

Either that or look into loadlin

---

### Post by danycgeno on 2006-08-11
Hi,

I access to this page and can´t donwload a program, you have.

Regards

---

### Post by hakre on 2006-08-29
I guess noone can, that PHP driven site needs an update after the register globals settings change. I mailed the site owner about it. If anyone has got a link to this small thingy, would be great.

/edit:
the email addy on that page isn't valid any longer, so no chance to contact the author. google lead me to a sourceforge page where something with the same name can be donwloaded:
[http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html)

it defenetly looks like it is the same software, proof is here:
[http://btmgr.sourceforge.net/](http://btmgr.sourceforge.net/)

i'll check that manager out later

---

### Post by hakre on 2006-08-29
> **Swab said:**
> Try Smart Boot Manager, you can install it to a floppy, then boot from the floppy and it should give you the option to boot from your ubuntu CD.  I haven't actually tried it, but worth a go. 

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

As you wrote you have not tried this. I did try this.

Infact Smart Boot Manager is recommended, but it comes with a complete Diskimage for a bootdisk you only need to write on the floopy. This image and a description of what to do with it is already located on the Ubuntu CD.

For Windows XP Users, I wrote an HOWTO ([HOWTO Create a Bootdisk for Ubuntu (on WinXP)](http://ubuntuforums.org/showthread.php?t=246486)) describing an easy way working for me. You only need to download 2 files. The HowTo contains quite the same way of doing as the already existing recommendation (I found later) in the installation documentation ([SmartBootManagerHowto (I can not boot from my cd-drive)](https://help.ubuntu.com/community/SmartBootManagerHowto)). The only difference is, that it is more WinXP/NT/2000 specific.

---

