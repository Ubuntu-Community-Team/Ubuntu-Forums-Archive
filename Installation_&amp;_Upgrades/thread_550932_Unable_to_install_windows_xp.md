---
title: "Unable to install windows xp"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by Nalum on 2007-09-14
Hi all,
I've been using Ubuntu for a while now and wish to dual boot with windows xp so that I can play games without having to mess around with Wine.

I've tried to install it on my second(slave) HD but when I get to the point of selecting what HD to install it on I get a message saying that it needs access to the HD that has ubuntu installed on it but cannot access it because it cannot read the format of the HD and so I can go no further.

Has anyone come across this problem or know of a solution that doesn't involve reinstalling ubuntu?

Thanks for your help.

Nalum

---

### Post by Pumalite on 2007-09-14
That's because the best way to dual boot with XP is to install XP first. Windows likes to be sda1

---

### Post by Can0n on 2007-09-14
I have almost the same problem as the author. When I removed my windows-partition throu the installationprogram and then tried to create a new one, cause I wanted to reinstall windows, it did create one. But when I wanted to make it a NTFS-drive it said something like "This is not a real windows-partition. Go back and create a new one. BLa blabla".

The harddrive I'm trying to reinstall windows on is /dev/sdb, maybe thats why?
It also contains my linux-partitions. root (/), home (/home) and swap, maybe thats why?

---

### Post by Pumalite on 2007-09-14
What do you think?. It's windblows you are dealing with: wants the first hard drive, the first partition, and the whole computer for itself. Get rid of it!

---

### Post by Can0n on 2007-09-14
I would love to get rid of it but I want to play games with my friends =)

---

### Post by Pumalite on 2007-09-14
Get a console.

---

### Post by Can0n on 2007-09-14
Someone else with any great ideas?

---

### Post by Pumalite on 2007-09-14
What's wrong with a console? (I'm not a gamer. so I asked to be educated here)

---

### Post by bilkan on 2007-09-14
Did you try changing the boot priority from the BIOS?

---

### Post by louieb on 2007-09-15
What I normally do is unplug the Linux drive, Install XP, then plug the Linux drive back in.  Then create an XP entry in /boot/grub/menu.lst to boot XP on the second drive.
Heres a good how to on the whole process.  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by maybeway36 on 2007-09-15
because a console doesn't run PC games.

---

### Post by djdjules on 2007-12-12
Hey people. I am facing a similar problem.

I had a dual boot: XP + Ubuntu
Then after some changes to the partitions with Gparted windows stopped working.
Windows could not boot anymore, it would give a BSOD telling me to run chkdsk.
The funny thing is that I could still see my windows files from ubuntu.
I tried to run chkdsk with the windows recovery console from the CD but it didn't work because the recovery console could not see the HDD.
Since Ubuntu was still working I tried to do ntfsfix but this didn't help.
So I gave up and backed up all my windows stuff and using Gparted I deleted the windows partition.
After this I tried to reinstall windows. The installer was able to list my HDD but said that it could not access the disk.
I went back to Gparted and tried formated the unalocated space to ntfs and retried to use the windows installer.
Windows installer still said that it couldn't access the disk.

At this point the HDD only has an empty ntfs partition and ubuntu after that. Ubuntu still works perfectly. 
I am thinking that I may have to backup ubuntu and wipe the whole HDD.
Then try to reinstall windows.
What do you people suggest?

---

### Post by Pumalite on 2007-12-12
Good idea. Use Gparted Live CD to erase everything in your hard drive, make new partition of your whole drive, formatted ntfs. Install XP. Boot from Gparted Live CD again and resize your XP partition and install Ubuntu. Some people prefer making two partitions: one ntfs for XP and another for Ubuntu. I prefer the first method.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

