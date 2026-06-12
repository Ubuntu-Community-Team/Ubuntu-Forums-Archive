---
title: "windows won't boot anymore after hardy update"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by muckv on 2008-05-24
Hey guys 

i have 4 partitions 


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4847    38933496    7  HPFS/NTFS
/dev/sda2            4848        6671    14651280   83  Linux
/dev/sda3            6672        6707      289170   82  Linux swap / Solaris
/dev/sda4            6708        9729    24274215    7  HPFS/NTFS


sda1 is the one with windows xp on it

when grub loads up, i can select windows xp. When i choose windows, it gives me another boot menu(as normal), a windows boot menu with 2 choices

-Windows xp media center
-Windows recovery console

When i choose windows xp my computer just reboots.

Any help?

---

### Post by cdtech on 2008-05-24
Boot into the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

```
sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```
grub >find /boot/grub/stage1
```

Whatever was returned for the find command use it in the next step (you are still at grub>.

```
grub >root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
grub >setup (hd0)
```

Then exit the grub shell

```
grub> quit
```

Hope this helps.......

---

### Post by muckv on 2008-05-24
I only have 7.10 ubuntu cd, is that ok?

---

### Post by cdtech on 2008-05-24
Sure.

---

### Post by muckv on 2008-05-25
this does not work, i still have the same problem

other ideas?

---

### Post by louieb on 2008-05-25
Don't think the Hardy update has anything to do with with windows failure to boot. Once you get to the Windows menu Grub has done its job and transfered control to Windows.

What happens when you try to loead the recovery console? 
The next thing I would try is to boot windows in safe mode. 
or if thats not an option boot to the recovery console and run **chkdisk**.
May be you have a windows virus are you running a virus scanner in Windows? 
Can you see your folders and files in your windows partition from Ubuntu?

---

### Post by muckv on 2008-05-26
Whatever option i chose, a reboot is the result. The windows partition is mounted in ubuntu as usual, and i don't have a virus.

---

### Post by cdtech on 2008-05-26
The only other choice I can think of is to fixmbr on the Windows MBR to see if your Windows will boot on it's own. This will remove the GRUB bootloader from the MBR of the NTFS (primary Windows disk) so you'll be able to boot right into Windows. GRUB can be reinstalled once you've corrected your Windows problem.

Hope this helps......

---

