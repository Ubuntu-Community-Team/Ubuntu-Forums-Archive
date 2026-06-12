---
title: "Disk partitioning odities ?"
date: 2018-06-26
forum: Installation &amp; Upgrades
---

### Post by aaltom on 2018-06-26
Hi all,
just started ubu 18 srv. for a first test.
I came all the way until disk setup start...
Then all logic got lost, when it offers me my ent. disk 500G and offcourse manually, but also my ent. disk 500G !?
The manual way again just gives me an option of 500G+1M, and looks that it wants to destroy all the rest of my data !??!?! NOT ACCEPTABLE !:(
I really have 4 part. in use and ONLY one reserved for ubu-testing. SDA1+2+3+4 (230G+90G+120G+20G swap +some free).

How can I do some REAL manual and controlled partitioning + install, without losing any data ?


br. Mike

---

### Post by uRock on 2018-06-26
Hello and welcome to the forums,

Can you tell us more about the system you are installing on?

Also see [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by yancek on 2018-06-26
If you only see the option to use the entire disk, I suspect you have windows 8/10 installed and left fastboot and hibernation on in windows.  No Linux system will mount a hibernated disk partition as it is too likely to damage files.  Turn them off and try again and if you still have problems, post back with details such as drive/partition/filesystem type info.

---

### Post by oldfred on 2018-06-26
If using MBR(msdos), you can only have 4 primary partitions.
I converted to gpt to eliminate that 35 year old issue in 2010.
But normally you use 1 primary partition as the extended partition and then can have as many logical partitions as you want.
You have to backup, delete one partition, make it the extended partition & create new partition(s). You can then restore data from the one you deleted.

You may be able to use fixparts to directly convert one partition to logical. But you still have to resize and expand extended to be able to make more logical partitions.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/) 
    
Or you can convert to gpt, but need good backups. It normally works, but if you do not have good backups, you will be the exception where it does not work.

If BIOS boot will need a bios_grub partition and reinstall grub.
       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by aaltom on 2018-06-27
Hi all,
and thanx for all replies.

I found out the problem I had:
The ubu-download page had 2 versions of the install image:
-First that came up is the od one (ubuntu-18.04-live-server-amd64.iso), this is some kind of a new beta-test-install script ?
[http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso.torrent](http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso.torrent)

-The second one is "normal" one (ubuntu-18.04-server-amd64.iso), this is the classic debian-like install-script. For this image you have to do a lot of clicks... SO WELL HIDDEN.
[http://cdimage.ubuntu.com/releases/18.04/release/ubuntu-18.04-server-amd64.iso.torrent](http://cdimage.ubuntu.com/releases/18.04/release/ubuntu-18.04-server-amd64.iso.torrent)

No logic here either ?
A server install with an un-controlled image, who would wnat that ? And also you have to scroll down the page for "Alternative Ubuntu Server installer", as I said well hidden link.
Shouldn't the std-image be first, and also shouldn't there be a WARNING that this is a "beta"-whatever test-image ?

Don't really know where ubu is trying to go, now I just struggled through the netplan-space-indent-hell, very, very frustrating...space-counting-1-2-3... Doesn't look too positive anymore.
I started out with slackware back in 1995, went to debian 2004, stared my first ubuntu 2008, which looked and felt quite good, but now what ?

Sorry about my annoyances...


br. Mike

---

### Post by uRock on 2018-06-27
I'm sorry to hear you had such a hard time with the live server install image. I just clicked through it and it seemed pretty intuitive. I didn't see it as being in beta, nor did I see it as being uncontrolable.

---

### Post by aaltom on 2018-06-28
Well I'm very sorry too... and offcourse very dissapointed.

Other stuff also came up on the new 18 release, such as usb-drives stay in the system even if I physically remove them !? Kernel problem ?
Anyway I'll keep on trying/testing it out for max. one day, then I'll revert back to 16, which was all ok.

-> Too much "new inventions" in this release ! 
Still the server release is supposed to be run as servers, and this experimental stuff is NOT good for them.

---

