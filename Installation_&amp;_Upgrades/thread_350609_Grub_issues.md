---
title: "Grub issues"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by EricJosepi on 2007-01-31
Yo!

This is the first time in a long time that I will be attempting to install Ubuntu for my laptop.  I'm trying to put it onto my 250GB external HDD and I have a question.  When I attempted to install it, the GRUB Boot loader f*cked itself up when it tried to install.  I'm just wondering if there is anyway that I can install grub seperately from the regular install process when this happens or am I SOL here?

Cheers,
Eric
:guitar:

---

### Post by EricJosepi on 2007-01-31
Ok... I think that I have the problem centered here.  I cannot disable the internal HDD on my laptop from the BIOS (I've look and I've tried) so now it comes down to this.  What do I set the Grub instructions to when the installer on the LiveCD says "Install Grub (hd0)"?

Any help would be appreciated!

Cheers,
Eric
:guitar:

---

### Post by logos34 on 2007-01-31
(hd0) is your internal drive...change it if you can to (hd1)

---

### Post by ucsdrake on 2007-01-31
> **EricJosepi said:**
> Ok... I think that I have the problem centered here.  I cannot disable the internal HDD on my laptop from the BIOS (I've look and I've tried) so now it comes down to this.  What do I set the Grub instructions to when the installer on the LiveCD says "Install Grub (hd0)"?

Any help would be appreciated!

Cheers,
Eric
:guitar:


basicly ive gone through the EXACT same thing as you have .. i also have a 250gb hd (kaser) and i wanted to install it to my external HDD and installed GRUB to hd0 ... what happened to me was i was unable to boot my computer unless my external HDD was plugged in and turned on

try [http://ubuntuforums.org/showthread.php?t=308027&highlight=install+external+hard+drive](http://ubuntuforums.org/showthread.php?t=308027&highlight=install+external+hard+drive)

hope that helps!

---

### Post by EricJosepi on 2007-01-31
All right, thanks for the help guys, I really appreciate it.:D 

Now for a more clever question, what is the best way to create a FAT32/NTFS partition that I can use to go back and forth between XP and Ubuntu on this drive?

---

### Post by ucsdrake on 2007-01-31
create that partition using Gparted in the install section .. and id recommend using either a NTFS or EXT3 file type because youre not limited to 4gb files or a 32gb size partition (like you would be using a FAT32 partition)  you can find codecs for Ubuntu to read NTFS and programs to read EXT3 in Windows XP

---

### Post by logos34 on 2007-01-31
> **EricJosepi said:**
> All right, thanks for the help guys, I really appreciate it.:D 

Now for a more clever question, what is the best way to create a FAT32/NTFS partition that I can use to go back and forth between XP and Ubuntu on this drive?

Have a look[ here]("http://www.psychocats.net/ubuntu/partitioning"). [corr.]

You could use NTFS-3G, which allows you to read and write to NTFS from linux.  I've been using it for the last month or so and no problems to report so far.  To read and write to ext2/3 from windows get fs-driver (i have 64-bit windows so i'm limited to running explore2fs which has only read capability)

---

### Post by EricJosepi on 2007-01-31
> **ucsdrake said:**
> create that partition using Gparted in the install section .. and id recommend using either a NTFS or EXT3 file type because youre not limited to 4gb files or a 32gb size partition (like you would be using a FAT32 partition)  you can find codecs for Ubuntu to read NTFS and programs to read EXT3 in Windows XP

So it doesn't matter where within the monstrous EXT3 partition that I just made I create the NTFS partition?

---

### Post by ucsdrake on 2007-02-01
no you should definetly create a new partition outside of both youre Linux and XP systems.  im willing to bet you have some extra room on that 250gb external hard drive of yours .. id check out that link that logos34 provided ... its quite helpful to give you a graphical idea of whats going on as well

---

### Post by EricJosepi on 2007-02-01
Thanks for all the help guys!  It's definitely making my second goround with Ubuntu a lot better than the first.  ... Also my sound card works this time. :)

---

