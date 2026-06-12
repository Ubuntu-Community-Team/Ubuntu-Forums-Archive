---
title: "How to install on laptop with no CD or floppy?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by jstevans on 2007-11-04
Hello,

I have a wonderful old Sony Vaio Z505-JEK onto which I would like to install Ubuntu as a replacement for Windows 2000.  However, the external CD PCMCIA drive is dead, the external floppy drive is lost, and I have no idea how to do the install in this situation.

I did manage to install Ubuntu as a dual-boot before the CD and I am quite knowledgeable including using Partition Magic and being comfortable at the DOS command line.

The machine has a USB port but the BIOS does not have an option to boot from it.

Is there any way I can bet Ubuntu onto this machine?

I read somewhere that an install can be done over the network but it did not explain how.

I assume I need to reformat the drive first?

Thank you for any help you can provide.

Jay

---

### Post by Pumalite on 2007-11-04
Netboot:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by tengobotas on 2007-11-04
Does anyone have any advice on how to install to a Powerbook g4(667) with no cdrom access?

I was wondering if there is a way I can start the install by mounting the iso.image within OSX(which is currently installed) and then continuing via ftp... its a stretch, i know.

Any tips are appreciated.

Thanks

---

### Post by jstevans on 2007-11-04
Hi Pumalite,

Thanks for the link, I understand most of it but I think I am stuck because my Sony Vaio Z505-JEK does not seem to be PXE capable.  The BIOS setup menu only allows me to choose to boot from floppy (which I long ago lost), CD (which is broken), and HD.

I hunted around some and think there are apps that will add PXE booting to a machine but they seem to need to be built up on a floppy - which I do not have.  

Is there another way to install Ubuntu onto this machine (no CD, no floppy, not net bootable)?  Or, can I add net bot-ability to it?

I'd welcome any additional help.

Jay

---

### Post by jstevans on 2007-11-04
On more thought - since I did manage to install Ubuntu in a dual-boot configuration before my CD drive died can I re-partition the laptop's drive to either remove the Windows 2000 partition or reduce it greatly?  This partitioning would need to be done without use of a CD, floppy, or netboot.

Thanks again

---

### Post by Pumalite on 2007-11-04
You can install Gparted in your Ubuntu. I'm not sure it can do the job because it will be working with a mounted drive.

---

### Post by jstevans on 2007-11-04
I'm installing it now, I'll let you know.

Any thoughts on how to do a clean install in this machine (no CD, no floppy, no netboot)?  Is there any way I can add netboot to the machine?

Jay

---

### Post by jstevans on 2007-11-05
Duh, duh, duh!!!  I went through downloading and installing Gparted and ran it only to realize I'd put Ubuntu onto the same partition as Windows.

OK, so now I have a different question - how do I get rid of Windows and end up with only Ubuntu?

This is the laptop with no CD, no floppy, no netboot ability?

Jay

---

### Post by eriqjaffe on 2007-11-13
> **jstevans said:**
> Duh, duh, duh!!!  I went through downloading and installing Gparted and ran it only to realize I'd put Ubuntu onto the same partition as Windows.

OK, so now I have a different question - how do I get rid of Windows and end up with only Ubuntu?

This is the laptop with no CD, no floppy, no netboot ability?

Jay

If you still have Windows installed, you can accomplish the Ubuntu install using [WUBI](http://wubi-installer.org/) and then you can use [LVPM](http://ubuntuforums.org/showthread.php?t=438591) to transfer the loopback partition to a physical partition.

In theory, at least, since I haven't tried it.

---

### Post by sirasgeirr on 2007-11-21
> If you still have Windows installed, you can accomplish the Ubuntu install using WUBI and then you can use LVPM to transfer the loopback partition to a physical partition.

In theory, at least, since I haven't tried it.

I myself had problem doing this with an old notebook with similair hardware setup, What worked for me and would probably work for you also if you still has Windows installed is to use UNetbootin [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) It was really easy to set up, But be careful if you remove Windows cause then you cant do it again, 

What happened to me is that  I had Xubuntu 7.04 installed and was gonna do the uppgrade to 7.10, I was sure to conect the power plug to the wall of my laptop but what i didnt realise was that it was the wrong cable leading to another laptop! So just before the installation was complete and it was setting up GRUB the computer died and refused to even boot after that, Luckily my laptop can boot from PXE so i managed to do a clean install of 7.10 :)

---

