---
title: "XP won't dual boot after install of Ubuntu"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by tom102 on 2014-05-24
I'm a new user of Ubuntu so please be gentle and patient.  I hope I'm putting this in the correct place as this is my first forum entry.  I have searched the forum and found several other dual boot problem threads but none seem to match mine exactly.

I have a fairly recent Acer desktop that was running MS XP pro.  After MS desupported XP I decided to install Ubuntu 12.04.4 LTS in a dual boot format to do most of my computing, especially internet work, but I wanted to keep XP for offline applications that I use frequently.

When I installed XP on this machine, I intentionally left a 30GB partition of unused free space for future file storage or dual booting purposes (the machine has a 1TB HD).  So, I figured I could install Ubuntu in that partition without repartitioning or messing with my XP OS or filesystem.

I installed Ubuntu and it works fine.  I'm very happy with it so far and it seems to have no apparent problems.  In fact I can still access my XP personal files (also in their own partition separate from the MS OS) using a "new volume" that showed up automatically in Ubuntu.

When I boot the computer Ubuntu shows as the first boot device and "Windows operating system" shows up as the last one (I also have a DOS partition that shows in the middle along with hardware boot options.  

If during boot I select the Windows Operating System, XP does not come up.  Instead I get a black screen with a blinking cursor in the first position.  I ran the Ubuntu boot repair facility but it did not change the behavior.

I know this is a boot sector problem but I don't know why or how it happened since I installed in a separate partition and did not mess with the partitioning (or anything else) that was already on the machine.

Any suggestions would be greatly appreciated, but keep them simple please or step by step.  Thank you

---

### Post by LastDino on 2014-05-25
Some more info indicating your hardware config and BIOS would be helpful. You said you installed XP recently? What was on it before?

---

### Post by kansasnoob on 2014-05-25
Since Ubuntu boots OK just follow the steps here to install Boot-Repair in Ubuntu:

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

Then create a Bootinfo Summary and post the link here.

---

### Post by tom102 on 2014-05-25
> **LastDino said:**
> Some more info indicating your hardware config and BIOS would be helpful. You said you installed XP recently? What was on it before?

My system is an Acer Aspire M1935 desktop (which I believe is an Asia only model as I live in Thailand) with 4gb memory and 1tb disk, intel core i3-2120, 3.30 ghz.  I bought the box empty and installed my own copy of XP Pro 32 bit on it from CD, and installed only the applications I needed to use.  

When I installed XP I partitioned the drive with a small 2gb FAT DOS :C partition and the MS OS actually installed on a 30gb NTFS partition :F, as D and E were hardware devices in the box.  I partitioned it with two additional partitions of :G NTFS (630gb) for personal file storage (photos, videos, music, documents, etc.) and :H as an 332gb empty partition for some future use.  

The empty partition designated as  :H in MS is where I installed Ubuntu, breaking that partition into 330gb for the OS, applications, and my personal files and an additional partition of 2gb of swap space which I configured during the installation as instructed.  While installing Ubuntu, I did not adjust the DOS, MS, or original personal storage partitions (C, F, and G) at all.  I don't know yet how to gather info on the Bios in Ubuntu, but it is the native bios that came with the box.

---

### Post by tom102 on 2014-05-25
> **kansasnoob said:**
> Since Ubuntu boots OK just follow the steps here to install Boot-Repair in Ubuntu:

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

Then create a Bootinfo Summary and post the link here.

Here's the link created by the boot info summary:

[http://paste.ubuntu.com/7517598/](http://paste.ubuntu.com/7517598/)

---

### Post by oldfred on 2014-05-25
Windows really only boots from primary partitions. You can have a second install of Windows in a logical partition, but it must boot and have its boot files in a primary NTFS partition.
Your install of XP is now in sda5 which is a logical partition and its boot.ini says it is booting from sda3.

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition([COLOR=#ff0000]3[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR=#ff0000]3[/COLOR])\WINDOWS="Windows" /noexecute=optin /fastdetect
```

You may be able to use fixparts or testdisk to convert your sda5 back to a primary partition. You may still have to run repairs or edit boot.ini to fix which partition it thinks it is in. Only because you have some available primary partitions can you rearrange. And that all the logicals will still be in one extended partition.

       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by mastablasta on 2014-05-26
why do you need a MS DOS partition? Dosbox will work excelent with your specs.

---

### Post by tom102 on 2014-05-26
> **mastablasta said:**
> why do you need a MS DOS partition? Dosbox will work excelent with your specs.

When I did the XP install I followed the partitioning advice of a web guru who advised a small Dos partition as :C as it would avoid virus attacks that target the :c drive because that is where most people have their MS OS.... in other words, just a security measure.

---

### Post by fantab on 2014-05-27
XP especially will not boot from a Logical Partition. It needs to be on the first Partition and that partition must be 'Primary'.

Reinstall XP without any Dos, directly on C: (Not installing windows on C: is very old trick and outdated really).
If I were you, I would partition my HDD as follows:
50Gb Primary NTFS XP C:
25Gb Primary Ext4 Ubuntu '/'
25Gb Primary Ext4 Free (if in future you need to install another linux distro or another Ubuntu version or flavor)
???Gb Extended Partition
4Gb Logical SWAP
???Gb Logical /home or simple ext4 partition to store your personal data.

(???= all the remaining Gb)

My two cents......

---

### Post by mastablasta on 2014-05-27
mhm do what he says ^^

not everyting web gurus write is golden... i've had my share of them and from then on i really look in various sources before deciding.

even if that still worked it doesn't protect you from rootkits and such . they are nasty. new malware will often try to insert itself into boot mnagaer (doens't matter where C drive is or what OS you are using). anyway use a descent & updated firewall and AV and avoid strange sites and you should be fine.

---

### Post by tom102 on 2014-05-27
So the only real solution is to wipe the drive and repartition and  reinstall everything?  I was hoping for something a bit easier but if  that's what I need to do I guess that's the solution.

---

### Post by oldfred on 2014-05-27
Since you have primary partitions available you can convert the XP to primary, it probably will need repairs but should work.
Windows usually is the first partition but does not have to be.

       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

    
But you should disconnect from Internet if you want to use XP.

---

### Post by fantab on 2014-05-27
> **tom102 said:**
> So the only real solution is to wipe the drive and repartition and  reinstall everything?  I was hoping for something a bit easier but if  that's what I need to do I guess that's the solution.

Yes reinstalling is best and simpler than 'fixing' the issue, since its relatively a new install. HDD formating and partitioning is not something we do often. Partitions. if planned well, can last the life of the HDD. Setting up well planned partitions is worth every effort.
Like its been pointed out there are tools to convert 'logical partition' to 'primary' but IMO it will be better and cleaner to re-format HDD and re-install your OS.

Backup All your Important DATA first.

---

### Post by tom102 on 2014-05-27
Reinstalling XP is impossible because the CD contains a copy that is years old and with no MS support it would be impossible to get it back up to date with SP3 and the thousands of security updates.

---

### Post by mastablasta on 2014-05-28
> **tom102 said:**
> Reinstalling XP is impossible because the CD contains a copy that is years old and with no MS support it would be impossible to get it back up to date with SP3 and the thousands of security updates.

you fell for the oldest marketing/sales trick in the book. make it urgent and necessary for customer to buy.

what you wrote here is based on FUD deliberatelly spread by some.

have a look here and download away...: [http://technet.microsoft.com/en-us/windows/windows-xp-service-pack-3.aspx](http://technet.microsoft.com/en-us/windows/windows-xp-service-pack-3.aspx)

furthermore there is a "hack" available that can extend your support for winxp to 2019 if you wish to get more security updates. the hack is not edvisable sicne it is not known if they (MS) plan to close up the loophole, so i won't write about it here.

---

### Post by LastDino on 2014-05-28
And next time I manage to get XP bootable normally and in updated position, I would make sure to make a tested clone of it, just in case I run into situation like this. Just saying.

---

