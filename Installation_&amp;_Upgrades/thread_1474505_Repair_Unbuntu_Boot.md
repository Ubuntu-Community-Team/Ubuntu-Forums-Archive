---
title: "Repair Unbuntu Boot ?????????????????"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Alexdelpiero1974 on 2010-05-06
Would you please tell me , How to repair Unbuntu Boot ?
i already have installed ubuntu 10.04 on my harddisk 
but my computer only boot windows , like ubuntu is not there ????
there is no selection screen 

please advise how to repair the boot only , to access Ubuntu 

another i checked the forum , there is alot of explaination about 
how to solve this problem , but with commands 
and i lost in it , i can't figure out , how to do it by command 

is there is any GUI program to fix boot problem

another thing How come that Ubuntu make a system with a repair for it 

the big question is do i have to install it once again , instead of repair 
the only boot problem ????


Please check and advise

---

### Post by Mark Phelps on 2010-05-06
> **Alexdelpiero1974 said:**
> ... is there is any GUI program to fix boot problem ...

Quick answer -- NO.  You will have to use the terminal (command line interface) to diagnose the problem and to fix it.  IF you're not willing to learn terminal commands, you've chosen the wrong OS.

---

### Post by Alexdelpiero1974 on 2010-05-06
so why bother ubuntu to make GUI in it's OS in the first place 

GUI is for flexibility and new user in OS in the world
and Commands also is for advanced users 

be in my place , i'm in linux world and want to shift from F**kin Microsoft 
and sure you know why ? 
so i'm putting ubuntu in trail to know if it's work for me or not 

and it's time to install and it's lost it's boot ???

what should i do ??????? 

> **Mark Phelps said:**
> Quick answer -- NO.  You will have to use the terminal (command line interface) to diagnose the problem and to fix it.  IF you're not willing to learn terminal commands, you've chosen the wrong OS.

---

### Post by dino99 on 2010-05-06
at the end of bios process hold "shift" key down to see the grub menu (if it really installed)

grub2 might be installed on ubuntu partition (ie /dev/sd?, "?" is a letter, you might have noted it when formatting)

sudo grub-install --root-directory=your-ubuntu-partition

then

sudo grub-mkconfig && update-grub

---

### Post by marcusjames on 2010-05-06
[SIZE=2]open a terminal and copy and paste this:

sudo update[/SIZE]-grub

---

### Post by Alexdelpiero1974 on 2010-05-06
Currently i have only XP boot , when boot there are no ubuntu @ all
i can only boot from Ubuntu CD , to work as live 
my ubuntu installed in /dev/sda6


> **dino99 said:**
> at the end of bios process hold "shift" key down to see the grub menu (if it really installed)

grub2 might be installed on ubuntu partition (ie /dev/sd?, "?" is a letter, you might have noted it when formatting)

sudo grub-install --root-directory=your-ubuntu-partition

then

sudo grub-mkconfig && update-grub

---

### Post by Alexdelpiero1974 on 2010-05-06
Currently i have only XP boot , when boot there are no ubuntu @ all
i can only boot from Ubuntu CD , to work as live 
my ubuntu installed in /dev/sda6


> **marcusjames said:**
> [SIZE=2]open a terminal and copy and paste this:

sudo update[/SIZE]-grub

---

### Post by Alexdelpiero1974 on 2010-05-06
I found this link :
[ftp://alpha.gnu.org/gnu/grub/](ftp://alpha.gnu.org/gnu/grub/)

which one of those can i download and how to put it on my ubuntu 
to make boot and work once again 


> **Alexdelpiero1974 said:**
> Currently i have only XP boot , when boot there are no ubuntu @ all
i can only boot from Ubuntu CD , to work as live 
my ubuntu installed in /dev/sda6

---

