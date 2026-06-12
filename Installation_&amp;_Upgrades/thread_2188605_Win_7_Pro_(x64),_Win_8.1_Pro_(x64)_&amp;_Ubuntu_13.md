---
title: "Win 7 Pro (x64), Win 8.1 Pro (x64) &amp; Ubuntu 13.10 (x64)"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by 0xygen on 2013-11-18
Hello people,

Firstly, apologies if this has been asked already but the only solutions I have found don't seem to be on an option for me. Having successfully installed Windows 7 onto a 1TB disk, I shrunk that partition to 250GB, then installed Windows 8.1 next to it and shrunk that to 250GB. That all went smoothly and my plan is to use the remaining 500GB for Ubuntu 13.10. When trying to install Ubuntu I ran into problems in that it did not recognise any of my partitions and the only option was to "Erase & use entire disk" or "Something else" (which only gave me the option of erasing the entire disk. I see a lot of people talking about UEFI which is a feature I just don't have - what I do have is a pretty much locked down/restricted BIOS as it's an old Dell Studio 540 system:

Intel (R) Quad (TM) 2 Quand CPU Q6600 @ 2.40GHz
6144MB DDR 2 Memory
Western Digital 1TB (WD10EARS-00Y5B1)

I saw a suggestion about trying to sort this out using GParted when running Ubuntu live but that seems to have screed up the boot partitions beyond repair which is very frustrating but you learn by trial and error I guess.

Would this have worked had I installed Windows 7, then Ubuntu, and finally windows 8.1? Or, would using any older ditro of Ubuntu more likely yield a successful result? Is it possible to install UEFI to replace my BIOS? I know that the motherboard is manufactured by AMI - if I could find out that exact model, might they have a BIOS version available that isn't locked down and therefore I'd need to flash the BIOS or is that just a really bad idea? I found somewhere that disabling fast boot (a feature that I actually can enable/disable) in my BIOS but it didn't make any difference.

Whilst it would be great to have then all on the same disk, would it simply be easier to put Windows 8.1 on a separate disk (as this is what is causing the problems - I have had Ubuntu alongside Windows 7 before and it was absolutely fine.

Any input/suggestions would be great.

Thanks,

-0xygen

---

### Post by fantab on 2013-11-18
I must say, you have 'shrunk' a lot.

Your problem with Ubuntu not installing was probably becuase you did not create space for Ubuntu. Ubuntu's installer must see either EXT4/Linux filesystem or just 'unallocated space'. Ubuntu will NOT install on NTFS.

When installing two versions of Windows, it is a good idea to install the older Windows version first, that is you did the right thing by installing Windows 7 then Win8. However, I must ask , why do you need two versions of Windows?

Anyways, to install Ubuntu and other OS, format and create your partitions on HDD in advance.
Here's what I'd do if I were you:
```
100GB NTFS PRIMARY Windows7 C:
100GB NTFS PRIMARY Windows8 C:
300GB NTFS PRIMARY Windows D: [for both Win7 and Win8, also this can be shared with Ubuntu]
500GB EXTENDED
25GB EXT4 LOGICAL Ubuntu / [for ubuntu system files]
25GB EXT4 LOGICAL Free 
7GB SWAP
443GB EXT4 LOGICAL /home or just 'free' for linux DATA.
```

Install Windows FIRST. You can tell windows installer where to install each Windows.
Install Ubuntu. Use 'Something Else' option to manually guide your Ubuntu installation. 
Select the first 25GB Parition, check Format, Use as= Ext4, Mountpoint=/
If you want to use the 443GB partition as /home then use Mountpoint=/home, use as=Ext4.

You can use Gparted from the Ubuntu DVD/USB to setup your partitions. When installing Windows reformat the partitions as NTFS with Windows installer, and like wise reformat EXT4 partition with Ubuntu installer.

EDIT: No you don't need UEFI.

---

### Post by oldfred on 2013-11-18
Only motherboards with i-series Intel chips may have UEFI. And early UEFI does not work well.

You probably ran into the 4 primary partition limit. Windows likes to have a separte boot partition. Not sure if both installs then used the same boot partition, I think they have to as boot flag determines where all boot files go. But if you have another partition that would be all 4.
You can install Windows without separate Boot partition but have to create NTFS partition first, and have boot flag on that partition.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[URL="http://ubuntuforums.org/showthread.php?t=1271600"]http://ubuntuforums.org/showthread.php?t=1271600

[/URL] This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Note in your case you have both Windows 7 & 8 boot files in one boot partition. You probably need to make both a Windows 7 repairCD and a Windows 8 repairCD so you can separately repair each. If you just delete Boot partition you will not be able to boot either.
[URL="http://ubuntuforums.org/showthread.php?t=1271600"]
[/URL]

---

### Post by fantab on 2013-11-18
[QUOTE=oldfred] Not sure if both installs then used the same boot partition,[/QUOTE]

Windows that is installed second takes control of the boot, and AFAIK it will boot from its own partition. And it will put 'boot' flag on its own c: partition.
[http://www.howtogeek.com/74335/how-to-dual-boot-windows-7-and-windows-8/](http://www.howtogeek.com/74335/how-to-dual-boot-windows-7-and-windows-8/)

---

### Post by 0xygen on 2013-11-18
Thank you for your replies, very helpful! The reason for two versions of Windows is work really - I hate Windows 8.1 but have to know how to use it. The partitions I had were the MBR, the two NTFS ones for Windows but the remaining 500GB was not allocated i.e. free space, on which I would have made a swap partition and then ext4. The issue was that Ubuntu couldn't recognise anything on the drive at all. I will carefully read over all of your replies again and check out the links...etc and have another crack at it.

I should have mentioned in my original post, I did use Partition Magic to shrink Windows 7 and dedicate 250GB to Windows 8.1 as the disk management in Windows 7 would only let me go as far as 400GB (roughly), even after a defrag. Could this have messed it up?

Thanks again people :)

-0xygen

---

### Post by oldfred on 2013-11-18
Several things can cause issues.
Was drive ever RAID or gpt partitioned? That can leave extra data that interferes.
Is Windows hibernated or not rebooted so it can run chkdsk after a resize. 
And Windows 8 is always hibernated. So you need to turn fastboot off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

    

Post this:
sudo fdisk -lu
sudo parted -l

---

### Post by 0xygen on 2013-11-20
I ended up installing Windows 7 Ultimate and Ubuntu 13.04 on the same disk - no problems there. I then put Windows 8.1 onto a separate disk. A bit of a cop out but after the system completely failed to boot and I couldn't fix it I didn't want to waste another 6 hours doing something that could go wrong again.

I will read more into this and fully appreciate all of your replies :-)

-0xy

---

