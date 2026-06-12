---
title: "Edubuntu CD won't install..."
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by whitecrow on 2006-07-22
I have this nagging feeling that I'm doing something wrong.  I have installed many flavors of Linux, including th past two versions of Ubuntu.  My installation of Dapper went fine today and I am so pleased.  But, I also ordered a Edubuntu CD for my kid's computer.    I first tried to install it on her computer, which has an AMD board and an amount of RAM that meets all the specifications on the Edubuntu CD sleeve. The CD booted the system and gave me the option to install.  I had read the instructions and chose the workstation option because I want a standalone machine.  No problems specifying  my location or the type of keyboard I have.  But after this, I get an error saying "The CD ROM drive contains a CD that cannot be used for installation.  Insert a suitable installation CD."  

My first thought was that the CD was somehow bad.  I ran an integrity check and the CD tested good.  I checked the files on the CD with the downloadable ISO files:  Everything's the same.  I moved the hard drive on which I want to install the OS to a box with an Intel board that met the specifications.  Same problem.  Is there a trick to this or is my CD bad despite the "good" test?  

Any answers appreciated.  I don't want to order a new CD unless that's indicated.  It costs money to ship and takes weeks to get here.  I cannot download an ISO; no high speed connection way out here in the country...

Whitecrow

---

### Post by greenstar on 2006-07-23
Yeah, I have an idea. Choose 1a or 1b as starting point, depending on your situation, then do the rest for either way.

**1a.** Do a server install and then do:

```
sudo nano /etc/apt/sources.list
``` 
and add the following lines

```
# Edubuntu CD-ROM
deb cdrom:[Edubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
``` 
[B]
OR
[/B] 
**1b.** Do a regular install, then do:

System->Administration->Synaptic Package Manager
then, with the Edubuntu CD in your CD-ROM drive, Settings-.Repositories->Add Cdrom

**2.** then do:

```
sudo apt-get update
sudo apt-get install edubuntu-desktop
sudo apt-get install edubuntu-artwork
sudo apt-get install edubuntu-artwork-usplash
sudo apt-get install edubuntu-docs
``` 
**3.** If you want to remove Gnome afterward,
do:

```
sudo apt-get remove ubuntu-desktop
``` 
Hope this helps,
Greenstar

---

### Post by whitecrow on 2006-07-24
Thanks Greenstar...but it looks like both of us were being a little too technical.  I decided to post my resolution of these issues in the event that someone else might have the same problems.  

To test the issues I was experiencing, I ended up installing edubuntu on two machines...both met specs; one has an Intel board and the other has an AMD board.  My eventual problems were as follows...in the computer with the Intel board, install wouldn't begin at all (computer could not recognize the CD ROM to boot from disk).  In the computer with the AMD board, edubuntu installation would begin but would be aborted with the "insert a suitable cd-rom" error.  

Both problematic installs were caused by hardware issues of the type that might cause a Linux newbie to become frustrated and quit.  I am writing here to let others know that Linux is not really that hard and you just need to keep trying.  

With the Intel machine, apparently the cd rom drive (an old, used one) I was using required a start-up driver that Dapper (Edubuntu) wasn't loading or didn't have.  When I noticed that the post saw the drive but did not list it as atapi, I removed and replaced drives (I repair computers and have lots of used parts around) until I got one that read as atapi. Everything worked on the third replacement and I now have an Intel box booting Edubuntu.  

The issue with the AMD box was also a hardware problem.  Maybe I failed to read the instructions properly but I tried to boot and install Dapper from a DVD / CD-ROM, which is the primary removable media drive on the box.  The existing drive is known good but I got the "invalid cd" error repeatedly.  The secondary removable media drive on the box is a plain old atapi CD rewritable drive.  I reset the BIOS to boot from the secondary drive and away we went without a hitch.  

My kid love Dapper Edubuntu already and it is dual booting along-side Windows XP with no problem.  

The moral of this story is....keep trying...it's probably not Linux.  LOL.

Whitecrow:mrgreen:

---

### Post by greenstar on 2006-07-25
Good work, whitecrow. That's what makes the Ubuntu community so great. There's always someone willing & able to see the problem from another angle.

You're right, this probably would've been a showstopper for most linux noobs. 

Maybe this should be added into the install docs as a note on troubleshooting problems with installation.

Greenstar

---

