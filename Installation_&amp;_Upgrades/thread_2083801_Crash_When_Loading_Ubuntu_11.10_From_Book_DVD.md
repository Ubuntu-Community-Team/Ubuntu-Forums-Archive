---
title: "Crash When Loading Ubuntu 11.10 From Book DVD"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by SmitherGJ on 2012-11-13
I just bought the book "Ubuntu Unleashed 2012 Edition: Covering 11.10 and 12.04 (7th Edition) " by Matthew Helmke. Included was the DVD with Ubuntu 11.10 onboard.
 
Before we go forward, my system is as follows:
HP Elitebook 8460p Notebook
Intel® Core™ i5-2520M (2.50 GHz, 3 MB L3 cache)
300 Gig HD
4 Gig Memory
2.50 Gig proc. Speed
I have Windows 7 installed on a first 100 Gig partition on the hard-drive. The rest is unallocated.
 
My plan is to install Ubuntu in a following partition of about 100 Gig and let Grub 2 do the work of selecting which one to boot to.
 
The disk comes up OK asking you to select a language (English). Then I can select either of "Try without installing" or "Install on Hard Drive" and it will still quit at about the same place. An Ubuntu symbol comes up on the screen and the little dots mark time as if something is loading for a number of seconds. Then it breaks down and dumps me into an Ash shell with the following error message:
---> Unable to find a meduim contianing a live file system <---
I can navigate around using the Ash Shell with such commands as LS and CD.
 
I had originally tried an minimized system Ubuntu .iso file downloaded from the internet and had the exact same problem.
 
I know that linux can run this machine. I have a Knoppix 7.0 disk that will completely launch the system from the CD tray. I can use this system to get online, manipulate files, and have used GParted to manipulate partitioning.
 
It is possible for me to create the partition I want, following windows, and then copy all the files from the DVD over to the newly created partition. But then I don't know how to make Grub2 load as the boot-loader and point to both of my systems.
 
What should I do? :P Relitive Linux Newbie, Gary

---

### Post by SmitherGJ on 2012-11-14
Here's what went down last night:
 
1.) I was able to partition the Hard Drive using GParted.  I have a regular Windows 7 Partition, then a Linux Root Partition, then a Linux Home Partition, then a Linux Swap partition, the a shared NTFS partition useful for both.
2.) I was able to use the Knoppix 7.0 Live Distro CD to write itself onto my Linux Partition.
3.) Knoppix 7.0 was able to write a boot loader program (Plain Grub I think) into the MBR.
4.) Computer will boot successfully into Win7 or Knoppix using the internal HD alone.
 
I still haven't been able to get Ubuntu 11.10 to boot on this computer.  Any ideas on how to get this accomplished will be appreciated. :)

---

### Post by SmitherGJ on 2012-11-16
Last night I tried to reboot using the DVD live option. I found that by pressing F6 at the menu arrived at, I could reach a single editable line for the launch point. I tried interjecting the 'shift' key during light off but it would never let me come to a grub screen or seem to make any difference at all. 
 
The F6 menu option had several canned choices of which I was able to try only the 'aspc=off' value. This did not allow a successful boot. I edited the launch line down to the first two entries and was able to see the various code as it went through in the launch sequence. It got to one point and repeatedly printed some inturrupt which I can't remember. It was not a successful boot and dumped me out at the aforementioned ash shell. 
 
I'm going to try this weekend to glean some steps to attempt from the 'Sticky Note' in this forum about ver 11.04. I do remember years ago when launching the Knoppix Live CD, I would used to have to set a specific video mode in order for it to launch. I wonder if that is what is going on here? :confused:

---

### Post by SmitherGJ on 2012-11-19
Over the weekend, I was able to download a copy of the Ubuntu 12.10 .iso.  I burned this to a DVD and then launched it from the tray.  It loaded completely giving me the option to install on the HD.  I went forward and had it load itself overtop of my Knoppix Linux Installation that I had already successfully installed on that harddrive.  It asked me about the bootloader which I directed to that drive.  I can now successfully boot either the Windows 7 system or the Ubuntu 12.10 system.  This looks like a really good system and I'm looking forward to getting to know and experimenting with it. [SOLVED]

---

### Post by mlentink on 2012-11-19
Hi SmitherGJ and welcome to the forums (and to the free world!).

You can mark your thread as 'Solved' by selecting that option in the "Thread Tools" at the top of this thread.

---

