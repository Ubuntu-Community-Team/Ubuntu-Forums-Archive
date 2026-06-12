---
title: "???How to access files from an old version of Ubuntu, from a USB version of 11.10???"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by awtovey on 2011-11-03
I run a partitioned hard drive with windows and ubuntu. Whilst updating to Ubuntu 11.10, the install was interrupted. This prevented me rebooting into ubuntu, effectively closing access to half my hard drive and the files within. I checked online forums and found a variety of fixes but most were too technical for me to grasp (I have no idea how to work with commands and the terminal). What I did do was create a USB version of Ubuntu 11.10, which has allowed me to boot into a new and rather empty looking desktop.

What I was planning to do was to then access my files stored on the ubuntu side of the hard drive partition and save them to an external drive. Then wipe that half of the drive and install 11.10 from the USB before finally reinstalling all my old files for access through 11.10.

Only problem is, having initially booted into the USB mounted 11.10, I cant access any of my old files. I have found a folder called 'Andrew' (that's me), inside another folder called 'Home'. I cannot access 'Andrew'. I assume this is where my files are. How can I get to them?

Also, is it possible to just install 11.0 (The USB booted desktop has an icon for this) on the main hard drive of my laptop and somehow recover the old files that way? Would going ahead and installing without saving files to an external hard drive somehow damage those files in any way?

Please help. I'm open to any suggestions. However, please keep instructions very simple and avoid ALL jargon. I want to be able to work with linux but I find the tech babble very intimidating and inaccessible. I'll need talking through this.

Cheers,

Andrew

---

### Post by awtovey on 2011-11-03
Please folks.... Someone must have a clue here.

I've spent the last 8 hours trying to work this out, looking through forums, etc. I've tried to access my old ubuntu files from Windows too but that doesnt seem to work - the programs I tried are unintelligible.

Basically at this stage I just want my files back. I cant get them because when Ubuntu was upgrading it was interrupted and got corrupted and now wont boot. Any approach towards fixing the code manually involves direct contextual knowledge that I lack. I'm very happy to just reinstall ubuntu but I dont want to lose my files. As I understand it I can either try to do something through a USB booted version of ubuntu or try to access the files from windows using a specialist program. Both avenues are failing and frustrating me. I need options, advice, anything. Please help!

---

### Post by darkod on 2011-11-03
First, trying to make it work as it is might not be that difficult as it sounds. But since you already said you don't want to do that, lets forget it for the moment.

When you boot into the Live mode with the usb stick, just open your Home folder, the icon with the house. :) Of course, that is not the home folder from the hdd install, that is just empty home folder fron the live mode.

But in the left menu, somewhere around the top, you should see all partition that ubuntu can find, listed. Just click on the partition that is/was your root partition, and it should mount it automatically and open it. You should be able to access the files and copy them where ever you want, even the windows partition. Or another external disk.

---

