---
title: "Partioning with encryption and dual boot"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by andreas6 on 2013-09-28
As i'm new to the forum: Hey.

Usually i'm using Arch Linux, but i want to try to make me a server, just for the knowledge. Want to try both Ubuntu and CentOS, so a dual boot is what i'm going for. But as i'm thinking of encrypt them both i just don't know how to partition my harddrive. 

Been googleing and searching for an solution, but none that fits my problem.

EDIT: And i want to use /home for both Ubuntu and CentOS. If thats possible...

---

### Post by TheFu on 2013-09-28
Welcome to the forums!  

Arch is a fantastic distro! ... er ... for power users and people willing to be on the bleeding edge ... with things breaking from time to time.
Enterprises and normal end-users just want the computer to work - no surprises please. That is where RHEL/CentOS and Ubuntu Servers come in.

First, I've never encrypted the entire partition, so I dno't know how that works under Ubuntu. I have encrypted HOME dirs and that works fine under Ubuntu.  Also, I've read from others in these forums that encrypting Ubuntu Server (everything or everything except /boot) doesn't work too well.  With CentOS, the same poster didn't have issues.

So ... I have doubts that /home can be shared since you'll need to ensure that every library involved matches between the 2 systems. Doubtful that can be accomplished.  Perhaps if you have separate /home for each, then create another partition and mount it under both /home/{inserter-userid}/data and use a common program for the encryption - like LUKS - then it might work?  I wouldn't risk the entire /home/{userid} without testing something first.

---

### Post by andreas6 on 2013-09-28
I'm really satisfied with my Arch system (running on my laptop and my Raspberry Pi). This is, as i said before, just for learning new stuff and a chance to get to know some of the distros known for enterprise-like system (or whatever i should call it...). 

The shared /home directory seems like an illusion at the moment. I think i just mount a part of the partition for "shared" files, lika music and stuff. 

But the other stuff SHOULD be possible. Trying out some stuff right now, but havn't got anything to work properly. Would be nice if the guided partitioning in the installation could make parts of the harddrive encrypted instead of just encrypt the whole disk. And to make things alittle more pain in the ass, some changes can't be undone, so i have to reboot from time to time. All i can say is that i now know my ESSID and password rather well =)

Oh well, I'll just keep trying alittle more before i give up.

---

