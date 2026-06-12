---
title: "Laptop won't boot to grub menu?"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Def215 on 2011-11-27
Hi everyone. So I have a slight issue with my netbook. My netbook won't boot at all. It will turn on and my netbooks splash screen will appear and then it will go to the blinking underscore cursor at the top lefthand side. I can't type anything in or do anything. It all happened after I was switching partitions, from windows xp and ubuntu. I was getting a word file and PDF files from my ubuntu partition to my windows partition. I put ubuntu in hibernate but I accidentally left my USB thumb drive in the laptop, which my settings are in USB boot mode. So when I went to get on my windows partition, it tried to USB boot and it said there was a boot error. So I turned it off and turned it back on without my thumb drive in and I am at where I'm at now.

If it's any help here are my computer specs. I have a Sony vaio netbook with an intel atom processor 160gb hd 1gig ram.

Does anyone think that I can fix this by using the live cd and reinstalling the grub bootloader? Any help is appreciated.

---

### Post by drs305 on 2011-11-27
If you can boot a LiveCD with your netbook, the easiest thing to do would be to install Boot Repair and allow it to try to fix things. 

If that doesn't work, Boot Repair has an option to run the Boot Info Script. This script will produce a file which will show us what has happened to your boot files.

This is the community documentation.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

You can also click the "Boot Repair" link in my signature line to view the thread in these forums.

---

### Post by Def215 on 2011-11-27
Thanks for the reply. I've downloaded live cd or the installation disk. I'm trying to USB boot my netbook and now it's giving me a message that says disk error. Is it because I didn't create my live cd correctly? I just extracted the files to a flash drive and now I'm trying to boot it with no luck.

Sorry in advance. I'm not the most computer savvy person in the world.

Edit: found the directions to get it to USB drive.

---

### Post by Def215 on 2011-11-28
> **drs305 said:**
> If you can boot a LiveCD with your netbook, the easiest thing to do would be to install Boot Repair and allow it to try to fix things. 

If that doesn't work, Boot Repair has an option to run the Boot Info Script. This script will produce a file which will show us what has happened to your boot files.

This is the community documentation.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can also click the "Boot Repair" link in my signature line to view the thread in these forums.

THANK YOU SOOO MUCH DRS305!:cool:

i cant tell you how much i appreciate the help! it worked and im posting this right now from my windows xp partition.

thank you again. i really appreciate the help from this forum.:)

---

### Post by mörgæs on 2011-11-28
Good, then please mark the thread 'solved'. It will help other people searching for an answer.

---

