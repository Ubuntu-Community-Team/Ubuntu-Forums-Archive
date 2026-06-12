---
title: "Ubuntu stuck after /dev/… clean, …/… files, …/… blocks"
date: 2023-10-13
forum: Installation &amp; Upgrades
---

### Post by schmoas on 2023-10-13
Hello,

Yesterday I tried everything to get ubuntu working on my machine. I first created a bootable drive with balena etcher on my mac. This worked perfectly when i installed ubuntu server on another machine a few months prior Note: I did get to the screen where i can select try ubuntu and all of this stuff. Before i got to that screen something about error /boot/ flashed for a split second and after selecting, it either got stuck on the cursor or i got a blackscreen. I then created a new bootstick with rufus which eliminated the cant find /boot/ error and went on. I got the same blackscreen. I then tried to launch the install with safe graphics which worked but after it finished installing and had to reboot it got stuck on /dev/nvme1n1p1: clean, …/… files, …/… blocks. I tried to chroot from my live linux stick and uninstall all nvidia drivers which had been suggested in a different thread but didnt work. I also tried getting into grub but when i hold esc + shift it instantly switches to grub console where i have no idea what to do. Also note that i am new to ubuntu and i have never done debugging at this level so please explain in newbie terms.

System:
GPU: rtx3090
CPU: i7 13700k
RAM: 64gb ddr5
MB: Asus Prime Z790-P
Dual Boot OS (was installed before installing linux): Windows 

Note: Linux is installed on a seperate disk not the same as Windows

---

### Post by Rubi1200 on 2023-10-19
Hi and welcome to the forums :-)

I would say, before this gets too messy, please run the system info script and boot info script from my signature. Please do not try to repair anything, just post the results here for analysis.

Hopefully, we can help you get this sorted out.

---

### Post by MAFoElffen on 2023-10-19
Ah... 

He meant: *"Please post the URL's to where they both uploaded their reports to pastebins..."* 

That is a lot easier for all of us, including you.

---

