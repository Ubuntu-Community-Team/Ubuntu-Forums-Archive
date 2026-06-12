---
title: "how to uninstall xubuntu from dual boot laptop"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by pdrift on 2007-05-19
hi, i bought a laptop from a friend at work the other day, its an old ibm thinkpad 600x
with p3 500mhz and over 300mb of ram. it had windows xp on it when i got it so i defragged 
and resized the partition to give me some room to install xubuntu. i chose xubuntu because
my understanding is that it runs better on older hardware than ubuntu does but now i don't like 
it as much as ubuntu.

my question is, how do i go about removing xubuntu of the harddrive so i can install ubuntu to that 
partition instead. i don't know if i can just erase the partition because i still want to dual boot windows and I'm not sure if i erase the xubuntu partition will i still be able to boot up windows.
isn't there some files for grub on the linux partition??  like the menu.lst or something.

i want to go from xubuntu to ubuntu on the second partition without disturbing win xp on the first.
 thanks in advance, i sure do aprreciate it.:confused:

---

### Post by zenwalker on 2007-05-19
Just install the ubuntu over xubuntu partition, and it will format that driver wiping out every thing there. Tats simple.

Other way is, format that partition of Xubuntu and then install the ubuntu on it.

---

### Post by mi_were on 2007-05-19
> **pdrift said:**
> hi, i bought a laptop from a friend at work the other day, its an old ibm thinkpad 600x
with p3 500mhz and over 300mb of ram. it had windows xp on it when i got it so i defragged 
and resized the partition to give me some room to install xubuntu. i chose xubuntu because
my understanding is that it runs better on older hardware than ubuntu does but now i don't like 
it as much as ubuntu.

my question is, how do i go about removing xubuntu of the harddrive so i can install ubuntu to that 
partition instead. i don't know if i can just erase the partition because i still want to dual boot windows and I'm not sure if i erase the xubuntu partition will i still be able to boot up windows.
isn't there some files for grub on the linux partition??  like the menu.lst or something.

i want to go from xubuntu to ubuntu on the second partition without disturbing win xp on the first.
 thanks in advance, i sure do aprreciate it.:confused:


Hi, the long and short of it is that Xubuntu and Ubuntu share the same basic structure, u can therefore just add the Ubuntu desktop to you computer and be good to go.

U can add the Ubuntu desktop in synaptic by install the Ubuntu-Desktop package or at the terminal by using

$ apt-get install ubuntu-desktop

If you really don't want to have kubuntu the uninstall in synaptic by deselecting the Xubuntu-desktop package.

If should be that simple.

---

### Post by pdrift on 2007-05-19
ok so i can do all of this right from xubuntu right? but i'm having a problem.
everytime i try to start up the terminal, it kicks me out back to the log in screen.

and i haven't gotten an internet connection working in xubuntu so i don't think i'll be able to 
use synaptic. 
i tried to boot off the ubuntu 7.04 cd but i get this error;

[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required
  to enable ACPI
[   189.240805] invalid compressed format (er=1)
[   189.253103] kernel panic - not syncing: vfs: Unable to mont root fs on unkno
wn-block(104,1)
[   189.253446]

whats all this mumbo jumbo????

---

