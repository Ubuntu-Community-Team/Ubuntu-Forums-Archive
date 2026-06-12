---
title: "GRUB Error problem! Help!"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by Dantesinferno on 2008-01-04
First of all I am a complete newb to Linux so I need all the help I can get!

I ve been getting the error 17 problem and I dont know how to deal with it.

I ve tried some of the recommendations here but they dont seem to work.

Ubuntu is installed in a separate external HDD btw. Nothing else is installed in there except Ubuntu.
I am trying to use what I am suggested here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


First problem I encounter is this:
When I enter this
grub> find /boot/grub/stage1

I get  (hd2,0)

Then I try to setup using various alternatives but nothing seems to happen. No (hd0), no (hd1), nothing.

So I root and go to the other possible solution.

With the sudo fdisk -l  command I see all my HDD but instead of getting information as /dev/hda1 they are in this form 

1st HDD
/dev/sda1.
/dev/sda2

2nd HDD
/dev/sdb1 

3rd HDD (this is where Linux is installed)
/dev/sdh1  
/dev/sdh2          
/dev/sdh5  

Suspecting the sdg1 I run
 mount -t ext3 /dev/sdh1 /mnt/root
 ls /mnt/root

I get
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinu

Not sure whether this is the correct one I unmount and try to mount Sdg5 but I get this
mount: /dev/sdg5 already mounted or /mnt/root busy

So I stay with sdg1
  mount -t ext3 /dev/sdg1 /mnt/root/boot
ls /mnt/root/boot

And I get this:
> Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdg



Note that I am using an older version of Ubuntu. Now I dont know if I didt it correctly but I get different messages than those in the page

It says that I should have gotten something like this:
> config-2.6.18-3-686      initrd.img-2.6.18-3-686.bak  System.map-2.6.18-3-686 
grub                     lost+found                   vmlinuz-2.6.18-3-686
initrd.img-2.6.18-3-686  memtest86+.bin

---

### Post by Pumalite on 2008-01-04
Disconnect your internal drives and try again.

---

### Post by njparton on 2008-01-04
May need to go one step further - reinstall with all internal drives disconnected.

Then use your motherboards boot menu to boot from the approriate hard disk once you're back up and running fully.

---

### Post by Dantesinferno on 2008-01-04
How do I disconnect them? You mean open my case and unplug it?

---

### Post by Pumalite on 2008-01-04
The only drive available to the installer must be the USB.

---

### Post by Dantesinferno on 2008-01-04
> **Pumalite said:**
> The only drive available to the installer must be the USB.

What solution do you suggest after I do that?

Note: I dont have Boot Magic or System Commander and I am a complete newb in Linux

---

### Post by ukripper on 2008-01-04
This may help [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Pumalite on 2008-01-04
I imagine you have a bootable CD with Ubuntu. Make CD first in boor order in BIOS, make sure your USB is recognized in BIOS and you are set to go.
Later, you can reinstall Grub in your internal drives with this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Dantesinferno on 2008-01-04
I disconnected my internal HDD run the live CD, did the steps here (quick start) [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and it now works :D

I d like to make Vista though my default OS and install Ubuntu in my PS3 since I dont want to risk anything in my PC.

I have no problems installing Ubuntu on the PS3 as I have already done it on my friend's but I dont know how to make Windows(vista) my default OS. 

Does EeasyBCD do this? And how do I use it? Sorry for making to many questions but I appreciate your help a lot :)

edit: Ok fixed that too. Thanks a lot :D

---

### Post by c0met on 2008-01-04
I don't have the exact link to the specific documents, but the website below has a lot of useful information about setting up Linux systems and using GRUB (including an explanation of some different error types that GRUB issues).

[CENTER][**[COLOR="Navy"]http://users.bigpond.net.au/hermanzone/[/COLOR]**]("http://users.bigpond.net.au/hermanzone/")[/CENTER]

---

### Post by Pumalite on 2008-01-04
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

