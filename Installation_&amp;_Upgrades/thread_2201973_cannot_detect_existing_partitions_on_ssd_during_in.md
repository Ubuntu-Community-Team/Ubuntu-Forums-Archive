---
title: "cannot detect existing partitions on ssd during install"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by thelost on 2014-01-26
Hi there

I have a dell xps 15 (l502x) laptop with a newly installed samsung 250gb evo 840 ssd and the original 750gb internal sata drive (now moved to the where the dvd drive was). I want to be able to install windows 7 and linux to the ssd and use the secondary drive for data.

So far I have successfully installed windows 7 to the ssd in a 160gb partition, and now want to install linux on the remainder of its freespace. The problem is that whilst the buntu installation recognises the 750gb harddrives partitions, it does not recognise the ssd's. It sees that the drive's there, listed as sda, but does not see any of the partitions that are on it.

I've tried pulling the second drive out so that only the ssd is present (my old windows installation is still on it), but that made no difference. I tried quitting the installation to the live desktop and launching gparted, but indeed it only sees the disk, not any of its partitions.

I have generated a report from boot-repair, here's a link: [http://paste.ubuntu.com/6823079/](http://paste.ubuntu.com/6823079/)

Any help people could give in this respect would be gratefully received. I'm sure that others have had similar problems, but I've been digging so much that I finally decided rather than vanish down a rabbit hole I should probably ask for help.

Cheers
Lost

---

### Post by fantab on 2014-01-27
The problem seems to be with the SSD. Did you change the partition table when installing Windows?
If its an option, then remove all the partitions on the SSD (You will erase Windows install). Create a new Partition Table with Gparted from LiveCD and create some partitions.
Reboot the Ubuntu LiveCD and see if Ubuntu sees the SSD partitions.

If that doesn't help then try [Fixparts]("http://www.rodsbooks.com/fixparts/"). 

If you have an UEFI system then I suggest you install both OS in UEFI mode.

Also Hibernating Windows too can cause similar issues. Make sure your Windows in NOT hibernating.

---

### Post by thelost on 2014-01-27
I installed windows 7 to the ssd fresh, creating a 160gb partition for it (plus 100mb system reserved partition which windows automatically creates).

Wiping windows really isn't an option as I need my laptop operable for work, unless I perhaps clone the partition and then restore it afterwards. Is it not possible to work with partitions as they are and make them recognisable? I am not very conversant with the boot-repair report and what's being shown, I guess I need to understand a little more about what the system is/isn't seeing and how to repair it if necessary. I feel uncomfortable making sweeping changes like wiping my whole disk on the off-chance they might work, I'd rather know what the problem is beforehand so that the outcome was predictable. Are there any resources that go into detail on this?

cheers

---

### Post by fantab on 2014-01-27
Alright.
There is something definitely not right with your SSD/Windows install. Try following:

Get into your BIOS and see what mode is SATA set to, IDE, AHCI or RAID. We need it be AHCI.
Also check in BIOS against SSD for any special settings. Check for IntelSRT, if its there and enabled then disable it.
Are you sure your Windows is NOT hibernating.

Run 'chkdsk' on your SSD:[ http://www.sevenforums.com/tutorials/433-disk-check.html]("http://www.sevenforums.com/tutorials/433-disk-check.html")

---

### Post by thelost on 2014-01-27
SATA is set to AHCI. No special settings for the SSD. I've run chkdsk and no errors reported, but I wouldn't expect anything to be wrong with the ssd as it's new, unless it's defective. 

I could always delete the hibernation file just to be sure, but I am pretty sure that it isn't hibernating, I never hibernate my laptop, though I do sleep it occasionally. There is a hibernation file on the c drive, but I think windows generates that as long as the system has hibernation turned on as an option.

---

### Post by oldfred on 2014-01-27
Boot-Repair is reporting all the zram partitions. I have not seen that and thought you have to enable that.
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM1NjQ)

So if Ubuntu is not working how is system showing zram? Or is this from Windows and not really zram but something in Windows?

It is not mounting any of the Windows NTFS partitions. Often caused by hibernation or chkdsk needed flags. 
Also if drive was gpt from UEFI install the suggested fixparts may fix it by removing old gpt data.
It is not showing SFS or dynamic partitions, but again zram is unusual.

You can keep old BIOS/MBR type install, but Windows 7 can be installed in UEFI mode from flash drive if flash drive is updated a bit.

---

### Post by thelost on 2014-01-27
> **oldfred said:**
> Boot-Repair is reporting all the zram partitions. I have not seen that and thought you have to enable that.
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM1NjQ)

So if Ubuntu is not working how is system showing zram? Or is this from Windows and not really zram but something in Windows?

It is not mounting any of the Windows NTFS partitions. Often caused by hibernation or chkdsk needed flags. 
Also if drive was gpt from UEFI install the suggested fixparts may fix it by removing old gpt data.
It is not showing SFS or dynamic partitions, but again zram is unusual.

You can keep old BIOS/MBR type install, but Windows 7 can be installed in UEFI mode from flash drive if flash drive is updated a bit.

I belive the zram is the Lubuntu Live USB showing up in the boot-repair report. I was running the report from a usb-key I prepared with Lubuntu installed on it.

I just checked with diskpart and disk management in windows and the ssd is showing as MBR not GPT.

---

### Post by oldfred on 2014-01-27
I see this:

 /dev/sda1     ?

Where the ? is normally an * for boot flag set. With question mark that may just be enough minor corruption to be an issue. 

From Windows reset active partition to sda1 or whatever Windows sees it as. Or if gparted, Disk Utility, testdisk or fixparts let you adjust it.

It looks like a partition table except for ?

```
 This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   335544319   167668736    7  HPFS/NTFS/exFAT
/dev/sda3       335544320   488392703    76424192    7  HPFS/NTFS/exFAT


```

---

### Post by thelost on 2014-01-27
Ah that's perfect. Well spotted! Inside windows I went into Disk Management and made sure the windows boot disk (sda1) was set to active. This worked perfectly, and now I have a fully functioning lubuntu installation.

thanks very much, really appreciated.

---

### Post by oldfred on 2014-01-27
Glad that worked, we were out of ideas otherwise. :)

---

### Post by thelost on 2014-01-28
out of interest, everything is working now, but when the computer booted this morning it presented me with the grub2 menu, and then afterwards the windows boot manager, and then booted as normal. last night I did change the boot order in grub2 so that windows would boot by default, but it seems like this means that it is now showing both boot managers on booting, perhaps as a result of changes, I'm not sure.

Is it possible to just use grub2, ie remove windows boot manager or similar?

---

### Post by oldfred on 2014-01-28
Windows does not show normally unless it has more than one entry in BCD. You may need to update or repair BCD?

 How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by thelost on 2014-01-28
hmmm. i do have my old install of windows on the secondary disk, which does show up as a boot option in grub2. I might transfer the data off, format the disk and then transfer it back on.

---

### Post by oldfred on 2014-01-28
Windows always installs all boot file to the one primary partition with the boot flag or active partition. And it uses the drive set as default in BIOS for boot files into primary partition. 
So if you have two Windows installs that is why BCD will show other Windows installs and grub will only find one Windows install as only one has boot files.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by thelost on 2014-01-28
much appreciated. there should be more than enough there to sort me out. i'm not really looking to keep the old windows install on the second drive, it was more a case of migrating data over safely once I was sure everything worked.

---

