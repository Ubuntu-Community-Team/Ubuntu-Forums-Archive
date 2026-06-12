---
title: "External USB Bootup &quot;No boot device&quot;"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by stuartbh on 2013-03-07
Ubuntu users,

I recently installed Ubuntu onto a 64GB USB stick I got at Micro Center, no LVM, no encryption, and it worked fine. I can insert it and "boot from USB" no problem. Then I took the Ubuntu installation CD and dd'ed it to a second 32GB USB stick I have ("dd if=ubunt-cd of=/dev/sda", where a = whatever the USB stick's letter was at the time). I then shutdown, removed the 64GB stick and booted up from the 32GB USB stick with the CD image copied onto it with a USB 1TB HD plugged in and an internal 320GB HD (with just windows 7 on it) on the system too. I then installed to the USB 1TB external physical hard drive requesting LVM and encryption be used. All went well absent any noticeable anomalies until I tried to remove the 32GB USB stick and boot from the USB HD. It just said that there was no boot device (I also removed the internal HD, just to make sure I was dealing only with the USB hard disk).
 
The laptop is a Compaq CQ62.

I then booted from the 64GB USB stick with the 1TB HD installed, mounted the "/boot" partition to "/mnt" and then did "grub-install --boot-directory=/mnt /dev/sdb" ("/dev/sdb" being the 1TB HD, as demonstrated by "fdisk -l"), but it seemed to have no effect.

Someone told me there is now some script I can run that will enumerate the full composite of issues that are true with all the bootable devices that I can use to try to diagnose the issue. Anyone aware of such a script, or any ideas I can try?

Thanks in advance.


Stuart

---

### Post by oldfred on 2013-03-07
You can plug in all the flash drives. I have a full install in my 16GB flash and script shows it. You just need to boot some version of Linux to download & run script.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

