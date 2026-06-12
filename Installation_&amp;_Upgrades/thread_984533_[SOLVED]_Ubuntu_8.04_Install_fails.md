---
title: "[SOLVED] Ubuntu 8.04 Install fails"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by CX15 on 2008-11-16
Hi everyone

I have taken the plunge and decided to switch to Linux - for reasons you all probably understand.

Ubuntu 8.10 installs with no problems but for reasons not pertaining to this thread, I DO NOT want Ubuntu 8.10

So now I am trying to install Ubuntu 8.04.

This is not working though.
I boot from the 8.04 CD and get to the "Prepare Partitions" screen during setup. There are no options available on this screen.
(see pictures below)

Could someone please help.

I knew the transition would not be easy, so I will keep trying.

Thanx in advance
CX

EDIT: Im installin the 64K version of 8.04 because of RAM requirements.

---

### Post by Partyboi2 on 2008-11-16
Did you check the cd for defects before trying to install? Can you also post your system specs please.

---

### Post by CX15 on 2008-11-17
Hi again

1. CD checked for defects - no problems.

2. System: Core2Duo 8500, 4GB RAM, 500GB SATAII HDD
           MB: Asus P5QL PRO, Nvidia GT9800.

---

### Post by CX15 on 2008-11-17
UPDATE:

Tried a few more installs of Ubuntu 8.04. No luck.

In a moment of desperation fooled around with :-#freespire:-#...
What happened next is probably not applicable to either this thread or forum, so lets just say "it didn't work"...

Then I deleted all partitions from the hard drive with fdisk from an XP CD.

Tried installing Ubuntu 8.04 again - same problem.

Then left with unusable disk and no internet (If I boot from the CD I have no internet conection).
I then re-installed Ubuntu 8.10 (which installs flawlessly) but now I'm back to square one again :confused:

Could really use some help, or at least some encouragment :(

Thanx guys

---

### Post by ramaswamyps on 2008-11-17
what exactly is your problem?
are you able to partition and the install starts installing?
did it say it is going to format the following partitions?
asked for your name and passwd?
if you ask more questions i will try to answer them
that way it can help.
what kind of internet connection you have?
dhcp will work automatically.
when it works note your default gateway and you can later put it in /etc/resolv.conf  as nameserver xxxx.xxxx.x.x

then it should work

give more details of problems.

---

### Post by CX15 on 2008-11-17
I apologize, but Im not very familiar with Ubuntu, so my answers might sound a bit novice.

Here is what happens.

1. I put the Ubuntu 8.04 CD in and boot the PC.
2. I choose "Install Ubuntu"
3. I choose language, country and then keyboard layout.
4. Then this screen appears:

[IMG]http://i386.photobucket.com/albums/oo307/ap_dutoit/IMGP3974_rsz.jpg[/IMG]

Not one of the buttons is clickable (all greyed out) except "Forward", "Back" and "Cancel"

When I click on Forward, this pops up:

[IMG]http://i386.photobucket.com/albums/oo307/ap_dutoit/IMGP3975_rsz.jpg[/IMG]

The back button does nothing and Quit asks me if I want to quit installation.

-----------

Answers to questions:

what exactly is your problem?  ---  see above. In short: I am unable to install Ubuntu 8.04 64K Edition

are you able to partition and the install starts installing? -- I assume not, as the install never makes it past the partioning screen.

did it say it is going to format the following partitions? -- no

asked for your name and passwd? -- no

what kind of internet connection you have? -- DSL 6MB/s. Wireless router, but hardwired to PC - Onboard LAN.

dhcp will work automatically -- not sure what you mean by this

when it works note your default gateway and you can later put it in /etc/resolv.conf as nameserver xxxx.xxxx.x.x -- no idea what you are refferring to here, sorry :(


Thanx a bunch in advance

---

### Post by ramaswamyps on 2008-11-17
mmm seems your hard disk is not found by ubuntu

you can try to boot into gnome desktop [the first option try ubuntu]

open a terminal and type sudo cfdisk
it should show you a partition table and details.
if your comp has more than one hard disk 
sudo cfdisk /dev/sda

if the hard disk is found it will show you details.
here you can do partition and type of format.

what computer hardware details you can provide?
like processor,mem, hdd type etc.

if it shows cfdisk details then you can install with install button.

the picture you have shown is not showing the left hand side of the screen.

it is same as that of 8.10 will show selectable harddisk 
manual automatic etc.

try it will work.

the first option boot to gnome will get network connected.

dhcp means your ip address is automatically obtained.

in windows how did you connect? you have static ip and dns address given ?

---

### Post by CX15 on 2008-11-17
> mmm seems your hard disk is not found by ubuntu

you can try to boot into gnome desktop [the first option try ubuntu]

NOTE: I have a working copy of Ubuntu 8.10 installed on my hardrive. There is no problem with the 8.10 install, only 8.04.

Anyway, So I boot from the CD then select the first option: "Try Ubuntu".

> open a terminal and type sudo cfdisk
it should show you a partition table and details.
if your comp has more than one hard disk
sudo cfdisk /dev/sda

When I type [sudo cfdisk] I get a grey window with 

  FATAL ERROR: Cannot open disk drive - Press any key..."

I only have one disk.

> what computer hardware details you can provide?
like processor,mem, hdd type etc.


CPU: Intel Core2Duo 8500
MB: Asus P5QL PRO
RAM: 2 x 2GB 800MHz DDR2
Graphics: Gigabyte NVidia 9800GT
HDD: Seagate 7200.11 SATA II 500GB
LAN & Sound: Onboard

> if it shows cfdisk details then you can install with install button.


Nope - Install button comes up with same problem.

> the picture you have shown is not showing the left hand side of the screen.

I dont see anything else to the left - anyhow here is "FULL" screenshots again - this time I ran install from the "Install Button".

[IMG]http://i386.photobucket.com/albums/oo307/ap_dutoit/IMGP3980_rsz.jpg[/IMG]

[IMG]http://i386.photobucket.com/albums/oo307/ap_dutoit/IMGP3979_rsz.jpg[/IMG]


> it is same as that of 8.10 will show selectable harddisk
manual automatic etc.

try it will work.

I dont see any selectable harddisk as when I install 8.10

> the first option boot to gnome will get network connected.

No network connection when I boot from CD at all :confused:

> dhcp means your ip address is automatically obtained.

in windows how did you connect? you have static ip and dns address given ?

IP and DNS were all automatically selected.


Hope all this helps!!

---

### Post by gjoellee on 2008-11-17
You managed to install Kubuntu!? Then go to the terminal and add this line:
```
sudo apt-get install ubuntu-desktop
```
when you get the option choose, either KDM or GDM if you are on Kubuntu 8.10 if you are on Kubutnu 8.04 choose KDM to avoid many known bugs that might appear.

When the installation is finished log out and in the login window click on "Sessions" and then click on GNOME then login in. You are on Ubuntu with all the KDE applications as well!

---

### Post by CX15 on 2008-11-17
> **gjoellee said:**
> You managed to install Kubuntu!? Then go to the terminal and add this line:
```
sudo apt-get install ubuntu-desktop
```
when you get the option choose, either KDM or GDM if you are on Kubuntu 8.10 if you are on Kubutnu 8.04 choose KDM to avoid many known bugs that might appear.

When the installation is finished log out and in the login window click on "Sessions" and then click on GNOME then login in. You are on Ubuntu with all the KDE applications as well!

Currently Ubuntu 8.10 is installed.
I guess I can re-install Kubuntu 8.10 again.

However, if I follow your instructions above, what exactly will be installed - Ubuntu 8.04 or Ubuntu 8.10?

What I need is just a clean fresh install of Ubuntu 8.04.

Regards
CX

---

### Post by CX15 on 2008-11-17
.

---

### Post by CX15 on 2008-11-17
EDIT: For reasons of clarity I have sanitised some of my previous posts in this thread in an attempt to clarify my problem a bit more.

Essentially, I am still unable to install Ubuntu 8.04.

---

### Post by Partyboi2 on 2008-11-17
Have you tried entering your bios and changing sata to AHCI mode. Another thing maybe to try is to  make sure that your hard drive is unmounted first before running the  installer. By going to Places>Computer and right clicking on the hard drive and unmount it.

---

### Post by CX15 on 2008-11-17
> **Partyboi2 said:**
> Have you tried entering your bios and changing sata to AHCI mode...

SOLVED!!:)

Thanks Partyboi:KS

(What's the difference?)

---

### Post by Partyboi2 on 2008-11-17
[http://www.dailygeeks.com/howto/sata-ahci-mode-bios-setting.-what-does-it-do/](http://www.dailygeeks.com/howto/sata-ahci-mode-bios-setting.-what-does-it-do/)

---

