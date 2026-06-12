---
title: "Dual boot w/possible GPT Drive? How?"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by cubdukat on 2012-12-19
I recently bought an Asus X75VD laptop with Windows 7 64-bit preinstalled. The disk is partitioned in the following way (also refer to enclosed pic):

1. 25MB (EFI System Partition)(GPT?)
2. 280GB (C:, OS--Windows 8)
3. 394GB (D:, Data)
4. 25 GB (Restore Partition)

What I am looking to do is install Ubuntu 12.10 64-bit so that I can get the dual-boot system I had on my previous laptop.

My question is this:

A. Can it be done? 
B. Can it be done without unnecessary drama and/or voiding my warranty? 
C. In order to be able to comply with the rules about having more than four true partitions on a hard drive, will I need to consolidate the C: and D: partitions, and if so, is there any way to do so without losing the data on the D: partition?

Right now I am booting from a 16GB USB thumb drive with 800MB set aside for persistent memory, but it doesn't seem to want to cooperate. I just end up having to redo all of my settings with every boot.

---

### Post by darkod on 2012-12-19
On GPT disks there is no distinction primary/logical partitions, and subsequently no limit of 4 partitions. They are all the same type and you can create as many as you want (well, not literary, I think the limit is 128 or something).
So, you don't need to worry about that.

For creating successful uefi dual boot you have to make sure to boot the ubuntu cd/usb in uefi mode, not legacy mode. I don't use uefi so I can't give more details. Refer to the documentation for more info:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In any case you will have to shrink one partition to make space for ubuntu. Use only windows Disk Management to do that, not the ubuntu installer.

---

### Post by cubdukat on 2012-12-19
Okay, I just did the test with Ubuntu Secured, and I checked the BIOS. It looks like I have a hybrid EFI. It has an option for UEFI boot, and when I set it up to boot from a thumb drive, that shows up as an option, but it doesn't offer that for the optical drive. 

I'm going to gather together the backup DVD's ASUS had me make when I bought the laptop, then I have to find a way to backup my Windows 8 install, then I'm going to shrink a 25GB portion of the D: partition and attempt to install.

When it asks me where to put the bootloader, which partition should I use: the first EFI partition or the C: (OS) partition? And how hard is it to go back if I screw something up?

---

### Post by cubdukat on 2012-12-19
I just thought of something else. I currently have a 32GB SDHC card, and there's an option to boot from that as well. Could I treat that like a regular hard drive and use that to install 12.10 and dual-boot with that?

---

### Post by oldfred on 2012-12-20
Is this Windows 7 or Windows 8. Computers with 8 have secure boot that complicates it. Those with Windows 7 do not have secure boot and then with no limit on partitions it is easy to install as long as you install in UEFI mode. Only the 64 bit version of 12.10 works from a flash drive.

Also turn off fast boot in UEFI/BIOS.

After shrinking Windows reboot a couple to times for it to run chkdsk and update to its new size.

Grub has a bug and does not create a correct chain load entry to Windows but Boot-Repair can fix it.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
I have yet to see anyone install a full UEFI install to a flash drive or memory card. Only a few new computers will boot from memory cards.

I have BIOS and as a test I created gpt partitions on my 16GB flash drive, did a full install,  and it boots Ubuntu just fine. But you would have to both use gpt partitions and install in UEFI mode.
That would be more like an install to two drives as memory card is just another drive.
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by cubdukat on 2012-12-22
Unfortunately things have gone from bad to worse. I shrunk a 35GB section of my D: drive to put Ubuntu onto, but Win8 still won't see it. Now, using EasyBCD I have rendered my system unbootable in either OS, so I am looking at trying to repair the Windows side so that I can uninstall EasyBCD and give it another try. 

I also have reason to believe that I may have flashed my BIOS so that any option to disable Secure Boot may have been hidden. I am hoping that this is not the case.

Here's the report from boot-repair. Unfortunately when I try to run it, it gives me a "grub-efi purge cancelled" error. That's what leads me to believe that Secure Boot is enabled.

[http://paste.ubuntu.com/1457857](http://paste.ubuntu.com/1457857)

---

### Post by oldfred on 2012-12-22
You installed in BIOS mode as you have grub in the MBR. With gpt partitioning there is a protective MBR just so old partition tools see that the drive has gpt. There is only one partition entry but there is room to put a boot loader in the MBR. I use that as my system is BIOS only.

If looks like your Windows still has its efi files in the efi partition. But you would have to boot from UEFI with UEFI turned on, not in BIOS/Legacy/AHCI mode.

You need to boot the Boot-Repair in UEFI mode. If system was originally Windows 7 it probably does not have secure boot, but will have settings for UEFI and legacy boot. 

Not sure about EasyBCD. There is little reason for it with UEFI booting as both Windows & grub coexist in UEFI partition. But grub will chain load back to Windows efi so from grub it is easy to dual boot. EasyBCD wants grub installed to a partition which is not really a UEFI install.

---

