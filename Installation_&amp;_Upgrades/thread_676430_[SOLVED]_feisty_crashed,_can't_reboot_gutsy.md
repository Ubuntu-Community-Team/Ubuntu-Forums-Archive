---
title: "[SOLVED] feisty crashed, can't reboot gutsy"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by ubu-lemon on 2008-01-23
i have serious trouble with my packard bell laptop
here is what happened :

1)
- i bought a vista laptop last autumn
- i decided to try linux (feisty fawn 7.04)
- most worked out well, some trouble with the ati before i got sound,
 and a little internet connection problem, both solved
- no driver for my webcam, and video was still something i needed to figure out
-also some trouble with printing, it all went ok, till something changed i don't know what

2)
- i installed some stuff here and there, the system was really stable, i was happy
- also things that never worked on windows before suddenly functioned without i had to do anything at all, as said i was happy
- i installed some stuff a few days ago (are they the source of my problem? --->'lilypond' and 'jack')

3)
-when starting up my computer, it does a usual check it does once so often, and it discovers 
'/dev/sda3/: multiple-claimed blocks in inode 3653894 : 7324822  7324822.
-ubuntu says 'unexpected inconsistency; run fsck manually' and then 'fsck died with exti status 4'
and it says ''teh fsck should be performed in maintenance mode'
which it does
-but then it says that ti cannot find 'apt get', that i should install it by typing 'apt get install apt' which i do but nothing happens. 
-someone suggests me to do a clean installation (and why not gutsy)

4) 
- i burn the image, check it
- i start the computer with the cd (boot is set to 'boot from cd' first), nothing happens, i hear the cd turn for about 30 sec then it stops. then it goes back to grub, with the usual menu and the process starts all over again, till were i'm again in the 'bad blocks'-stuff


help !! 
(i'm still a bit new so please don't make it too complicated, thanks)

---

### Post by Pumalite on 2008-01-23
Your hard drive might be going south. Check with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://sysresccd.org/Download](http://sysresccd.org/Download)

---

### Post by ubu-lemon on 2008-01-24
i'll take a look at it tonight when i'm back home.

could you tell me a little bit what will happen (give a general idea of it) when i insert these testdisk and/or the other? (i have difficult doing things if i don't have some kind of image of what i'm doing and
the site does not give a lot of info about that, just that it will recover lost stuff)


thanks

---

### Post by c0met on 2008-01-24
Have you tried that apt-get command with sudo in front of it?

eg. sudo apt-get install apt (also note the hyphen)

Some ideas that occurred to me...
[LIST]
[*]If your processor is a 64 bit one, are you using the correct install version of Ubuntu?
[*]Try reburning the ISO onto CD at a slower speed. From reading forums, it seems that this often works.

---

### Post by ubu-lemon on 2008-01-24
> **c0met said:**
> Have you tried that apt-get command with sudo in front of it?
eg. sudo apt-get install apt (also note the hyphen)

no, i haven't, i will now ... (have to wait till it does the whole check, that takes some minutes)
(i did not forget the hyphen, only just here cause it was from memory i wrote that, the other i had written down)
so... it says 'sudo: command not found' 


Some ideas that occurred to me...
[LIST]
> **c0met said:**
> 
[*]If your processor is a 64 bit one, are you using the correct install version of Ubuntu?
[*]Try reburning the ISO onto CD at a slower speed. From reading forums, it seems that this often works.

no, it's not a 64bit laptop
i did burn the iso at low speed cause that's the only thing my dear old windows 98 does...
i might try form a usb stick perhaps? (should i set the boot device priority to  'removable device' then?)

---

### Post by ubu-lemon on 2008-01-24
> **Pumalite said:**
> Your hard drive might be going south. Check with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://sysresccd.org/Download](http://sysresccd.org/Download)


another question...
will this TestDisk and the sysresccd do something that does not allow me to go back?
i mean : suppose there is nothing wrong with my harddisk and there is still another way to make my ubulap talk, should i then first try everything before trying these disks or doesn't it matter?

---

### Post by Pumalite on 2008-01-24
You can check the integrity of your hard drive, Partition Table,etc. Just don't format anything.

---

### Post by ubu-lemon on 2008-01-24
is TestDisk still on the computer or do i have to burn a cd for it?
(i'm a little saturated reading all this stuff, maybe it's just time for bed,
i don't see it, sorry)

i read :

[I]Running TestDisk executable 

If TestDisk is not yet installed, it can be downloaded from TestDisk Download. Extract the files from the archive including the sub-directories. 

To recover lost partition or repair filesystem from hard disk, USB key, Smart Card..., you need enough rights to access physical device. 
 Under Dos, run TestDisk.exe 
 Under Windows, start TestDisk (ie testdisk-6.9/win/testdisk_win.exe) from an account in the Administrator Group. Under Vista, use right-click "run as administrator" to launch TestDisk. 
 Under Unix/Linux/BSD, you need to be root to run TestDisk (ie. sudo testdisk-6.9/linux/testdisk_static)[/I]

i'm currently in grub's list 
and i have the choose from that list
1)ubuntu, etc,(which will eventually lead me to the detection of the bad blocks) and also a vista loader(but that one is half broke i think, i'm not tempted to try it, it suggests me to start a complete restore i think or at least it did a few months ago)

or
2)to write 'e' to edit the commands before booting, or 'c' for a command-line

---

### Post by ubu-lemon on 2008-01-25
it's solved!!!!


an online friend suggested me to write
'fsck /dev/sda3'

which fixed the problem  :-)


thanks for your replies and the TestDisk might still be handy an other time 
(if only i get to understand how to use it that is :-) )

---

