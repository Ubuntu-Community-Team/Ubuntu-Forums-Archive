---
title: "Natty, grub2 and RAID"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by chitowner2 on 2011-05-11
Hello All,

Last night I attempted an install of natty narwhal, ububntu 11.04, server edition, on a new build and it failed to boot after installation, flagging a problem with grub2 not having been installed.

The mobo is EVGA with an AMD-64 cpu, tho I suspect that is not relevant, since after the usual google search it turns out there are numerous similar instances with assorted hardware. 

[eg see this:  [http://www.google.com/search?hl=en&client=ubuntu&hs=r4j&channel=ks&q=install+grub+natty+raid&aq=f&aqi=&aql=&oq=](http://www.google.com/search?hl=en&client=ubuntu&hs=r4j&channel=ks&q=install+grub+natty+raid&aq=f&aqi=&aql=&oq=)  ] 

In my case there are multiple hard disks formatted as a pair of software RAIDs, a small one in front to use as a boot, and a main one subdivided into LVMs for /sys, /home, etc. Setting up the RAIDs in the natty server installer could have been easier with a bit more detailed narrative in the menus and tabs, but ultimately this post is about grub 2 (eg "grub-pc") not installing.

What I found is that apparently grub did actually install- it simply did not get configured correctly. I know this because after trying to boot the system failed, and getting a 'grub cursor' I tried to apt-get install grub-pc and got the ubiquitous "already newest' reply, so this tells me that the installer did not configure grub correctly. As a result, the system essentially has no boot loader and is effectively "bricked". 

Re-doing the install has been tried by several others in posts on assorted sites. (see URL above). Other threads here have looked at this issue, #1690964 and #1744563 for example, without apparent success.

I am appealing in particular to any of the developers with relevant expertise to look into this issue and please post a response here. Apparently something is in the works [[https://launchpad.net/ubuntu/natty/+source/grub-installer/+changelog]](https://launchpad.net/ubuntu/natty/+source/grub-installer/+changelog]) but has not been completed.

I welcome any replies. This seems to be a major whoopsie in the ubuntu saga. IF ANYONE HAS A FIX FOR THIS PLEASE POST!!

Regards,
CT
:confused:

---

### Post by MAFoElffen on 2011-05-11
> **chitowner2 said:**
> Hello All,

Last night I attempted an install of natty narwhal, ububntu 11.04, server edition, on a new build and it failed to boot after installation, flagging a problem with grub2 not having been installed.

The mobo is EVGA with an AMD-64 cpu, tho I suspect that is not relevant, since after the usual google search it turns out there are numerous similar instances with assorted hardware. 

[eg see this:  [http://www.google.com/search?hl=en&client=ubuntu&hs=r4j&channel=ks&q=install+grub+natty+raid&aq=f&aqi=&aql=&oq=](http://www.google.com/search?hl=en&client=ubuntu&hs=r4j&channel=ks&q=install+grub+natty+raid&aq=f&aqi=&aql=&oq=)  ] 

In my case there are multiple hard disks formatted as a pair of software RAIDs, a small one in front to use as a boot, and a main one subdivided into LVMs for /sys, /home, etc. Setting up the RAIDs in the natty server installer could have been easier with a bit more detailed narrative in the menus and tabs, but ultimately this post is about grub 2 (eg "grub-pc") not installing.

What I found is that apparently grub did actually install- it simply did not get configured correctly. I know this because after trying to boot the system failed, and getting a 'grub cursor' I tried to apt-get install grub-pc and got the ubiquitous "already newest' reply, so this tells me that the installer did not configure grub correctly. As a result, the system essentially has no boot loader and is effectively "bricked". 

Re-doing the install has been tried by several others in posts on assorted sites. (see URL above). Other threads here have looked at this issue, #1690964 and #1744563 for example, without apparent success.

I am appealing in particular to any of the developers with relevant expertise to look into this issue and please post a response here. Apparently something is in the works [[https://launchpad.net/ubuntu/natty/+source/grub-installer/+changelog]](https://launchpad.net/ubuntu/natty/+source/grub-installer/+changelog]) but has not been completed.

I welcome any replies. This seems to be a major whoopsie in the ubuntu saga. IF ANYONE HAS A FIX FOR THIS PLEASE POST!!

Regards,
CT
:confused:
I am not a connected with Conical or Ubuntu, except as a "User"  I do have a server that I'm testing right now with concurrent internal PATA and SATA RAID arrays... and an external 15 drive SCSI RAID array.  I may or may not be able to help you, but Your post was unanswered and I didn't want it to get "lost" or be unanswered.

From what you said, you are doing fake-raid using dmraid and lvm(?) with a non-raid boot partion/drive(?) and Grub didn't install?  That seems pretty straight forward.

Please post the results of the bootdisk script in my sig.  That would give people here an idea how you are set up and if grub installed or not.

Yes, grub has to boot, find and read the kernel boot files and your logical volume manager.

---

### Post by chitowner2 on 2011-05-11
> **MAFoElffen said:**
> 
From what you said, you are doing fake-raid using dmraid and lvm(?) with a non-raid boot partion/drive(?) and Grub didn't install?  That seems pretty straight forward.

Please post the results of the bootdisk script in my sig.  That would give people here an idea how you are set up and if grub installed or not.

Yes, grub has to boot, find and read the kernel boot files and your logical volume manager.


All partitions are raided, including /boot. Boot is in a 6-part raid1, nominal size is ~4.5G. The other is a raid5. Used software raid, not 'fake-raid'.

Grub did install, just not correctly. I verified this by trying to "apt-get install grub-pc", and got back 'already newest'. 

Since I can not get ssh to work, I am at a loss as to how to load your bootdisk script on the server. Trying to run ssh returns a "socket" error; can't connect to /com/ubuntu/upstart, whatever that is.

CT
still :confused:

---

### Post by chitowner2 on 2011-05-12
UPDATE

Well, not a solution per se, but a resolution any way.

Turns out that somehow, easily including my misconception of the partitioning editor, caused the raid to be established on incorrect partitions.

I did have mucho grande trouble with the partition editing. All I wanted was two primary partitions, duplicated, on each of six disks. 3 were transplanted from another machine and 3 were new bought. The natty partition editor kept giving me grief. every time i did partitioning on one disk, partitioning on another disk would seemingly revert in the gui editor.

I used fdisk -l to check, and it showed the partitioning I wanted, but in the gui editor it kept changing. I rebooted the installer, got back to the partitioning menu, and re-partitioned each drive, rebooting after each disk, until the gui stopped showing changes. Then I finished the install after once again verifying with fdisk that it all looked good. 

It wasn't. Somehow I ended up with natty thinking there were two discrete raids of 6 elements each, but what I discovered later, is that two of the disks didn't partition at all. Both of those conditions existed _simultaneously_, so apparently grub could not decipher where the /boot was, so it hung.

Wound up doing partitioning again, in a shell, after wiping the partitioning that existed, then finishing the install and finally grub did boot.

Maybe someone more knowledgeable than I can grok how a command line view and a gui view of the same hardware kept disagreeing, despite rebooting multiple times. It was a laborious and recursive process, and ultimately it failed and had to be redone. But it's OK now.

CT
:popcorn:

---

