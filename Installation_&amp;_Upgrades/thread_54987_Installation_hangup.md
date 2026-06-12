---
title: "Installation hangup"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by Myrdhyn on 2005-08-07
Hello all,

Ok I am new to ubuntu forums so lemme give you a bit of background before I get to my problem. I have been working on windows for years (repair shop, net administration etc etc) and have just plain got sick of windows basically murdering itself all the time and would LOVE to make the big jump to complete linux on my home system(s).  I've toyed with linux/unix OSes in the past a bit but I am still a pretty big linux noob.  I did some reading and decided that ubuntu ( and kubuntu) are exactly what I want in a linux distro or os period.  So I downloaded it and burned the iso and went to install.  Here's where the problem starts...every time it gets to install stage 2 and gets down to setting up the packages I get a complete and utter system hang when it is trying to setup the xserver-xorg package :\ I have tried reinstalling about a billion times, redownloaded it and burned new copies about 2 and tried downloading and installing the 64-bit version (have an AMD64 but i have reasons for not wanting the 64bit distro at this time) and tried downloading kubuntu (which i hope to switch to eventually anyway as i prefer kde) nothing works it always hangs when it gets to setting up xserver-xorg...not a kernel panic, i dont have any flashing lights...just a complete lockup, can't type anything, cant hit num/caps/scroll lock, have to powercycle it.

Any ideas?

---

### Post by varunus on 2005-08-07
What video card do you have?  What about keyboard/mouse? (USB or PS2?  Brand?)

You could try doing a "server" install (by typing server at the installation boot prompt).  This will install without X (and hence with no GUI).  You can then try installing X manually and see if it works better...

---

### Post by Myrdhyn on 2005-08-07
video card is a radeon 9800 pro 256meg 256bit ddr2
mouse is a  usb microsoft wireless...grrrr cant think of name off the top of my head its the one with the wheel that moves side to side also
keyboard is just some cheap ps2 keyboard (dont need anything fancy)

hmm i could try a server install but the problem is...i've never done anything like that before with linux :\  when i say i've toyed around with linux a bit...i basically mean mandrake gui install or fedora/red hat where basically i didnt have to do much (just wanted to get kinda a taste of linux easily), or I've done some very basic stuff in a unix console (solaris 9 i believe) for a programming class i had to take (had to compile on the sun cluster) but that doesnt mean I am not willing to try some crazy stuff :p lol lord knows i've done backflips for windows in my day :D

edit: anyone else have anymore ideas?

---

### Post by Myrdhyn on 2005-08-07
noone has any other ideas? 

edit: got it working....only thing i did different was setup the partitions a bit different (and more like i like them anyway) and go with reiserFS instead of ext3, that and the video card question tipped me off that maybe the installer didnt like me havin my monitor on the dvi port of my vid card so i switched it over to vga

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 am glad u got it working

the biggest problem when moving from windows to linux is still thinking windows
and that just don't work

i am still getting there but have Kubuntu running on 3 systems here at home
so its learn it or bust for me
cos i ain't going back to that abomination called windows :) ...

---

