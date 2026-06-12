---
title: "Installing Ubuntu on an SSD partition (dual-boot)"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by cestevez on 2014-04-21
Every time I have a problem usually someone has had the same problem before and I find the solution immediately, so I'm a bit surprised that no one (that I could find) has ran into this problem. So I have to conclude it is something that rarely occurs. I'd like to mention this from the get go.

I purchased this new laptop with fairly nice specs (Core i7, 16 GB RAM, 250 GB SSD, 750 GB HDD). As you would imagine the OS is in the SSD and the data in the HDD. I downgraded from win8 to win7 and immediatelly made a partition to dual-boot ubuntu. The problem is that when I pop in the Ubuntu CD (or any Linux distro for that matter) it does not "see" the SSD partitions. It just sees the whole drive, so I could wipe out the whole drive and install Ubuntu (I think), but I cannot install it on the partition. I did a separate gparted CD (not ran from the Ubuntu CD) just to see if gparted saw the partitions, same problem, it just sees the whole drive. I don't know why I did this last step, just some desperate wishful thinking.

I don't know if the problem is SSD related or something else. My first reaction was to blame the SSD detection (old Ubuntu disk), but after burning 13.10 had the same problem (BTW, I just saw that 14.04 came out). When I downgraded to win7 I had to play a bit with the BIOS (EFI settings), so all those settings are now disabled (so this shouldn't be the problem, i guess). I'm not sure what additional information can be of use. Win7 works fine, I can see the reserved Ubuntu partition, I could even store files there if I needed to. As I have not been able to reach it via Linux, it is still formatted as NTFS, but I always install windows first then Linux to have the boot manager be Linux. The HDD only has one partition, so I cannot see if the HDD will experience the same problem. As of now it is already kind of full so testing this would require a lot of backing up (not sure if I have enough space elsewhere), I will like to avoid this, if possible. 

Any theories? ideas? suggestions? vague guesses?
Anything would be helpful.

Thanks in advance for your help,
CE

---

### Post by oldfred on 2014-04-21
You used a Windows 7 DVD which is BIOS only. 
So installing Windows 7 converted drive from gpt to MBR(msdos), but Windows does not correctly convert drive. It leaves the backup gpt partition table and Linux tools then seem MBR & gpt and do not know what to do except totally redo it.

You can either convert Windows 7 DVD to flash drive and make some changes to make it a UEFI installer since system is UEFI.
Or you remove backup gpt partition data and install Ubuntu in BIOS mode. Or install Ubuntu onto hard drive which may still be gpt.

Windows only installs to gpt partitioned  drives with UEFI boot mode.
Both Windows & Ubuntu only install to MBR drives and boot with BIOS boot mode.
Ubuntu can boot in UEFI or BIOS from gpt partitionded drives.
But you should have both Windows & Ubuntu in same boot mode for ease of dual booting.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You cannot install Ubuntu to NTFS partitions.


 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Post this from Ubuntu live installer's terminal:
sudo parted -l

---

### Post by cestevez on 2014-04-22
I will like to try the UEFI/GPT dual-boot as it will probably yield much faster boot times, but for now (quick and dirty) do you think this might work? wipe GPT/MBR mess windows made, insert windows cd in recovery mode, rebuild MBR, then install Ubuntu?

Thanks a lot for your help, this is already great news for me.

---

### Post by oldfred on 2014-04-22
If you remove backup gpt data with fixparts, you should not even have to run any Windows fixes. Windows just does not see the gpt table once installed in BIOS/MBR mode.
Then you can install Ubuntu in BIOS boot mode on SSD.
Is hard drive gpt or MBR?

I do like to have a bootable install on every drive. I have my working installs of Ubuntu on my SSD, but have actually have several test installs that all work on my data drive. 

I like this logic.
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs on all larger drives.

---

### Post by cestevez on 2014-04-23
Got it! Thanks! Will try and post back once solved.

---

### Post by cestevez on 2014-07-16
Yes! I finally got around to do this and your second post did the trick. Thank you very much!!!

---

