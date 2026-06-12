---
title: "Dual Boot Ubuntu with Windows"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by NautTboy on 2007-02-27
I have 2 partition from 1 80G HD.  I want to install Ubuntu on the other partition not being use.  I'm stuck at "Prepare Mount Point" could someone help me with the next step?  Seem like Gparted see Windows installed on HDA2, so I want to install on HDA1. I've attached a picture where I'm stuck at.

---

### Post by logos34 on 2007-02-27
You need to go back and complete creating new partitions out of what was hda1.  Make a 38GB ext3 partition and the remainder ~1GB to swap.  Then when you get back to the mount point screens you'll specify '/' for the 38Gb and /swap for the 1GB, and tick the 'reformat' boxes for those two but NOT the windows parititon on hda2 (or whatever it's designated after you do the above).

---

### Post by NautTboy on 2007-02-27
Go back to which/what point to complete the partition? Here are the

Ubuntu Setup steps:

.Language
..Location
...Keyboard
....My Info 
......Prepare Disk Space:
......1. Resize IDE1(MASTER),partition#1
.........(HDA1)and use freed space.
......2. Erase Entire IDE1(HDA) 82.3GB
......3. Manually Edit Partition

Are you saying I should use Option 1 instead of 3?

---

### Post by mikewhatever on 2007-02-27
You need to go back a step, delete the none Windows partition and create two new partitions for Ubuntu in the unallocated space, one root, the other swap, then format them only, and only then mount all of the partitions.

---

### Post by NautTboy on 2007-02-27
Ok, thanks.  I'll try it when I get home.  See if I can delete that partition in the prior step.

---

### Post by NautTboy on 2007-02-28
Thanks Mike, that work.  Now is my next step.  When booting up Grub, windows is last on the list.  How can I make that first, move to the top?  

Look at the picture, it doesn't look like it see my CD Rom drive, Or am I looking at the wrong place?

Wow! so many questions, so many things to learn. But that's it for now.  Is to make the CD/DVD ROM work.

---

### Post by mikewhatever on 2007-02-28
To make Windows boot first by default copy and past Windows entry can work. Make a backup of grub menu.lst fist
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

then edit the menu.lst

gksudo gedit /boot/grub/menu.lst

> 3.Another way
You can cut the entire Windows entry from where it is under the end of the automagic kernels list and paste it above the beginning of the automagic kernels list.
 Above this line: ### BEGIN AUTOMAGIC KERNELS LIST

4. What NOT to do-  don't paste your Windows entry anywhere inside the automagic kernels list because it will be deleted when you have a kernel update in Ubuntu.


I took it from [Herman's site](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst) which is great and has other interesting options.

According to the picture, the CD--Rom is already mounted. Does it work if you insert a CD?

---

### Post by NautTboy on 2007-02-28
Sorry for my stupid question.  Where can i do that copy and paste? Also update the menulist?  Is there a RUN command line somewhere?  Or do you mean copy and paste when i first logon.

CD/DVDROM - Audio seems to work fine
DVD Load up with error
VCD won't even recognized

Picture show error

---

### Post by NautTboy on 2007-03-01
I try to edit /boot/grub/menu.lst it won't let me save or replace.  So I logout and try to logon as root but screen said can't not logon as root here.  I dont know where im suppose to logon at.

---

### Post by Coelocanth on 2007-03-01
You need to become root when you use the terminal. The command 'gksudo' should do that for you. If that doesn't seem to work, you can try nano:

```
sudo nano /boot/grub/menu.lst
```

After you're done editing, hit CTRL^X to exit nano, then Y to save your changes, then Enter.

Of course, be sure to make a backup copy of your grub menu first.

---

### Post by NautTboy on 2007-03-01
Previously asked, where do I code that? In the logon Screen? Is there a Run Command line like Windows msdos screen?  No use if you know how to paint but dont know where the brush and paint is at.

> **Coelocanth said:**
> You need to become root when you use the terminal. The command 'gksudo' should do that for you. If that doesn't seem to work, you can try nano:

```
sudo nano /boot/grub/menu.lst
```

After you're done editing, hit CTRL^X to exit nano, then Y to save your changes, then Enter.

Of course, be sure to make a backup copy of your grub menu first.

---

### Post by Coelocanth on 2007-03-01
Open a terminal after you've logged in:

Applications -> Accessories -> Terminal

and type the commands in the terminal.

---

### Post by NautTboy on 2007-03-02
Learned, Accomplished!

---

