---
title: "jockey-gtk deleting ubuntu-desktop &amp; gdm"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by dummy910 on 2011-08-16
This is the most odd Linux happening I've ever run across, in my almost 15 years of using the penguin.    

Loaded jockey-gtk as to install ATI drivers, big mistake! Program detects there is in fact a driver for this system, I clicked the Activate button lower left, a progress meter pops, then...  What's stranger yet, X crashes, screen locks into the middle of a dmesg screen from previous boot. 

Machine not frozen, but gdm and ubuntu-desktop are removed(wiped, deleted, gone!) from the install.   

Luckily Openbox was installed next to ubuntu on this laptop, so I rebooted the machine into that as to troubleshoot and guess what? ubuntu was wiped out although all of the gnome stuff-programs remain in tact, as was openbox. Odd, very odd!  

To bring ubuntu back, booted into a terminal and proceded with the following: sudo apt-get install ubuntu-desktop sudo apt-get install gdm reboot and the machine is back to where it was prior to loading the aforementioned jockey-gtk(as to activate the detected ATI driver) 

Oh yeah, I removed jockey with the following, so this wont happen again. sudo apt-get remove jockey-gtk  Anyone else run into anything like this??

---

