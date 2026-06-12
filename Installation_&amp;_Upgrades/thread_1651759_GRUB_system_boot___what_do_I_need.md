---
title: "GRUB /system boot   what do I need ?????"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by dreuzel on 2010-12-23
GRUB /system boot   what do I need ?????

I used to have a window  system that can  boot a disk... ok this is not perfect  but an unique position 
is required to start, otherwize you are in a mess anyhow... (MBT)  this used to be called a boot block...

A had a boot.ini to  switch between  boot-able systems.....


Then I had to learn GRUB....   a mystical  device naming convention  troubled me 
from finding the right disk a cryptic description  blocked me to  find what I needed ... ok as long  as I stick to one and the same system  i can 
get it to work  controlling a  well hidden  grub.lst file .....



Now this is improved,????!!!???
Disk  names have become  magical number dependent on location and content nothing is transparent  any more ... 1 error (switched disk order .... and  the boot goes completely in the mist
with 3 disks  you have hundreds of combinations  99 of them clearly failing 
(sorry did not and refuse to read 100 pages manual  description to do a simple thing)

As I want to change anything I have to dive in very complex system of  all different files 
and somewhere within  100 lines patch  some information....????
Nothing happens  only upto when I Run a difficult procedure  that should help me boot my system 
but as I can not boot my system  I have no Internet.... I can not find the  procedure ....

so the best option is to erase the system ...

Where are we going to ????   what happened to  clean and simple ??
why is booting the most complex UNIX operation in the world 
  this is NO design......

Can someone please advise on a CLEAN ands simple  boot system That works....
is NOT COMPLEX and tricky  where  I can  simply chose  between a few system disks and 
press a button and viola ....

I URGENTLY NEED TO KILL THE NEW GRUB in Ubuntu 10.10 it is a messs

---

### Post by kansasnoob on 2010-12-23
It's not at all clear to me what problems you're having with grub 2 but I wrote this HowTo for those corner issues where legacy grub is either needed or desired:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

If you need more detailed help then we really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

