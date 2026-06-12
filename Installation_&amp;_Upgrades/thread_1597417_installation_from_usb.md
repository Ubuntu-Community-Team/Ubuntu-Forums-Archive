---
title: "installation from usb"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by prudra on 2010-10-15
I wanted to install on my new 32-bit dell-vostro-1040 laptop on the extended partition. I have downloaded ubuntu-10.10-desktop-i386.iso on my other laptop and wrote it in the usb by the terminal commad:

$dd if=ubuntu-10.10-desktop-i386.iso of=/dev/sda bs=4M

But when I tried the installation the machine just ignored it booted the hdd. 
However a usb containing opensuse-11.3.iso by the same command was recognized by the machine and showed the welcome screen.

Why this difference between ubuntu and opensuse? And how shall I make the machine recognize ubuntu?
Thanks.
P.Rudra.

---

### Post by viralmeme on 2010-10-15
> **prudra said:**
> I wanted to install .. when I tried the installation the machine just ignored it
Some makes of USBs refuse to boot following this method, a solution is to boot to Windows and use the [HP Drive Key Boot Utility]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839"). This works on other makes of USB devices - sometimes :)

---

### Post by kio_http on 2010-10-15
This method is NOT compatible with Ubuntu's live cd system. You can use Unetbootin to create a live usb key.

---

### Post by C.S.Cameron on 2010-10-15
If UNetbootin does not work for you try Startup disk creator which comes on the Live CD.

---

### Post by sikander3786 on 2010-10-15
In addition to Unetbootin, Startup Disk Creator, this page might also help you.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by prudra on 2010-10-15
> **sikander3786 said:**
> In addition to Unetbootin, Startup Disk Creator, this page might also help you.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


I am actually working from debian-lenny OS. Shall I partition the usb-stick with the help of gparted and what will be the number and sizes of the partitions? will the file-system will be reiserfs/ntfs? In one of the partitions will, of course, go the ubuntu-xxxx.iso. What files will the other partitions have. Will the writing command be   $dd if= xxxx of=/dev/sdb1 bs=4M  ?
Thanks. I am just an end-user.
P.Rudra.

---

### Post by oldfred on 2010-10-16
Still another way:

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 
Another - multibooting multiboot055.sh:
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

---

