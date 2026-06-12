---
title: "ubuntu partions screen blank"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by somegirl1990 on 2012-05-28
i have an hp pavillion dv6000 laptop. it has no operating system on it.  So origipnally I was going to download ubuntu 12.04 the latest version  but it said I didnt have enough space for it. So I downloaded ubuntu  version 10.04 which i had to download onto a blank disk as an iso image  from another laptop. i put the disk in and when i come to the partion  page its blank.. ive read everything on here trying to figure it out i  removed dmraid and it still didnt work i typed in "sudo blkid" in  terminal and all it said was TYPE:squashfs i dont know what that means.  lol. what do i do to make this work? im so frustrated. Please help me.  thank you. let me know if you need anymore info. FYI: my sister bought  this computer from a pawn shop or something so it was already like this  when she got it im trying to fix it for her. so i probably wont be able  to answer questions about the history of the computer

---

### Post by wilee-nilee on 2012-05-28
> **somegirl1990 said:**
> i have an hp pavillion dv6000 laptop. it has no operating system on it.  So origipnally I was going to download ubuntu 12.04 the latest version  but it said I didnt have enough space for it. So I downloaded ubuntu  version 10.04 which i had to download onto a blank disk as an iso image  from another laptop. i put the disk in and when i come to the partion  page its blank.. ive read everything on here trying to figure it out i  removed dmraid and it still didnt work i typed in "sudo blkid" in  terminal and all it said was TYPE:squashfs i dont know what that means.  lol. what do i do to make this work? im so frustrated. Please help me.  thank you. let me know if you need anymore info. FYI: my sister bought  this computer from a pawn shop or something so it was already like this  when she got it im trying to fix it for her. so i probably wont be able  to answer questions about the history of the computer

Does it have  a HD?

---

### Post by somegirl1990 on 2012-05-28
> **wilee-nilee said:**
> Does it have  a HD?

Hmm.. Idk. How Do I find out?

---

### Post by somegirl1990 on 2012-05-28
> **wilee-nilee said:**
> Does it have  a HD?

OH WAIT YOU MEAN HARD DRIVE?? yes it does i took it out and put it back in just to make sure it was in right still didnt work.

---

### Post by wilee-nilee on 2012-05-28
> **somegirl1990 said:**
> OH WAIT YOU MEAN HARD DRIVE?? yes it does i took it out and put it back in just to make sure it was in right still didnt work.

Open gparted it is in the menu, you may need to put a partition table on the hard drive. So once open if it shows a hard drive empty choose device-create partition table, iot should default to a msdos type, when done close gparted and try the install again.

Hard to tell exactly why their is a blank page, this just might be it.

---

### Post by somegirl1990 on 2012-05-28
> **wilee-nilee said:**
> Open gparted it is in the menu, you may need to put a partition table on the hard drive. So once open if it shows a hard drive empty choose device-create partition table, iot should default to a msdos type, when done close gparted and try the install again.

Hard to tell exactly why their is a blank page, this just might be it.

there are no devices detected, but theres a hard drive in the computer. what now? lol

---

### Post by wilee-nilee on 2012-05-28
> **somegirl1990 said:**
> there are no devices detected, but theres a hard drive in the computer. what now? lol

Not sure really could be a bad hd or bad connection, are my ideas, maybe others will have some ideas, bummer deal though to get started with this.

---

### Post by oldfred on 2012-05-28
If you go to BIOS, as soon as computer starts it should tell you what key to hit. Key varies by vendor. I do not have HP but it is del key, some use f2 or could be just about anything.

Does BIOS show a hard drive?

---

### Post by somegirl1990 on 2012-05-28
> **oldfred said:**
> If you go to BIOS, as soon as computer starts it should tell you what key to hit. Key varies by vendor. I do not have HP but it is del key, some use f2 or could be just about anything.

Does BIOS show a hard drive?

This is what i see in BIOS under Main

System Time
System DAte
Notebook Model
Product Number
System Board ID
Service ID
Processor Type
Processor Speed
Total Memory
BIOS Version
Serial Number
UUID Number
Diagnostic Log

---

### Post by listerdl on 2012-05-28
Why dont you use gparted? Burn it on an iso and take a look at the HD - partitions etc...

Perhaps you just need to wipe it and make it all a nice clean ext4 then install Ubuntu

---

### Post by oldfred on 2012-05-28
Continue on the other tabs for BIOS and does it show the details of a hard drive or just the CD?

If BIOS does not see drive then it is a hardware issue.

---

### Post by somegirl1990 on 2012-05-29
> **listerdl said:**
> Why dont you use gparted? Burn it on an iso and take a look at the HD - partitions etc...

Perhaps you just need to wipe it and make it all a nice clean ext4 then install Ubuntu

and if it is a hardware issue, theres no way to fix it? id have to just replace it? or do you know?

---

### Post by somegirl1990 on 2012-05-29
> **oldfred said:**
> Continue on the other tabs for BIOS and does it show the details of a hard drive or just the CD?

If BIOS does not see drive then it is a hardware issue.

and if it is a hardware issue, theres no way to fix it? id have to just replace it? or do you know?

---

### Post by oldfred on 2012-05-29
Did you check the other tabs to see if BIOS sees hard drive?

Then double check that connections are tight & correct. Very occasionally it can be the cable, but if not then the drive is probably the issue. But you should remove drive and try it on another system to confirm. Or spend $10 for a USB drive case and use that to test on another system. If drive is dead you can use drive case for another drive to use as a backup.  If drive working then it may be motherboard issue or who knows. 

Others may have suggestions.

---

