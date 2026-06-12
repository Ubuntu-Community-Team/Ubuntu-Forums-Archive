---
title: "Finding and mounting disks?"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by Freddy on 2006-07-16
Hi all, I'm a previous longtime user of Kubuntu but for the last half year, I've been scouting distros but now I'm back :-).

When I booted up the new Dapper Drake for the first time, it booted fine and I started the new installation routine. All this just went like a clockwork but now to my little problem. 

I use 3 diffrent harddrives in this computer and several partitions on them but this new installation system only will use my hde1/2 which I don't, I tried to change harddrive but how, the dropdown menu only shows my hde. Can someone pls either help me on how to use all 3 disks or even better tell me how I can go back to use the former method of installation.

Thanks /// Freddan

---

### Post by Choad on 2006-07-16
in ubuntu it would be system>administration>disks

but not too sure in kubuntu.

you can always have a look at /etc/fstab and check it over yourself!

---

### Post by Freddy on 2006-07-16
Nah that was not what I meant.

If I haven't downloaded the wrong CD, the installation of Dapper is done from within the Live CD and the new installer is a graphical one, my problem is using all disk for diffrent partitions in the install.

The partition table I want is. 

HDA (1) NTFS windows (2) NTFS Windows (3) boot (4) swap
HDB (1) / (2) /home (3) fat32
HDE (1) NTFS

The graphical partitions handler finds all of my disks and partitions but when choosing to configure them manually, it will only let me to configure HDE, and not my other two disks. I'm in dire need of help or atleast be able to work with the old installer, which I understood and knew :).   /// Freddan

---

### Post by Choad on 2006-07-16
oh i found custom partition a little counter intuitive in the graphical installer too.

you might be doing what i did...

the first screen you see is a partition magic-like partition editor...

just press next on that and it will give you a list of all your partitions and how you want to mount them.

obviously you could already have done that, but its worth mentioning!

if not, all i can suggest is that you use the alternate install cd (which is the classic debian installer)

---

### Post by Freddy on 2006-07-16
Ahh thx man, I'll go for the alternative :-). Didn't know that existed such a thing. The Debian way allways works ;-).   /// Freddan

---

### Post by MarsmanA on 2007-12-28
HI!
I have some problems mounting disks. First, I don't find system>administration>disks on my ubuntu 7.10. How can I access mounting and partitioning then? And maybe if someone knows: Is there some problem finding partitions when you use some virtual machine (I use Virtualbox). 

Thanx.

---

