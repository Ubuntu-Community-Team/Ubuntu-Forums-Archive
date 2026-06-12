---
title: "Wireless problems"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by grandpa1 on 2011-01-27
I listed title as wireless problems, but it is more than that. 
1. I need to move? a file (not a folder) from a cd to the proper folder in the File System. 
2. The file I need to move is an unzipped driver for my wireless adapter (Rosewill rnx-n150ube, a linux driver) to the proper folder in the File System...which folder?

3. I want the linux system to search --->System/Administration/Additional Drivers and find  my linux driver to activate. I understand that I must first Mount the file into the MNT folder in the File System. I have not found a combination of commands to enter into the Terminal to accomplish this. 

I am running Ubuntu 10.10 downloaded direct from Ubuntu.  Machine is an HP laptop zv6000.

Any help would be greatly appreciated..

---

### Post by gordintoronto on 2011-01-27
If you run Accessories/Terminal and enter this command:
lspci | grep 802
it will show you the real identity of the wireless adapter -- unless it is an USB unit, in which case you would use the command lsusb.

(Rosewill is Newegg's house brand, and it may well contain the chipset of the day. The chipset is what is important to getting it working.)

Is it at all possible that you could run for a few minutes with a wired connection to your router? Then you could run Additional Drivers.

---

### Post by grandpa1 on 2011-01-27
Thanks for your response. Here is what I get when I enter:

lsusb |  grep 802

Bus 001 Device 005:  ID 0bda: 8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

The file I am trying to get from my cd to the proper folder in the File System is on the cd, which is a linux driver from Rosewill.

So, at this point I have been able via mkdir to get a new empty folder in MNT, and my problem is to determine the  proper commands to mount this cd file into the MNT folder. After that is another problem that I can address later. Thanks again

---

### Post by grandpa1 on 2011-01-27
I think I have solved the first part of my problem, so I am going to call this  Post as Solved. I typed the following into my Terminal

sudo mount/dev/cdrom  /mnt

---

### Post by gordintoronto on 2011-01-27
It ain't solved until the wireless works!  [smile]

What file are you trying to cp from the CD?

When I Google RTL8188SU ubuntu I get quite a few responses, many of them too old to be relevant. It appears that support for the device will be built-in with Ubuntu 11.04, but that is not a stable system yet.

---

