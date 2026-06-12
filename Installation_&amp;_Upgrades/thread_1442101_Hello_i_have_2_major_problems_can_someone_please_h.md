---
title: "Hello i have 2 major problems can someone please help me"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2010-03-29
hello i am selling my laptop and i need to get rid of ubuntu (am going to install it on my new laptop) 

first what does this mean ?? if run this in my ubuntu terminal , what does it do ??? thanks

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr



i have windows 7 and ubuntu (my laptop orginaly came with windows 7 and no disks just recvoey manger)  how do i remove ubuntu and the grub loader ( i know how to get rid of the partion disk management delte format etc)  
how do i remove the grub loader so that the laptop boots striaght from windows 7 and the grub is not there it goes directly to windows 7 

Thank You:)

---

### Post by raymondh on 2010-03-29
The first command installs lilo (a bootloader) into your MBR ... effectively overwriting GRUB.  You want to revert your system back to original windows and it's bootloader.

Here's another alternative.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Download the appropriate version (32 or 64 bit) and burn to disc.  Boot into the disc. 

A quick google search on how to repair the MBR for windows:

[http://www.wired2tech.com/forum/viewtopic.php?t=225](http://www.wired2tech.com/forum/viewtopic.php?t=225)

After repairing your MBR, you will only boot into windows ... you can still use the win7 disk management utility to delete Ubuntu and it's partitions, as well as enlarge the existing windows.  Remember to run checkdsk.

As always, back-up your files first.

Good luck.

Raymond

---

### Post by balkrish999 on 2010-04-01
> **raymondh said:**
> The first command installs lilo (a bootloader) into your MBR ... effectively overwriting GRUB.  You want to revert your system back to original windows and it's bootloader.

when i type the two comands in ubuntu will i get my original normal windows bootloader back the orginal 1 ???   cas iwant the orinial 1

---

### Post by Mark Phelps on 2010-04-01
Recommend you use the repair disk from the link to restore Win7 boot loader.  You will have to boot using it and run Startup Repair three times -- because it replaces the MBR on the third pass.

After that, as already indicated, you should boot directly into Win7 and use the Disk Management utility to remove the Ubuntu partition(s) and resize the Win7 partition to fill the unused space.

---

### Post by raymondh on 2010-04-01
> **Mark Phelps said:**
> Recommend you use the repair disk from the link to restore Win7 boot loader.  You will have to boot using it and run Startup Repair three times -- because it replaces the MBR on the third pass.

After that, as already indicated, you should boot directly into Win7 and use the Disk Management utility to remove the Ubuntu partition(s) and resize the Win7 partition to fill the unused space.

+ 1  (Thanks Mark Phelps!)

2 OP, after deleting ubuntu and resizing win7, also run a checkdsk.

Raymond

---

### Post by balkrish999 on 2010-04-01
> **Mark Phelps said:**
> Recommend you use the repair disk from the link to restore Win7 boot loader.  You will have to boot using it and run Startup Repair three times -- because it replaces the MBR on the third pass.

After that, as already indicated, you should boot directly into Win7 and use the Disk Management utility to remove the Ubuntu partition(s) and resize the Win7 partition to fill the unused space.


i have downloaded the windows 7 64 bit repair disk and burnded it to a cd-rw 

but why does i have to run the strat up repar 3 time s????

---

### Post by balkrish999 on 2010-04-01
also shall i remove ubuntus partions from  windows 7 from disk magament and then do the reapri disk thing 

or shall i do the repair disk thing first and then remove the partion which 1 thanks :):):)

---

### Post by balkrish999 on 2010-04-01
i have downloaded the windows 7 64 bit repair disk and burnded it to a  cd-rw 

but why does i have to run the strat up repar 3 time s????

also shall i remove ubuntus partions from  windows 7 from disk magament  and then do the reapri disk thing 

or shall i do the repair disk thing first and then remove the partion  which 1 thanks

---

### Post by raymondh on 2010-04-01
> **balkrish999 said:**
> i have downloaded the windows 7 64 bit repair disk and burnded it to a  cd-rw 

but why does i have to run the strat up repar 3 time s????

[COLOR="Red"]As Mark Phelps said ... "it repairs on the 3rd pass"[/COLOR]

also shall i remove ubuntus partions from  windows 7 from disk magament  and then do the reapri disk thing 

or shall i do the repair disk thing first and then remove the partion  which 1 thanks

[COLOR="Red"]1.  Repair your MBR (master boot record) first.
2.  Then, delete Ubuntu
3.  Then, expand the existing windows7 to take up the unallocated space
4.  Then, reboot and if told to run checkdsk, do so.[/COLOR]





[COLOR="Red"]Raymond[/COLOR]

---

### Post by balkrish999 on 2010-04-02
> **raymondh said:**
> [COLOR=Red]Raymond[/COLOR]


when i click on start up repair 3 times nothing happens what shall i do now?

---

