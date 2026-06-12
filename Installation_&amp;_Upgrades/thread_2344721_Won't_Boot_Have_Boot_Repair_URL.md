---
title: "Won't Boot Have Boot Repair URL"
date: 2016-11-27
forum: Installation &amp; Upgrades
---

### Post by asker3 on 2016-11-27
Hello,

I had Ubuntu 14 on an old XP box. I tried to upgrade from USB to version 16 but it would not. It said there was not enough room on the drive. I think there should be on the hard drive. Now it won't boot at all not even to the original XP disk. I can get the "Try Ubuntu" to work and I have tried Boot Repair...

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

It did not repair it and the URL it gives is [HTTP://paste.ubuntu.com/23545221/](HTTP://paste.ubuntu.com/23545221/) and the instructions say to put it up on this forum.

I have worked with this problem for a long time now and am now at a loss.

Thank you for your assistance.

---

### Post by oldfred on 2016-11-27
You show no hard drive at all.
Does BIOS show drive?
If BIOS shows drive, in Disks, icon in upper right corner has Smart Status. Is that working and showing your drive?

---

### Post by asker3 on 2016-11-28
Not sure what I am supposed to be seeing.

It is an Intel processor. There are no icons or Smart Status. UEFI boot is enabled.

---

### Post by oldfred on 2016-11-28
You mentioned it was an old XP computer which would have been BIOS only.
Only computers with Windows 8 or later were UEFI. A few Windows 7, most often downgrade from a Windows 8 hardware design.

So if you have an UEFI setting is it then really a newer computer?
And then what brand/model?

But UEFI/BIOS has to show drive other wise no operating system will be able to see it.
Are drives set to AHCI mode in UEFI/BIOS?

---

### Post by asker3 on 2016-11-28
It is a Windows XP Home Edition

"Drive Configuration" says...

ATA/IDE Mode -- Native
Configure SATA as -- IDE
S.M.A.R.T. -- Looks like is set as disabled

So...SATA should be set to AHCI?

Should S.M.A.R.T. be enabled?

---

### Post by oldfred on 2016-11-28
SATA should be AHCI, you probably had to have it off for XP.
I had to turn it on in my system when I got a small SSD in 2011. But SSD had to have AHCI on for trim to work, but then XP did not. So I turned off XP and have been happy since.

Generally if drive supports SMART better to have it on. Sometimes throws false data, but in most cases helps to track status of drive.

---

### Post by asker3 on 2016-11-28
That got the USB to start up. I can "Try Ubuntu" but it will not install it. It says "No root file system is defined. Please correct this from the partitioning menu."

The partitioning menu is completely unusable.

---

### Post by oldfred on 2016-11-28
If you get no root file, then you have to create at least one new partition or select one ext4 partition and use it as /.

Examples. May show older versions, but still the same.
       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) 

For whatever reason I find using gparted slightly easier for partition changes. But still have to use Something Else to select (change) the ext4 partition I created to use as /. Standard install is just / & swap. If you have swap created in advance, it does auto find that and use it.

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

### Post by asker3 on 2016-11-29
OK, so it looks to me like I need to use the Purge and Reinstall method. I have Grub 2.0 tar file.

How do I use it? Do I put it on a disk or USB and rum commands?

Will it format the drive so I can install Ubuntu? I will need to format at some point. I do not care about the old XP install at all if it is still in there. It can go and I hope it will.

---

### Post by yancek on 2016-11-29
Why would you want a Grub2 tar file?  Grub will be installed during the installation of Ubuntu.  You don't need anything else.  Are you trying to repair your old install or do a new install of 16.  If you are doing a new install and don't have any data on the drive to save, just select the option to "Erase Disk and install Ubuntu".  If you want something else, clarify.

---

### Post by asker3 on 2016-11-29
Hi yancek,

I would like nothing more than to Erase disk and install Ubuntu!

I have tried it many times. Nothing happens. To install there is no partition being seen at all or apparently even the hard drive.

This began when I tried a clean install of version 16.0 over 14.0 which was done as above as Erase disk and install Ubuntu over Widows XP.

---

### Post by oldfred on 2016-11-29
You cannot install to a drive not seen.
If in BIOS it is shown, but not in installer or gparted, then drive may have failed.
If not in BIOS either connection came loose, or it failed.

---

### Post by asker3 on 2016-11-29
Looks like drive failed then. Well... thanks. Now I'm wondering about the advisability, ease, and cost of sticking a new hard drive in this XP Home Edition box.. I wonder if it's easy enough and worth it. If HDs will even work on it anymore.

---

