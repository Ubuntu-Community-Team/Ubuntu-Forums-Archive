---
title: "Ubuntu hangs in many ways"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by The standard username on 2011-08-23
I have been trying to install ubuntu 11.04 32bit and 10.04 LTS 32bit  on one desktop to no avail.  
it hangs in many ways:

first on 11.04 it hangs after forwarding from keyboard layout screen, it just hangs there. I overcame that hiccup  by installing after choosing try ubuntu from live cd.  on 10.04 it works fine . 

both hangs after installation start specifically at the 15% mark for 10.04.

Gparted hangs if I try to apply any change.   I even tried to do the changes from windows easeus partition manager which worked fine and successfully partitioned using ext3.  

but when trying to install ubuntu reaching gparted, choosing to use the partitions without format , it hangs after clicking forward.

It's old desktop: FMV-CE30E5
AMD® Athlon XP 2400+
Chipset Sis 740
1GB ram
120GB *IDE* Ultra *ATA*/133 HDD (newly installed, the hard disk is fine no bad sector)

Windows XP NTFS installed less than 70GB. 

the scheme I tried for ubuntu is following:
I originally chose ext4 , but when used easeus I chose ext3, because it does not support ex4

500mb ext3/ext4   /boot
 5000mb   swap area 
49xxxmb  ext3/ext4    /

when it hangs, it hangs totally, no mouse can move, no response to keyboard, no ctrl+alt+f1 .   just stays :guitar:

---

### Post by sidzen on 2011-08-23
Your Specs --  (?) --

North Bridge    SiS 740
Socket    Socket A (462)
Processor Types    Athlon, Duron
Number of CPUs    1
Front Side Bus    266/200MHz
Memory Type    DDR, SDRAM
Maximum Memory    1.5GB
Memory Channels    Single
External Graphics    AGP4X
--------------------------
Your machine will not run any 'buntu above 10.04 LTS due to kernel issues and graphics issue

Q:  Why try to run ubuntu on such a limited resource PC?

What is needed is a i486/i586 distro with either the lightest DE or no DE (only a WM).  
Also suggest eliminating XP if a Linux distro is desired. 

If ready to start from the above, say so . . .

---

### Post by The standard username on 2011-08-23
"Your machine will not run any 'buntu above 10.04 LTS due to kernel issues and graphics issue"

thanks for the reply, but why then 10.04 hanging too?    I just want to make use of the pc. it can run windows xp fine. I wanted to add a linux distro and since i use ubuntu on my other pc.  I wanted to try that  . is there a way to install 10.04 LTS ?

beside ubuntu live cd works so poor graphic ability can't be an issue. 

I ll try another distro if I can't get 10.04 LTS to work.

---

### Post by dino99 on 2011-08-23
how i make installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sidzen on 2011-08-23
First do as dino99 suggests.  If this does not work, then come back and we'll go from there.

---

### Post by The standard username on 2011-08-23
I did .  in Gparted as part of ubuntu installation, I removed my old partition that I reserved to  /boot which I made in easeus .  then wanted to resize the partition I  reserved for "/"  . here it says I need to apply the changes before resizing. when I hit forward .  instead of applying the changes. it hangs .  even the mouse indicator hangs.    it seems gparted which ubuntu uses can't do any of the changes.  even gparted live cd couldn't . 

I tried also xubuntu 11.04  same story .  

I think I will try 8.04 and see if it works. or if you have any suggestion . is there diagnostic program to help identify the problem?

---

### Post by sidzen on 2011-08-23
Suggest downloading System Rescue CD  
( [http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.3.0/](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.3.0/) ), 
burning it to CD at no more than 8X, 
booting to it on the PC in question. 

Hit default four or five times [Enter] and, at the multi-colored prompt on the page that asks user 
to enter either "wizard" or "startx", type in the command which will wipe your entire hard drive with zeros 
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync [/PHP]When it's done (make a sandwich, it will take a while) you will see some stats (four lines) ending in "xx MB/s" 
 
Type in 'startx' at the prompt, which will bring up a yellow-colored terminal window.  In this window, at the prompt there, type in 'gparted.' 
 
Partition, formatting most of hdd to ext4, or as desired 
 
Best wishes!

---

### Post by The standard username on 2011-08-23
can I do this only to the partitions I want to use? 
I want to keep windows xp. I can try backup .  but do you have explanation as to why this would be needed.  I mean what would make gparted hangs if the hdd had ntfs partition and not zeroed.  
I appreciate your help, but just want to know . so I can consider going the rough road and wipe windows xp while enjoying a sandwich (;.  you know it takes long time to upgrade XP to sp3

---

