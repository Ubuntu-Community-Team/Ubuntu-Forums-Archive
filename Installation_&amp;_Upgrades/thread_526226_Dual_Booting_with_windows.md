---
title: "Dual Booting with windows"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by will71110 on 2007-08-15
I need some help.  I'm trying to install Ubuntu on a laptop with windows.  I have used gparted live to part the disk so now I have hda1 though 6 (6 is the new part).  hda6 is where I have put my ext3 part.  

Ubuntu locks the install when I try and install to that drive.  I have a ACER 4000 Ferrari.  Is there something I'm missing?

---

### Post by Pumalite on 2007-08-15
[http://ubuntuforums.org/showthread.php?t=103098&highlight=Acer+4000+Ferrari](http://ubuntuforums.org/showthread.php?t=103098&highlight=Acer+4000+Ferrari)

[http://ubuntuforums.org/showthread.php?t=199966&highlight=Acer+4000+Ferrari](http://ubuntuforums.org/showthread.php?t=199966&highlight=Acer+4000+Ferrari)

---

### Post by will71110 on 2007-08-15
That thead didnt help.  It's about getting a black screen when booting.  I dont even get that far.  My problem is getting it to format the partition that I created.  I'm getting No root file system is defined on the install.  What does that mean?

---

### Post by notbitmonk on 2007-08-15
Click on edit partition and type / on the install or mount point.

---

### Post by will71110 on 2007-08-15
How do you create swap mem from there.  I get a warning that swap mem is a good idea and I need to create space for it.

---

### Post by will71110 on 2007-08-15
Figured the swp mem out...Did have enough space to create it.  Got it now.

---

### Post by will71110 on 2007-08-15
Now that I got this far with it, will I need to do anything special to get windows to dual boot with ubuntu?  Or will that go automacitally?

---

### Post by NewbieNik on 2007-08-15
Will,

It should load a GRUB menu when you boot where you can choose which OS and version you want to boot into. If nothing shows when you boot up then there is an issue with GRUB.
You can only load one OS at once, so to use Windows you need to reboot the laptop and choose Ubuntu and vice-versa.

---

### Post by will71110 on 2007-08-15
That was easy enough.  I got it running.  I was told it is not a good idea to read the NTFS files on my windows part.  is that true?  Should I leave those alone(unmount them?) What is the command to unmount them?

---

### Post by seek3r on 2007-08-15
[SIZE="3"]Reading the NTFS partitions is fine, its writing to them that causes problems unless you install some extra software. [/SIZE]

---

### Post by kirios on 2007-08-15
> **will71110 said:**
> I was told it is not a good idea to read the NTFS files on my windows part.  is that true?  Should I leave those alone(unmount them?)
[COLOR="DarkRed"]Ubuntu mounts NTFS volumes as read-only by default. Yyou can't overwrite or delete files on the NTFS partition unless you install ntfs-3g and change the permissions on the volume.[/COLOR]

---

### Post by will71110 on 2007-08-16
Gotcha.  I dont plan on them interacting with each other anyways.  I'm only using Ubuntu on my laptop to get use to linux.  Also its a test bed for my media center which is also running Ubuntu.  Going to get mythTV installed on it when I get my internet back (Lost my aDSL modem to a power serge:( )

---

### Post by dreadie on 2007-08-16
As an aside, if you do want to unmount those partitions for any reason, 
sudo umount -lf <mountpoint>

My Windows partition mounts as /media/sda1, so I'd type
sudo umount -lf /media/sda1

---

