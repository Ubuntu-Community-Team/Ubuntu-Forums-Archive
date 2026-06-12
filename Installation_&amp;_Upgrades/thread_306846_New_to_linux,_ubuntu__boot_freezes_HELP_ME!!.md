---
title: "New to linux, ubuntu  boot freezes HELP ME!!"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by k6kid on 2006-11-25
Quick and down to the point,
Installed ubuntu on spair 80 gig hard drive used alternate setup cd with text based install.
Everything went flawless! Except when i try to boot ubuntu i get to the screen with the logo, and the status bar, well the status bar gets almost all the way done with like 1/2 bar to go, then logo gets dis-colored, and I get some blue junk at the top of my screen, and on the sides of the status bar.

I have run "sudo dpkg-reconfigure xserver-xorg"  and run through many different settings with my video card and such, still the same problem, i "think" its a video problem?!

Specs.
Custom built 
AMD 3500+ skt. 939.
1gig gskill ram
200gb main hdd
80gb "linux" drive
ATI Radeion x700pro 128mb graphix card
sony dvd-rw drive
generic cd-rw drive
 
Have tried to remove tv tuner etc. in my pci slots but still haveing same lock up problem

---

### Post by aidanr on 2006-11-25
when grub is loading hit escape and edit the boot command and remove the "splash" and "quiet" options, see if you can see if it spits out any errors. i've noticed quite a few threads with the amd 64 and your symptoms, you may want to also want to have a search around [here]("http://ubuntuforums.org/forumdisplay.php?f=134") to see if theres any fixes

---

### Post by k6kid on 2006-11-25
sorry, the release is a  32bit version, NOT the 64bit release.
How do i enable silent boot, from start up when "grub" boot manager starts is a few seconds, do i press escape then? before the boot manager starts?? or after when i select ubuntu to load and ubuntu is loading?
Sorry i am Very new to linux.!  -Thanks!

---

### Post by aidanr on 2006-11-25
when grub loads (you may have to hit escape for a list of your installs) press 'e' to edit the command grub uses to boot ubuntu, then on the second line remove the words quiet and splash and then hit enter and then 'b' to boot, this removes the splash screen temporarily so you can see whats happening and see if theres any error messages

---

