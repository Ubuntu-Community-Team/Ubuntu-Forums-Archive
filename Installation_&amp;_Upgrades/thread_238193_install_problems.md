---
title: "install problems"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by arkface on 2006-08-17
hey,

i burned ubuntu on to a disc and everything. so now im installing it fully on to my other computer, but when i get to the 24%, it just sits there for hours and hours. ive restarted the installation process 5 times already. the last time i just left my comptuer on all night hoping that it was just the ways things are with the installation process. but, alas, it didnt work. it's been at 24% for at least 12 hours. when it gets to 24%, it says: Copying files (9:12 [which is assume is the amount of time it takes]).

im running  on an hp pavilion dv4000 laptop.

---

### Post by ewaguespack on 2006-08-17
it shouldn't take anywhere near that long, I would try the following:

-verify the md5sum of the iso you downloaded, consider reburning the iso

-try adding "pci=noacpi" as a kernel argument during installation

---

### Post by babyfox on 2006-08-17
I am having the same problem except at a different point.  On page 2 of the setup where you select a city, the computer just freezes.  I am running a Dell Deminsion 2350 with no current operating system.

Any help would be appreciated.

---

### Post by wheels5894 on 2006-08-17
Yes, and I have the same problem. It gets to 56% and then dies, usually with 2min o3 sces to go. Tried all the obvious included checking the ISO and reburning. Anyone any ideas please?

---

### Post by arkface on 2006-08-17
bump

---

### Post by unisol on 2006-08-18
how about trying the alternate-install cd it installs in textmode and is a more stable installer

---

### Post by wheels5894 on 2006-08-18
Just downloading the alternative version so I'll see how that works. I have already moved the mouse and keyboard away from the USB ports as it seems some  installs have problems with them.

I'll report back later when I've tried this new instal disk.

---

### Post by carontis on 2006-08-18
I think you all should check for your cpu in relation to the distro; you can find different Ubuntu's distros and everyone good for you cpu. Remember also when you boot the 1st time, to use those buttons shown, where you can instantly decide your language, keyboard and VGA (usually VGA is better leaving it at 800x600 @16). Finally you can start to install simply pressing Enter. If you don't have DHCP active on your modem or router, take out the cable and do the settings for your line only after. Sometime the installer checks for a line, but it's getting to much time and almost always it returns a message error (like can't find the line). This is what I found during all installations I did.

---

