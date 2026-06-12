---
title: "When i install Ubuntu .. WinXp stop working"
date: 2004-12-29
forum: Installation &amp; Upgrades
---

### Post by globalspace on 2004-12-29
Hi guys,
i'm very confused  :confused: 

i've installed WindowsXp on a partition of 15GB .. and i keep the space remaining free without partition ...
WindowsXp works ...
I've installed Ubuntu .. i've done this parttion :
- 15GB of Linux Ext3
- 600MB of Swap
- 8.5 GB of Fat32

When i select on GRUB Ubuntu works ... but when i select Windows Xp it starts to load .. and the blue bar starts to move ... and then it stops .. and it crash ...

:(
I don't know what to do ... Help please :(

---

### Post by hardcandy on 2004-12-29
Can you cut and paste a copy of your "/boot/grub/menu.lst " and "/etc/fstab" files to the forum?

One other thing, is WinXP on the first partition of the hard drive?

---

### Post by globalspace on 2004-12-29
[QUOTE=hardcandy]Can you cut and paste a copy of your "/boot/grub/menu.lst " and "/etc/fstab" files to the forum?

One other thing, is WinXP on the first partition of the hard drive?[/QUOTE]

yes **WinXp** is in the **first partition /dev/hda1 **.. 

and this is a copy of my **/boot/grub/menu.lst **

[http://paste.phpfi.com/43676](http://paste.phpfi.com/43676)

... and **/etc/fstab**

[http://paste.phpfi.com/43675](http://paste.phpfi.com/43675)

thanks for the help  ;)

---

### Post by globalspace on 2004-12-29
i see that i can start windows in MODALITA' PROVVISORIA ... i don't know how to translate in english .. maybe " Rescue Mode"  :oops: 
but i have the same problem if i start in Normal Mode

---

### Post by feneks on 2004-12-29
Which partition has the boot-flag?
If I figured it out correctly the windows partion needs the boot flag to work.

reference:
[http://www.ubuntuforums.org/showthread.php?t=6132&page=1&pp=10&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=6132&page=1&pp=10&highlight=dual+boot)

otherwise you could try
*rootnoverify (hd0,0)* instead of *root (hd0,0)*

---

### Post by Rancoras on 2004-12-29
[QUOTE=globalspace]When i select on GRUB Ubuntu works ... but when i select Windows Xp it starts to load .. and the blue bar starts to move ... and then it stops .. and it crash ...[/QUOTE]

What blue bar?

---

### Post by globalspace on 2004-12-29
[QUOTE=feneks]Which partition has the boot-flag?
If I figured it out correctly the windows partion needs the boot flag to work.

reference:
[http://www.ubuntuforums.org/showthread.php?t=6132&page=1&pp=10&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=6132&page=1&pp=10&highlight=dual+boot)[/QUOTE]


boot flag was on Linux ... now i putted into Windows 's partition 

i have this problem :

when i **shutdown**  my notebook and i select winxp from grub **all works fine ** .. but if i **reboot**  from linux and i select winxp , it **crash** on loading 
(where i see the logo's WindowsXp and the bar under it)
 :cry:

---

### Post by globalspace on 2004-12-29
[QUOTE=Rancoras]What blue bar?[/QUOTE]

the bar under the logo of Windows Xp .. the bar which move from left to right  :oops:

---

### Post by feneks on 2004-12-29
already looked at [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) ?

---

### Post by globalspace on 2004-12-29
[QUOTE=feneks]already looked at [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) ?[/QUOTE]

i don't know what to search because i don't have an error message ...  :confused:

---

### Post by feneks on 2004-12-29
Haven't read your posting:
[QUOTE=globalspace] when i **shutdown**  my notebook and i select winxp from grub **all works fine ** .. but if i **reboot**  from linux and i select winxp , it **crash** on loading [/QUOTE]

 :confused: 

I can only imagine one thing that might be responsible. WinXP gets confused about contents of RAM which wasn't killed by reboot.   :confused:  :confused:

---

### Post by hardcandy on 2004-12-29
As far as bootable flags, both the linux and the WinXp partitions need to be bootable and need the flag set. 

> when i shutdown my notebook and i select winxp from grub all works fine .. but if i reboot from linux and i select winxp , it crash on loading  
I'm thinking it could be a power management issue, I do not have Ubuntu on a laptop, can you turn off the suspend function?

---

### Post by globalspace on 2004-12-30
i've tryied to disable the Suspend Mode .. but i've done this :
on the ScreenSaver Preferences -> Advanced i've disabled Power Management (which have the option Standby,Suspend and Off)
nut the problem still remain... :(

for the ram i don't know what to do if is the ram  :confused: 


PS. I see that when i do REBOOT , Ubuntu says " Stop Power Management" -> "[OK]" ... so i think that Ubuntu disable it


PPS. I'm doing a Memory Test (ram) with MemTest86 ... i hope to find the problem :(

---

### Post by feneks on 2004-12-30
[QUOTE=globalspace] PPS. I'm doing a Memory Test (ram) with MemTest86 ... i hope to find the problem :( [/QUOTE]
I don't think you will find a problem this way. My theory just assumes that Ubuntu lefts some information in RAM, then Windows boots and recognices this information and can't handle with it. - But this doesn't sound likely.  :sad:

---

### Post by shmk on 2005-04-21
[QUOTE=feneks]I don't think you will find a problem this way. My theory just assumes that Ubuntu lefts some information in RAM, then Windows boots and recognices this information and can't handle with it. - But this doesn't sound likely.  :sad:[/QUOTE]
 I got same problem sometimes.

If I leave Ubuntu with the "restart computer" command and then try to enter in winxp appear the winxp loading page and then my computer automatically shutdown  :???:

---

