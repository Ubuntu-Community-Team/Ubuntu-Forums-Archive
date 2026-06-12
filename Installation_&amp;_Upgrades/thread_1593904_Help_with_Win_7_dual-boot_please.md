---
title: "Help with Win 7 dual-boot please"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by I'm A Robot. Beep on 2010-10-11
Hi all,
I'm a bit of a linux noob im afraid!
Could some body help me with the install process? I've read so many different things today that im getting confused.

I have 2 HDDs. 
The first has Win7 installed on a ~450Gb partition. and i've made a 30GB "Unallocated" partition that i want to use for Ubuntu. 
The second HDD is for storage.

Does this look ok so far? 
I have read some where about "swap" partitions but i'm unsure if i need to create this first or during the install? (or if it is even necessary with 8Gb of RAM?)

Ok, so I boot Ubuntu from the DVD. 
Choose "Try Ububtu" or what ever it says.
Run the installer.
Choose "Install alongside other OS"
Next screen is "Allocate drive space" but my Unallocated partition doesn't show; Ubuntu wants to steal some of Windows' partition.
I click on "1 smaller partition is hidden, use the advanced partitioning tool" and this is where i get REALLY confused.

[Screenshot1.png]

I guess the "free space" is my unallocated partition so i select it and click "Add"? 
Which gives me... 

[Screenshot2.png]

So. do I choose "Primary" or "Logical", "Beginning" or "End", "Ext4 journaling" or "Ext2" and What is the "Mount point"?

Or should I forget about all this and go back to the start?

Sorry for the mass amount of questions. :confused:

---

### Post by Mark Phelps on 2010-10-12
Actually, having used a multi-drive setup for years now, I would recommend a different approach ... each drive with its own OS.

To do that, you would do the following:
1) Disconnect the current OS drive, leaving only the data drive connected
2) Boot from Ubuntu CD in LiveCD mode, use Partition Editor to shrink the current partition to the right to make room for Ubuntu.
3) Install Ubuntu to the drive -- now that there is room
4) Reboot with only the Ubuntu drive connected, to ensure that Ubuntu boots and starts OK.
5) Reconnect the other drive, but continue to boot from the Ubuntu drive
6) Start Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB menu and SHOULD add an entry for your other OS.
7) Reboot the machine

You should then see a GRUB menu.

The advantages of this approach are the following:
1) Each drive is independently bootable
2) Each drive has an MBR consistent with the OS on that drive4
3) Repairing the boot loader, or OS, on either drive runs no risk of damaging or corrupting the MBR, boot loader, or OS on the other drive.

---

### Post by I'm A Robot. Beep on 2010-10-12
Thanks for the reply. 
I muddled my way through in the end and all is well. So far anyway.
Cheers

---

