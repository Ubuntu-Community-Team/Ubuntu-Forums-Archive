---
title: "Boot problem"
date: 2022-05-21
forum: Installation &amp; Upgrades
---

### Post by sundaresh on 2022-05-21
My ubuntu installation does not boot. 
Among the errors it gives it starts off by saying it cannot find init, and fsck errors and goes to grub shell. I would like to recover a lot of my own programs, on my computer. Please help.

---

### Post by oldfred on 2022-05-21
You do have good backups?

If corrupted or broken drive, Boot-Repair cannot fix issue, it primarily fixes grub issues. But report may show more info.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by sundaresh on 2022-05-24
A nearby computer shop examined the hard disk using some software and showed me it has 8 bad sectors but otherwise the disk is 95% ok. What would you suggest ? Also the disk has only one partition and no FAT 32 partition. So the entire disk is one partition.

---

### Post by tea for one on 2022-05-24
In post 2, oldfred suggested that you download and run the boot-repair report.
The report provides many details to allow forum members to offer help and advice.
Any reason why you do not want to supply the report?

---

### Post by sundaresh on 2022-05-25
Yes, not a seasoned operator, nor a casual user. Let me get this straight, I should make a bootable pendrive of  Boot-repair with ppa option, and boot with it. Is the ppa option for creating the bootable USB of Boot-repair or is it an option for booting using Boot-repair. Are there any other options I should choose and I boot with Boot-repair ? Just a thought, would trying to reinstall Ubuntu , detect existing version and possibly recover it ? It's a shame that Linux should be going the Windows way. All these would be proprietary Windows hacks when there is clearly nothing ethical about either Windows or hacking.

---

### Post by tea for one on 2022-05-25
> **sundaresh said:**
> Let me get this straight, I should make a bootable pendrive of  Boot-repair with ppa option, and boot with it.
No, the boot-repair iso may contain an older version of the boot-repair software.
It is better to follow the instructions detailed in option 2 of [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Prepare a bootable USB using your Ubuntu iso.
Boot into a live session.
Open a terminal and add the boot-repair repository.
Then download the boot-repair utility, run the software and provide the report.

> **sundaresh said:**
> Just a thought, would trying to reinstall Ubuntu , detect existing version and possibly recover it ?
It would be a good idea to backup your personal data while using the live session.
As you mentioned that your disk has some bad sectors, a backup is essential.

> **sundaresh said:**
> It's a shame that Linux should be going the Windows way. All these would be proprietary Windows hacks when there is clearly nothing ethical about either Windows or hacking.
I do not understand what you mean by this?
Using boot-repair is a useful feature of Ubuntu and, if you have a quick search through the forums, many users have had success with this appplication.

---

### Post by yancek on 2022-05-25
>  A nearby computer shop examined the hard disk using some software and  showed me it has 8 bad sectors but otherwise the disk is 95% ok. What  would you suggest ?

The first thing to do when you get an error reporting bad sectors is to run a filesystem check using the fsck software.  It doesn't repair anything because software can't repair hardware so the bad blocks are marked so the system does not try to use them.  Any Linux on a CD/DVD/USB will have fsck.

I also don't understand what you meant by your comment about Linux going the windows way??

---

### Post by sundaresh on 2022-05-26
Regret comment. I have a fair idea now. Thank you.

---

