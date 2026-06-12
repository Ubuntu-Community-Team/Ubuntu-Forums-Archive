---
title: "Upgrade from 17.04 to 17.10 stuck &quot;Installing for x86_64-efi platform.&quot;"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by riverfr0zen on 2017-10-20
The upgrade (via Software Updater) was stuck at the point above for several hours. I exited the upgrade and then tried 

dpkg --configure -a

but it just keeps stalling at the same place when it comes to installing grub-efi-amd64:

> sudo dpkg --configure -a
Setting up grub-efi-amd64 (2.02~beta3-4ubuntu7) ...
Installing for x86_64-efi platform.

Any ideas? Thanks in advance.

---

### Post by oldfred on 2017-10-20
Either you somehow converted to UEFI and do not have an ESP - efi system partition.
Or drive changed from sda to sdb and do not have an ESP on drive seen as sda.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by riverfr0zen on 2017-10-20
Thanks for the reply. I did have to mess around a little when I first installed Ubuntu (17.04) on the system trying to figure out how to switch to gpt partition table. Unfortunately it's a all a crazy haze now (although it made sense at the time =)

Anyway, I hit CTRL-C on the cmdline where the dpkg --configure command was stuck, and it looks like it upgraded the rest of the packages (except for a couple, which I'm assuming are related to the grub-efi package--I was able to cancel those the same way).

Decided to take a chance and reboot (ran update-grub for luck). Everything seems to be okay. Unfortunately the grub menu is full of a bunch of extra stuff (low-latency mode?), possibly because the upgrade to 17.10 didn't finish smoothly(?). In any case, the system is working fine, and I'm in Gnome3 instead of Unity as expected. I had to choose the '4.13.0-16-generic' kernel from grub rather than the low latency one (which doesn't work).

Crossing fingers, I guess. But here's the BootInfo summary in case you can glean anything useful from it:
[http://paste.ubuntu.com/25781005/]("http://paste.ubuntu.com/25781005/")

---

### Post by oldfred on 2017-10-20
Your sdc drive is not correct.
It has to be gpt as over 2TiB, but is MBR, so you converted it to a 2TiB drive.
Or you have some proprietary configuration that is not recommended. Then conversion to gpt may lose data.

You may be able to convert to gpt, but if you have important data on drive make sure you have good backups.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
      
 Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by riverfr0zen on 2017-10-20
Thanks for pointing that out! Actually /dev/sdc is a USB drive intended for backups, so the Grub2 shouldn't be installed there (it's fine if /dev/sdc is MBR, because I don't need partitions > 2TB there). The OSes, including Ubuntu are all on /dev/sda.  So can I just move Grub2 to /dev/sda (a GPT disk)? Will that iron out the inconsistencies? 

FWIW the OS is booting just fine, it seems. I just want to fix the issue so it doesn't cause similar problems in the future. Thanks again for your help.

---

### Post by oldfred on 2017-10-20
Your sda2 is the ESP and that is where grub should be installing.
It says you have UEFI Secure Boot on, may be better to try with it off?

Its not the size of the partitions, but the size of the drive that MBR can support.
MBR was designed base in the early '80's when MB was large, GB was not really considered. So having TB as max was considered extremely large or overkill.

       MBR details including 2TiB limit and GPT link
[URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record
[/URL][http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://www.rodsbooks.com/gdisk/whatsgpt.html](http://www.rodsbooks.com/gdisk/whatsgpt.html) 
    
[URL="http://en.wikipedia.org/wiki/Master_boot_record"]
[/URL]

---

