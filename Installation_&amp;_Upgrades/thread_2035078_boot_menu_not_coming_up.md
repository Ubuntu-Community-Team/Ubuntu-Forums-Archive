---
title: "boot menu not coming up"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by aLarM on 2012-07-29
okay guys, i just reinstalled ubuntu, while already having windows 7 installed, everything went smooth this time. but there's one problem, after i restarted the computer for the installation to finish there was no grub boot menu, instead it just went straight to starting up windows 7. grub was installed as during installation in the progress i saw it say something like "update-grub", or something along those lines.
help would be appreciated, if you need any info from terminal let me know and i will hop on the live cd.

---

### Post by oldfred on 2012-07-29
Post the link that the BootInfo report creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by johnnycatt on 2012-07-31
oldfred,
I had the same problem as described above.

I opened Boot-repair by using the liveCD.  This didn't seem to work. I still just go straight to windows7.

I have run "sudo fdisk-l" and it shows both Windows and linux on the harddrive (Linux is sd6 and sda7, I think sda6 is my root -- it is the larger file).

it is a 320GB harddrive and I partitioned it roughly 50% for windows and 50% for Linux.  When I look at the hardrive via Windows7, it only shows the "half" that is windows and nothing else.  It only shows that I have a 148GB harddrive (not the 320GB that is actually there - I'm sure this has to do with the partition)

I'm not even sure where to go from here.  I did read something on here about "mounting" /sda6, but that little process didn't work out, but I can't find the thread I was reading when I tried it. 

Windows works fine.  Linux is there, but i don't know how to access it.

---

### Post by Dawnbandit on 2012-07-31
You might need to manually edit the grub file with gedit, make sure you run it as root. ```
Sudo gedit
``` And if I read correctly it said "Update Grub" you should check if you have the latest version installed.

---

### Post by oldfred on 2012-07-31
@johnnycatt
Best to start own thread, trying to fix similar but usually different configurations in one thread often leads to confusion.
Boot repair should give you the option to install grub2 boot loader to the MBR if you have a good install in the Linux partition. If not perhaps advanced options or then you have to post link to BootInfo for us to analyze issues. If that is needed post in a new thread.

@aLarM
If Boot_repair does not solve issue, then post link to BootInfo.

---

