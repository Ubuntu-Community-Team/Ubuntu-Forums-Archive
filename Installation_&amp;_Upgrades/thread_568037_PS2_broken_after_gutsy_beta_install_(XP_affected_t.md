---
title: "PS/2 broken after gutsy beta install (XP affected too)"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by Vaphell on 2007-10-05
i have really nasty problem

i had XP SP2 on my PC and decided to slowly migrate to ubuntu. I use 6.10 daily in my work but I wanted to see what is in gutsy so i dloaded beta iso. I thought first ubuntu install would be test one anyway so no stress.

Live CD didn't find any PS2 hardware: logitech basic models of mouse and keyboard were frozen/bricked. I thought that it's some glitch and installed gutsy beta anyway. I moved mouse to USB and I filled text fields using clickable char table. That was a bad idea :[

result:
keyboard always freezes - just after selecting OS in GRUB, no matter what - both xp and ubuntu are affected. Spamming capslock stops changing indicator state.
I dloaded some small linux distro live cd and checked that keyboard still works in other OS. On the other hand 7.04 hangs just like 7.10beta

My only hope was that removing grub by fdisk /mbr somehow would fix the problem (but why it would... i have no idea). After some hassle i managed to do that - booting from cd was not affected because keyboard dies later, during hdd booting. Unfortunately booting straight to XP still bricks my keyboard. Keyboard works ok in recovery console of XP, but i have no idea what to do there.
I read similar threads and people suggested playing with bios settings, usb mouse and keyboard enabled/disabled but it doesn't seem to be doing anything - keyboard hangs no matter what.

So now i am without basic input device unable to to log in to any of OSes, i can just look at pretty login screens and that's about it. My pc is only useful as a file server as remote loging in to shared resources still works :/

Any idea what went wrong and why PS2 ports hang after ubuntu install even after removing grub? And more important: how to fix it ffs?
I will probably try to install xp again but i am not convinced it bring my keyboard back.


wtf? Why the hell ps/2 support in ubuntu still has issues after many releases? I read ancient threads indicating that every ubuntu distro was affected. I wanted to migrate to linux and ubuntu looked noob friendly enough for me ( i use 6.10 on my work laptop and was pleased) but after experiencing such shortcomings and pretty much killing my enthusiasm i must rethink my decision. And i have to stop promoting ubuntu among my computer illiterate friends, if their boxes will get fked up there would be no hope for them to restore :[

some pieces of my gear: amd64 3000+, mobo ga-k8nf9 (nF4), 512bm ram, gf6200, 2 sata drives (seagate x2)

---

