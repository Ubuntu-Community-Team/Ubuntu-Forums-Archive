---
title: "I cant get XP to install after I installed Ubuntu"
date: 2005-02-01
forum: Installation &amp; Upgrades
---

### Post by Frazer on 2005-02-01
When I first set up Ubuntu I Formatted my hd and got rid of windows because I wanted to clear it out.  I left 60gb of space to use for xp at a leter date.  My Ubuntu system was working fine after the install.  I went to install xp again and after the install when it reboots I get an error loading operating system message.  Now both Linux and Windows will not run. Iv reinstalled windows again and same problem.  If I reinstall Ubuntu it works fine.  Someone told me this could be to do with the boot Loader on the Ubuntu disk sets up (i think its GRUB) im not sure what the problem is though.  I am quite a noob to all this linux stuff and I have never had to use a boot menu to swich between OS's.  anyone got any ideas on what the problem is, thanks.

---

### Post by clparker on 2005-02-01
I think i heard from a buddy of mine, you gotta do XP THEN ubuntu if your gonna do a  dual boot. Consider this a blessing in disguise.

---

### Post by rudi on 2005-02-01
I think it has something to do with the default boot manager that windows automatically installs. It points to the first primary partition of your hard drive. If the ubuntu installer partitioned your drive you've probably got a partition scheme like:
    ```

   #1 /   ext3
   #2 swap swap
   free space
``` 
    Now when you install windows it creates a new partition after swap. The Boot manager points to #1 / which is linux. 
 You could boot using a live cd, and edit your grub.lst to point windows to #3. Then install grub in the mbr. (wild guess though)

---

### Post by Frazer on 2005-02-01
Even after formatting the linux partions in the xp install I t says the same error, could be be because of the  grub loader? where is the grub loader stored because I have formatted all partions while installing xp.  Ill try to edit the grub setting when I get home (at uni now)

---

### Post by Buffalo Soldier on 2005-02-01
GRUB is installed at the MBR (Master Boot Record)> Master Boot Record An area of the outermost cylinder of a PC hard disk which contains the partition table. This contains four entries identifying the types, starting cylinder and sizes of up to four partitions on the hard disk. One of the entries is flagged as 'active'; this marks the partition from which the machine will boot. (Floppy disks don't have an MBR, since they don't have a partition table. Instead, they just have a boot sector (same as a logical disk), which contains a Media Descriptor Table (MDT) and bootstrap loader. The MDT describes the format of a floppy disk or logical disk).

Try checking out [HowTo: For the newbies](http://ubuntuforums.org/showthread.php?t=13042)

---

### Post by Frazer on 2005-02-04
hey thanks for the help, I think i know how to sort it all out now.  well the 2 weeks without any version of windows has made me prefer linux so im not really gonna need my XP anymore except for games.

---

### Post by crane on 2005-02-04
[QUOTE=Frazer] so im not really gonna need my XP anymore except for games.[/QUOTE]

yea but thats changing fast too!!


As far as duel booting, You need to install windows first. Windows bootloader is not compatable with linux at all.
If I remember correctly to change the MBR you have to do a low level format or something like that.
 the whole drive will have to be erased and reformated including the MBR. After that you can install windows, then linux.

Good Luck

---

### Post by thestarman on 2005-02-07
[QUOTE=Frazer]When I first set up Ubuntu I Formatted my hd and got rid of windows because I wanted to clear it out.  I left 60gb of space to use for xp at a later date.  My Ubuntu system was working fine after the install.  I went to install XP again, and after the install when it reboots I get an error loading operating system message.  Now both Linux and Windows will not run. I've reinstalled windows again and same problem.  If I reinstall Ubuntu it works fine.  Someone told me this could be to do with the boot Loader on the Ubuntu disk sets up (i think its GRUB) im not sure what the problem is though.  I am quite a noob to all this linux stuff and I have never had to use a boot menu to swich between OS's.  anyone got any ideas on what the problem is, thanks.[/QUOTE]

Frazer,

So far I haven't seen any answers telling you what's wrong!  So, I'm replying... some were a bit close, but never flat out said this:  **WINDOZE NT/2000/XP/2003 OSs can not *normally* boot up, UNLESS they can control the first partition of the first hard drive!**  By installing Linux in your first HDD partition, you've made it impossible for them to do so, since they can't control Linux partitions (thankfully)!  Although it *might* be possible to run a system like this if you **hide** the Linux partition; note I only said might, I suggest that you re-install Windoze XP in the very first partition, leaving EMPTY SPACE for other partitions, and then install Ubuntu Linux after that!  Ubuntu will set up the GRUB boot manager with Win XP listed on the menu so you can boot up to either OS.  :-) 

Daniel.
[http://thestarman.dan123.com/](http://thestarman.dan123.com/)

---

### Post by darkcoder on 2005-02-15
Also, many system utilities like Norton Utilities will warn you about your invalid boot sector if you install grub there.  The best way to make it Xp friendly it's to use NTLDR as your primary boot loader and add Linux to that XP boot menu, and then install grub on your / partition.

More info about the process [here](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

