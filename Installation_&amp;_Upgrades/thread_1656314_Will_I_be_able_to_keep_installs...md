---
title: "Will I be able to keep installs.."
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Totally Annoyed on 2010-12-30
After struggling with the install, geting my network drive working, and sound card situated, I have decided to wipe Windows 7 off my computer all together. I was wondering will all the software that I have downloaded (such as the one to get my sound card to be recongnized) still be there if i do a re-install? Or is there another way to take windows off my computer? 
:guitar:

---

### Post by gordintoronto on 2010-12-30
No, a reinstall will wipe out what you have installed.

You could always just use the Windows partition for storing data.

---

### Post by presence1960 on 2010-12-30
Is ubuntu already installed in a dual boot setup? If no then you can install Ubuntu and choose to use the entire disk.

If yes you can use Gparted (System > Administration > Gparted Partition Editor) to format the windows partition to ext 3 or ext 4 and use it for data storage.

Either way you may want to make an image of your windows partition to an external disk using [clonezilla]("http://clonezilla.org/"). This way if you ever decide to reinstall windows you will have exactly what is there now on windows when you restore from the image you made.

P.S. you do want to back up any files on windows partition as they will be lost. You can then transfer them back to ubuntu after.

---

