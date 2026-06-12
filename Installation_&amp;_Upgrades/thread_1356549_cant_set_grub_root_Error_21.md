---
title: "cant set grub root Error 21"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by madmaze on 2009-12-16
Hello everyone,
Here is my dilemma:
I used to have centOS on my machine taking up half the hdd, the other half with Ubuntu 9.04.
so my partitions were setup like so:
/dev/sda1 465gb primary part. -centOS
/dev/sda4 465gb extended part.
       /dev/sda5 -ubuntu root
       /dev/sda6 -swap
       /dev/sda7 -ubuntu home dir
now I had the brilliant idea to get more space on my HDD so I formatted /dev/sda1 and that was where i think grub was. Now ive had my fair share of grub problems in the past and most of them just consisted of me booting from a live disk, then >grub >root (hd0,0) then >setup hd0 and that was it.

now for some reason everything ive tried resulted in "Error 21: Selected disk does not exist".
Ive tried root (hd0-4,0-5) and same error everytime.
any suggestions?
is it possible it doesnt like that my ubuntu is on an extended partition?

---

### Post by phillw on 2009-12-16
> **madmaze said:**
> Hello everyone,
Here is my dilemma:
I used to have centOS on my machine taking up half the hdd, the other half with Ubuntu 9.04.
so my partitions were setup like so:
/dev/sda1 465gb primary part. -centOS
/dev/sda4 465gb extended part.
       /dev/sda5 -ubuntu root
       /dev/sda6 -swap
       /dev/sda7 -ubuntu home dir
now I had the brilliant idea to get more space on my HDD so I formatted /dev/sda1 and that was where i think grub was. Now ive had my fair share of grub problems in the past and most of them just consisted of me booting from a live disk, then >grub >root (hd0,0) then >setup hd0 and that was it.

now for some reason everything ive tried resulted in "Error 21: Selected disk does not exist".
Ive tried root (hd0-4,0-5) and same error everytime.
any suggestions?
is it possible it doesnt like that my ubuntu is on an extended partition?


Hi, I'd go for a re0installation of Grub. As you're on 9.04, you should be on Grub legacy. To do that .... 

> 
[LIST=1]
[*]Install GRUB 0.97 
[LIST]
[*]sudo apt-get install grub 
[/LIST]
[*]With *grub* installed, the user must still create the *menu.lst* and *stage1/stage2* files by running the following two commands. 

[LIST=1]
[*]sudo update-grub 

[LIST]
[*]Generates *menu.lst*  

[LIST]
[*]Tab to "Yes" when prompted. 
[/LIST]
[/LIST]
[*]sudo grub-install /dev/sdX 

[LIST]
[*]Choose the correct device (sda, sdb, etc), normally the one on which Ubuntu is installed. 
[*]Creates the *stage1* & *stage2* files in */boot/grub* and writes to the MBR. 
[/LIST]
[/LIST]
[*]Reboot
[/LIST]


Another way is ....

> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.


Either one should get you up & running.

Regards,

Phill.

---

### Post by darkod on 2009-12-16
> **madmaze said:**
> Now ive had my fair share of grub problems in the past and most of them just consisted of me booting from a live disk, then >grub >root (hd0,0) then >setup hd0 and that was it.

now for some reason everything ive tried resulted in "Error 21: Selected disk does not exist".


It all depends which grub were you using, from which installation. If you were restoring it with root(hd0,0) most probably you were using grub from centOS. With deleting that partition you deleted / and also /boot folder inside it.
If you never used grub from Ubuntu 9.04 (provided that's what you're using), I'm not sure how to reinstall it best.
If you never had /dev/sda5/boot folder and grub files inside, it can't just restore it.

---

### Post by madmaze on 2009-12-16
Thanks for all the quick replys.

I figured it out.. I was running off of a ubuntu live disk.. and i assume that must have been the problem.. I popped in the gparted live disk and double checked my partitions.. thankfully that disk also has grub on it.
then it was as easy as finding the right partition >root (hd0,4) then >setup (hd0) and finally >sudo reboot 

Im not sure why the live disk didnt work.. i did exactly the same thing.. 

@darkod: I did have bootloaders on both centOS and Ubuntu, but the Ubuntu grub called centOS's Lilo.. so grub was def on that partition.

thanks again for the replys

---

