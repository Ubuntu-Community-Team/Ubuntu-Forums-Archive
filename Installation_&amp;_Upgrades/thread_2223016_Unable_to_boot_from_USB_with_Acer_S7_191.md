---
title: "Unable to boot from USB with Acer S7 191"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by eren-canpolat-t on 2014-05-09
I'm trying to install Ubuntu 14.04 (64 bit) on my Acer S7 191 which came with Windows 8 preinstalled (and was recently upgraded to 8.1).


[LIST]
[*]I disabled the fast boot option in Windows. 
[*]I disabled the secure boot option in the BIOS. 
[*]I changed the boot order in BIOS and now booting from USB is the highest in the list. 
[*]The boot mode is UEFI. 
[/LIST]

When I try to boot from USB, I see the Acer logo reloading in an infinite loop. It feels like it's trying to boot from USB but failing and retrying (no error logs visible). When I change the boot mode to "Legacy", I can boot Ubuntu from USB. But, I'm afraid, if I install Ubuntu in legacy mode, it will break my Windows installation. Because [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) says: "if the other systems (Windows Vista/7/8, GNU/Linux...) of your  computer are installed in EFI mode, then you must install Ubuntu in EFI  mode too." There is a section in that document describing "Converting Ubuntu into EFI or Legacy mode" Would you recommend installing Ubuntu in legacy mode and then converting it to EFI afterwards (is it a proper solution)? 

Note: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) points out this is the correct forum to post such issues. I previously posted the issue at [http://ubuntuforums.org/showthread.php?t=2222665](http://ubuntuforums.org/showthread.php?t=2222665) but didn't get any response. So, please fell free to delete that thread since this one explains the problem in more detail.

---

### Post by eren-canpolat-t on 2014-05-09
I went ahead and tried installing Ubuntu in the legacy mode. After selecting the partitions for the root and the swap, I clicked the "Install" button. Then, I was presented wth the following very helpful dialog box:[http://imgur.com/ujTQy0TNow](http://imgur.com/ujTQy0TNow), even after switchiing back to UEFI mode, I'm not able to boot Windows. I guess something is seriously corrupted in the SSD.Help is really appreciated at this point. It looks like everything is broken now.

---

### Post by oldfred on 2014-05-09
From your flash drive installer in live mode. Post link to BootInfo report so we can see details.
You need to have UEFI on or BIOS mode off to boot Windows. And have BIOS mode on, UEFI off to boot Ubuntu. Some systems auto switch, others require you to channge settings each time.
Secure boot would have to be off.

Did you use Windows to shrink the NTFS partition before install and reboot. It has to run chkdsk after any resize to the NTFS partition. So you need to use f8 or a Windows repair flash drive to fix Windows.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by eren-canpolat-t on 2014-05-09
Hi,Thank you for the  response.Yes, I did the shrink from within Windows 8.1. And when I booted Ubuntu, it showed up as unallocated.That was before I decided to wipe the Windows and install Ubuntu on the whole disk due to all these boot problems. Now, it looks like I have a bigger problem: the partition tables seem all messed up and I have no idea what to do.Here is the output of Boot Repair: [http://paste.ubuntu.com/7422180/](http://paste.ubuntu.com/7422180/)

---

### Post by eren-canpolat-t on 2014-05-09
And when I try to launch gparted, I get the following error during launch; The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.

---

### Post by oldfred on 2014-05-09
Is this an UltraBook? With Intel SRT which looks like RAID to Linux?

You need to turn off the Intel SRT and remove the RAID settings. Change to AHCI.
Some have a bit larger SSD for the SRT and just use it as / (root) and put /home or data partitions on the rotating drive.

Your boot info did not show hard drive. The 2048 sectors I have seen once or twice and they were a major issue.

       Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

    
I would totally repartition using gpt partitioning on both drives.
Does this show anything? May have to have removed RAID settings on drive first.
 sudo parted -l
or download gdisk
      
 sudo gdisk -l /dev/sda
            sudo gdisk -l /dev/sdb

    
More info in link in my signature.

---

### Post by ubfan1 on 2014-05-09
I think the RAID is the problem, but I don't know much about it.

---

### Post by eren-canpolat-t on 2014-05-09
Hi,

Yes, it's a Ultrabook with Intel SRT.

I can go into the Inter SRT menu, but I don't see how I can turn it off. I see 6 menu options:

1. Create RAID Volume
2. Delete RAID Volume
3. Reset Disks to Non-RAID
4. Recovery Volume Options
5. Acceleration Options
6. Exit

---

### Post by eren-canpolat-t on 2014-05-09
I wen't for the "Reset Disks to Non-RAID" and could install Ubuntu on one of the physical hard disks (there were two 64GB SSD disks). Thanks for the help.

---

### Post by lehnert66 on 2014-07-31
> **eren-canpolat-t said:**
> Iwebt for the "Reset Disks to Non-RAID" and could install Ubuntu on one of the physical hard disks (there were two 64GB SSD disks). Thanks for the help.

Hi. Just found this topic and I just now sit with the exact same problem, trying to install Ubuntu 14.04 on an Acer Aspire S7 with Raid 0 SSD drives. Can you explain in a bit clearer "earthly" words how you solved it, step by step? I'm not a pro when it comes to install Linux Ubuntu... :-) A step by step explanation without technical terms or short frases will help me out for sure.  Thanks in advance.

---

### Post by eren-canpolat-t on 2014-07-31
> **lehnert66 said:**
> Hi. Just found this topic and I just now sit with the exact same problem, trying to install Ubuntu 14.04 on an Acer Aspire S7 with Raid 0 SSD drives. Can you explain in a bit clearer "earthly" words how you solved it, step by step? I'm not a pro when it comes to install Linux Ubuntu... :-) A step by step explanation without technical terms or short frases will help me out for sure.  Thanks in advance.
First: I ended up wiping Windows and installing Ubuntu alone. It has been a while, but according to the log here, it looks like I entered the [COLOR=#000000]Intel SRT menu and selected "[/COLOR][COLOR=#000000]Reset Disks to Non-RAID". Several guides prepared by [/COLOR][COLOR=#000000]**oldfred** helped me a bit (I remember finding them a bit confusing at the time). Sorry for not being able to help much, I hope you can solve the problem. By the way, have you tried updating your BIOS? I reported the "[/COLOR][COLOR=#000000]Acer logo reloading in an infinite loop" to Acer and they claim they have fixed the issue with a new BIOS firmware.[/COLOR]

---

### Post by lehnert66 on 2014-07-31
Figured out how to shut off Raid as described and managed to install Ubuntu 14.04.1 LTS now. The combi with this computer and the Ubuntu is absolutely killer! :-) Thanks for your post and help. :-)

---

