---
title: "Dang, blew it all away. but how?"
date: 2018-11-20
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2018-11-20
so this was weird
I have finally succeeded (it seemed) in dual installing 18.04 UEFI with Windows 7.
Yesterday I was happily working away.
but this morning I rebooted and ....nada. No Bootable Devices. No windows, no Ubuntu.
But before I shutdown I installed and ran Gparted (because I had mislocated /home in that install and wanted to see what the partition structure looked like) and instead of several partitions (75Gb for windows, 30gb for Ubuntu, 140GB for data) the entire 250gb was showing "Unallocated"

what happened? 
I don't expect that running Gparted would have affected anything.

the only other move I'd made yesterday was to use Gdisk to "recover" from an apparent GPT error. I used.... I forget which command. e? to rebuild the backup GPT from the primary.
might that bave blown things away?

I guess I am back to Square 1. reinstalling Windows and then reinstalling 18.04

given I had those GPT errors when I did Verify with Gdisk, are there any steps I should take to really verify my HDD before I start again?

---

### Post by ajgreeny on 2018-11-20
It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help us figure out what happened and whether or not your gdisk commands caused any deletion of partitions.

---

### Post by pjstock on 2018-11-20
Here's the result from Book-Repair summary.

[http://paste.ubuntu.com/p/sxv4GMKC7d/](http://paste.ubuntu.com/p/sxv4GMKC7d/)

---

### Post by ajgreeny on 2018-11-20
Regrettably that boot-info output does not help me a great deal apart from showing that there are no partitions on your hard disk, hence no OS to boot to.
What I can not say is what you did that may have caused this to occur but I do wonder if your use of gdisk may be behind this, though with no info on the command you ran it is very difficult to tell you more.

Should you choose to reinstall both OSs remember that [COLOR="#FF0000"]**they must both either use MBR/BIOS or both use UEFI, not one of each.**[/COLOR]
Windows 7 was probably originally installed (if preinstalled by seller) using MBR/BIOS but as you say there were GPT errors I wonder if you installed Ubuntu using UEFI on a GPT formatted system.

Wait to see if others more knowledgable that I appear and can give you more details of the problem shown in the boot-info output.

---

### Post by pjstock on 2018-11-22
OK, I gave up and just went with complete reinstalls. But I am still having trouble.
Windows 7 reinstall easily.
then I reinstalled Ubuntu 18.04, with / on a 30gb partition and /home on a seperate 130gb partition.
both appear to be Legacy installs.
However, on reboot I do not get the menu where Ubuntu is the default and there is an option of Windows 7. It just boots straight into Windows 7.
I thought I must have messed up the install (as I choose Something Else even though the first line was "Install alongside Windows 7?" and so I started to re-reinstall Ubuntu.
but at the Installation type Page it is showing me "this computer currently has Windows 7 and Ubuntu 18.04 installed. what would you like to do?"

I think this is basically a New Topic so I am going to post it as a new topic.

---

