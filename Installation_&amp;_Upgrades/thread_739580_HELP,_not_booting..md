---
title: "HELP, not booting."
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by WEIR_SJ on 2008-03-29
right i will start by saying HI,

now that is out the way i need help i have never used linux before and seen this ubuntu for the first time today, and have been trying to get it to work all day. First i tried the 7.10 for 64 bit pc and that dint work, next i tried the newer beta 8.04 and that too did not work...

...after reading a few different post i downloaded and tried the alternative cd and this has seemed to install fine, untill it ask me to remove the install cd and do a reboot, again all was fine untill i get to the loading screen with the process bar. as soon as the process bar comes up i get like 2mm across and everything stops, it just hangs....i need help.

system is as follows

motherboard = abit IP35 Pro
CPU = Itel quadcore Q6600
RAM = 2gb (ocz)
Gfx card = BFG 8800 GTX oc2
DVD drive = SATA Samsung

i have vista on a SATA 500gb HDD (this was unplugged while installing ubuntu) and have installed the ubuntu on a second SATA 250gb HDD


thanx in advance for any help.

Stuart W
ps. can any reply please be in the form on an idiot guide

---

### Post by Pumalite on 2008-03-29
You have two potential problems here: your Quad and your 8800GTX. Your card has been solved, but I don't know about your Quad Core. If you can afford to install 8.04 (in development. I have 2. They do great), I'd try Ubuntu 8.04 Live CD and if that doesn't work, try Ubuntu 8.04 Beta Alternate CD. Go for 64 bit.

---

### Post by WEIR_SJ on 2008-03-29
thanks i will give this a try (tho a bit reluctant, after spending all day just trying to get the one i have to install too)

just a note but i can not boot from the live cd's so will have to try the 8.04 alt.cd.


thanks again

Stuart W

---

### Post by Pumalite on 2008-03-29
You might be surprised by the 8.04 Beta Live CD.

---

### Post by WEIR_SJ on 2008-03-29
just to point out i from my original post i did try the 8.04 Live CD but all i got was an error...


think the last thing i seen on screen before it all froze was :-

root@ubuntu : ~#

but like i said im new to this and it may as well be in russian for me lol



thanx again

Stuart W

---

### Post by Pumalite on 2008-03-29
You are right then. Go for the Alternate CD.

---

### Post by WEIR_SJ on 2008-03-29
ok and thanks Pumalite for your help thus far....


....i will post back with an update after trying the 8.04 


out for now.
Stuart W

---

### Post by WEIR_SJ on 2008-03-30
**_**UPDATE**_**

ok im back but this time im typing this using firefox thou ubuntu.....

[IMG]http://i23.photobucket.com/albums/b374/sjweir76/ubuntu.jpg[/IMG]

now to get this far all i did was put the 7.10 alt. cd back in and do a recovery.

but sometimes it will boot and others it will not (more often the later)

i have done all the update (202 of them) and now it asking for me to do a restart (not sure i wanna do that lol, dont wanna spend 2 days getting it to boot again :(

any other help welcome

Thanks
Stuart W

---

### Post by Pumalite on 2008-03-30
Make a review and a backup of all your important files: menu.lst; ftab; org.conf, etc Compare blkid to fstab.

---

### Post by WEIR_SJ on 2008-03-31
ok that last post was in russian to me :confused::confused::confused:

---

### Post by Pumalite on 2008-03-31
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo cp /etc/fstab /etc/fstab.old
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
At the Terminal:
blkid
Save it in a file
Now: 
cat /etc/fstab
Now compare UUID's

---

