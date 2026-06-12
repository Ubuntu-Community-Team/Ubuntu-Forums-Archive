---
title: "Porblems with booting from CD - Ubuntu Help me boot From CD Files Question"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by NuxIT on 2012-04-29
Hi, So I was prepping my machine for the Ubuntu 12.04 load. I was going to do a Dual boot with Windows XP. So, I cleaned up 25 GB of space on my of my drives to load Ubuntu onto. However, I couldn't get my x86 32 bit CD to boot even though the ISO burn appears fine. I load the disk in Windows and it come up with the Installation options. 

So, I tried the Ubuntu Help me boot From CD Files install and it started to load a bunch of files to what I'm guessing is my C: drive. The Boot files failed to load at the end because it ran out of space on C: and now I don't know where Ubuntu boot put all these boot files! I'm missing 500MB of space from CD Files install and don't know where it put the files? Any ideas? I turned off Hibernation and now I have 1 GB free but I want my 500MB Back!!!

Another messed up thing that happened is I lost my Disk and partitions in Windows that I was going to load Ubuntu onto!!! I don't know how the heck that happened but the ONLY way I can see this disk in Windows now is if I set it to Master on IDE and disable the other disk on the controller! It's quite frustrating since I see both disk in BIOS but once windows boots it no longer sees my Seagate disk unless I set it to Master on IDE?? What the heck?? Thanks for any  tips and suggestion on where the heck Ubuntu stores the CD temp files for help with boot from CD. And what might of happened to my disk from this.  Grrrr

EDIT, I just put the CD in and noticed that it starts to put the files onto C:\ubuntu
Still not sure where my 500MB went since I did a search for last modified files on C: drive and nothing stands out. Strange. Not sure what's glitching out on my load/system. Probably take a brake for a while.

Ok, I just remembered that after I did the Help me boot from CD option I was shutting down to reboot and windows XP asked me what hardware Profile to Choose. I only have one Profile so I choose Profile 1. It's strange because Windows never ask me that before and now  I think my seagate drive ST380011A some how isn't included in that Hardware Profile now unless I set it to master on IDE. Has anyone encountered this before? I'm pretty certain it has to do with the Hardware Profile. I searched the registry for ST380011A and tried to delete those entries but it would not let me. Drive still shows up in BIOS but nothing in Windows or Disk Manager.. Thx

EDIT Again, LOL. Welp, Nevermind. I have a strange setup and I changed some things in BIOS again for my drive controllers and now I see the drive in Windows XP again. Pretty weird but changing the controller in BIOS got the drive back into XP.

---

