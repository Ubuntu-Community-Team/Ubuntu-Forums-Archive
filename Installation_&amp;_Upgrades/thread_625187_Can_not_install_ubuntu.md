---
title: "Can not install ubuntu"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by jakey123 on 2007-11-27
When each time I try to install ubuntu 7.10 It says
Grub can not load 5:lolflag:

---

### Post by torgrot on 2007-11-27
This is not a good error follow the instructions below.  Are you certain it was error 5?

Quoted from the GNU/GRUB manual

    5 : Partition table invalid or corrupt
        This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 

Check the partition table by running fdisk as root ('sudo fdisk -lu) in Linux, or use your favorite partition editing software to make sure one of your partitions has been marked 'active'.

If no partition is marked as active, you can use Super GRUB Disk to do that for you.
If more than one partition has already been marked as active, you need to remove the 'active' flag from one of them, as only one is supposed to be set as active at a time. Use your partitioning software of that.

torgrot

---

### Post by jakey123 on 2007-11-27
Well I can't remember i'm honist how can you tell
but I;m back in windows I looked up some stuff It says It may not be compatable with your bios

---

### Post by jakey123 on 2007-11-28
):P Hi there it did't say Partition table invalid or corrupt Is a hard drive a Partition sory I don't know how to spell Partition.  I need some more help

---

### Post by Pumalite on 2007-11-28
What kind of computer do you have?

---

### Post by twist2b on 2007-11-28
yea 
1. post your specs...
2. what exactly have you done
3. how did you partition your drive? becuase thats important....
4. you should prob start over..... if your dual booting then go to xp or vista.... w/e you have and re-create the partition

---

### Post by jakey123 on 2007-11-29
I have a Dell 2400 running Windows Xp SP2

---

### Post by Pumalite on 2007-11-29
'The Dimension 2400 is a budget home/office system based on Intel's i845GV chipset, and houses a Celeron 2.4Ghz processor (in the model we tested) or a Pentium 4 up to 2.8 GHz. Depending on the processor, the system uses either 266MHz or 333MHz DDR memory, up to 1GB worth. Graphics and sound are provided by Intel's 'Extreme' integrated graphics chipset and Soundmax integrated audio respectively. Nothing to write home about here, but adequate for the PC's intended role as an office machine. A 40GB hard disk provides storage, and a 48X CD-ROM drive is present for software and music. No floppy drive was included in the system we reviewed, though a slot for one is built into the custom Dell case.'

How much memory do you have? Besides that, I'd use the Alternate CD to install.

---

