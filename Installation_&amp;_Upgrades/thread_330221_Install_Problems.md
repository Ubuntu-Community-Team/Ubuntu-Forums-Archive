---
title: "Install Problems"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by smray on 2007-01-02
When I put the disc in and select install on version 6.06 it gos through the stage of determining drivers and then it loads all the drivers but once this is finished it sits on a black screen with the mouse on it. I've ran out of ideas, the computer which I am trying to install it on, specs are
766mhz intel celeron socket 370 cpu
320mb of Sd ram made up of 2x128mb and 1x64mb sticks
Onboard Video or Asus Agp 3000
4112 mb western digital caviar hard drive
It doesn't matter wether I use onboard or the Agp card, and I've tried with only one stick of 128mb ram.

---

### Post by ingo on 2007-01-04
Have you tried a different installation medium? A faulty cd may be the root of all your troubles. Have you tried knoppix to see whether that can boot your system?

---

### Post by Pobega on 2007-01-04
Some computers just don't want to work with the LiveCD. You should give the alternate install CD a try if that is your problem.

---

### Post by kEinstein on 2007-01-04
Hmm... I once had a similar problem in Fedora 4. You might want to check this out:
1) Insert your CD and turn on the computer
2) go to a command line and type 'fdisk -l'. You will be given a table with info on your hard drive
3) look for the values C 'cylinders' H 'headers and S 'sectors', write them down (or remember)
4) go back to the install-screen, use 'expert mode' and add the following arguments
```
 hda=C,H,S 
```
Replace the C,H,S values with your specifications.
e.g. 'fdisk -l' returns C...7752, H...252, S...63 you are required to use the following argument:
```
 hda=7752,252,63 
```
5) hit enter and watch Ubuntu install on your PC.

In case you are interested, this argument aims at the Cylinder, Header, Sector problem on 'old' PCs as your BIOS might not be able to read the values correctly from the partitition table. By giving these arguments at the install line, you override the information with the appropriate values from 'fdisk'

PS: This problem occured on a HP NX 9010 laptop with 2.66GHz and 40GB HDD in 2003/04 - in combination with Fedora... took me quite a long time to figure out WHAT especially caused the problem. The solution and its application is quite simple though.

Hope this works for you, post your results!

---

### Post by smray on 2007-01-07
thanks guys,

when i boot the live cd from the text interface, with acpi off it seems to work, thanks for your suggestions

---

