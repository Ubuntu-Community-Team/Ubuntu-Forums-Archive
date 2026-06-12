---
title: "completely clean install?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by bolex100 on 2008-02-23
That's it.  I'm converting.  I'm starting my first ever Linux install.

I want to wipe win2000 off my HP omnibook 900 notebook before I install Ubuntu 7.10.

1/ how?  In to past I over installed windoze or, (long, long) ago I used fdisk from a floppy.

2/ which file system works best?  I currently have NTFS

---

### Post by Pumalite on 2008-02-23
Post your specs.

---

### Post by taurus on 2008-02-23
1A.  You can tell the installer to use the whole harddrive and it will wipe your windows off before it installs Ubuntu on it.

1B.  Or you can use gparted in System -> Administration and delete all the partitions on your harddrive.  Then, format it to ext3.  Then, tell the installer to use that space.

2.  You cannot install Ubuntu on a ntfs filesystem.  Use ext3 which is a default filesystem.

---

### Post by -random on 2008-02-23
you might want to have a look at

[https://help.ubuntu.com/7.10/windows/C/preparing.html](https://help.ubuntu.com/7.10/windows/C/preparing.html) before installing..

it's about switching from windows to linux. If it's to late don't worry! I only came upon it after installing over my windows >_< lol

---

### Post by bolex100 on 2008-02-23
Specs are;
HP omnibook 900 notebook
Pentium3
650MHz
256M RAM

At the moment I have burned an instalation disk.  Even booting from the disk only gets me to a desktop with 2 options
Examples
Install
If I choose "install" it accessess the CDROM for 10 minutes and then just sits.  There are no other screens.

---

### Post by taurus on 2008-02-23
With 256MB of RAM, running from the CD, LiveCD, is going to be tough.  Therefore, you can try using the alternate CD or install Xubuntu, using the alternate CD as well.

---

### Post by bolex100 on 2008-02-23
Actually, I just looked harder.  I think I only have 192Mb on this machine.
should I be looking at different Linux?

I tried the install again and read the page at Random's link.  The point it fails at is the Languague screen.  It never gets there.

---

### Post by taurus on 2008-02-23
Try the Xubuntu alternate CD or even Fluxbuntu.

---

### Post by pbcartwright on 2008-02-23
another thing you might want to consider is creating separate partitions for "/" and "/home"
if you do that, if you ever have to reinstall, or decide to try  new distro, your user info will remain, including email, bookmarks, application settings...

always a good thing to create / and /home .
if you have a 60Gb HD, I'd make /=15-20Gb and the rest for /home.

good luck!

---

### Post by -random on 2008-02-24
Sometimes when a machine 'freezes' at a task, I give it LOADS of time.. have you tried doing everything up to the point where it freezes and leave it for say 20min or even more?

There's a chance that your cd might not have burnt/downloaded correctly. Try booting from the cd and choosing the option 'check cd 4 defects'?

---

### Post by bolex100 on 2008-02-24
I finally loaded Xubantu.  Thank for all the help.  Now I just need to find a drum machine, .... but that's another tale.

---

