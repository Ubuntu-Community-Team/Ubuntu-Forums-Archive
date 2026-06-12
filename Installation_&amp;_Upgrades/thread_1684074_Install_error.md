---
title: "Install error"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by jnarciso on 2011-02-08
I'm attempting to install Ubuntu 10.10 on a Toshiba laptop.  The laptop is about three years old and has plenty of memory and storage space.  The laptop previously ran Windows Vista-32 bit.  

The hard drive has been formatted, so there is no OS.  I burned a CD image of 10.10 to install from CD boot.  The machine boots the disc and it gives the Ubuntu install screen.  The install screen gives the choices of install on hard disk, try it out, or perform memory test etc.  I select install on hard disk.  

A second later, the machine displays the Ubuntu purple welcome page.  Then the machine goes to a black command line interface.  Several machine messages are loaded automatically.  The last line prints an error message:  

(initromfs) mount: mounting /dev/loop0 on //filesystem/squashfs failed: Invalid argument
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem

The machine will not allow any further action.  I figured there was a problem with the CD, so decided to burn the install package to a USB drive.  I get the same install error message.  

Please help, I tried searching the forums and can not find a solution

---

### Post by Old_Grey_Wolf on 2011-02-08
What model Toshiba laptop is it? Some laptops have problems with Ubuntu.

Are you using Linux or Microsoft Windows to burn the CD? It looks like you may have a bad download or CD burn.

Make sure the iso image you downloaded does not have errors by following the instructions at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM).

If you didn't use a torrent mirror to download the iso, I would recommend it. I prefer downloading from a torrent; because, the torrent does some checking on the quality of the download as it happens. A torrent is also a lot faster.

Burn the CD at the slowest speed. You could also make a bootable USB as you know. The fact that you had the problem with your USB makes me I think you may have a bad download.

When you boot from the CD/USB, select the option to test for errors.

If all is well, you should be able to install Ubuntu.

---

