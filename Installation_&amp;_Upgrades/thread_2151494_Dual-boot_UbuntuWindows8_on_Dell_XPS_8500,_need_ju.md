---
title: "Dual-boot Ubuntu/Windows8 on Dell XPS 8500, need just a few advices"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by veroslav on 2013-06-04
Hi,

I have a Dell XPS 8500 that came with Windows 8 pre-installed. Now I am trying to dual boot it with Ubuntu 12.04.2 and I have a few questions after having read this guide:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

1. I've changed the boot options as follows:

Secure Boot state: Disabled (Default was Enabled)
Secure Boot: Disabled (Default was Enabled)
Load Legacy OPROM: Disabled (Default was Enabled)
Boot Mode: UEFI (Default was Legacy)

Should 'Load Legacy OPROM' be disabled/enabled? What does it mean? Also, if I remember correctly, the default boot mode was set to 'Legacy'. This confuses me, as I thought that every Windows 8 install requires UEFI boot mode by default. How can I be sure that Windows 8 was installed in UEFI mode?

2. I was unable to locate 'QuickBoot/FastBoot' and 'Intel SRT' in BIOS, however I did disable 'FastStartup' in Windows 8. Are these options perhaps called something else depending on the kind of motherboard manufacturer?

I managed to boot Ubuntu Live DVD in EFI mode without problems. I've attached a screenshot of GParted showing the disk partitions. This is what I intend to do:

Shrink /dev/sda5 to around 0.5 TiB with PartitionWizard. I intend to install both Ubuntu/Kubuntu 12.04.2 so the remaining space should be split equally between them. So this means two root (/) partitions of ca 0.6 TiB each. I've got 8 GiB RAM so I intend to use only 2 GiB for swap. 

3. Can I leave the EFI partition (/dev/sda1) as is and let (K)Ubuntu use it without formatting/modifications to it? Will (K)Ubuntu installer be able to detect and use it automatically? I believe yes but I am unsure.

And that's it! Can anybody confirm that I am on the right track here? Anything I might have missed?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by ajgreeny on 2013-06-04
Well, with those partitions, none of which is an extended partition, you must have UEFI, not legacy BIOS, however, I am not sure what oprom really is, so will leave that for others to deal with.

I strongly recommend that you shrink the Windows OS partition using Windows 8's own disk manager, which I assume Win 8 still has, rather than any other third party utility, and after doing so, make sure you run checkdsk (is that what it's called?) a couple of times to ensure all is OK with Windows.

The EFI partition should (must) be left alone as it already has the files that Win 8 needs in order to boot to that OS.  Any Linux OS will find it and put its own boot files into it to allow booting of that OS as well.

---

### Post by veroslav on 2013-06-05
Hi and thank you for responding, ajgreeny.

I also suspected a EFI system but they sure do everything to confuse one. Nice to get it confirmed.

Yes, I will wait for a confirmation on whether oprom should be disabled/enabled from somebody before I do anything. Sounds like it could play some role in the whole EFI/SecureBoot issue and I want to do it right from beginning. 

I always do try shrinking it directly from within Windows but for some reason I never manage to shrink it more than half it's original size. Will give it a shot again.

Thank you very much for confirming my thoughts on EFI partition, will leave it as is.

Now I just need to get an explaination of 'Load Legacy OPROM' and I am good to go! :)

Kind Regards,
Veroslav

---

### Post by veroslav on 2013-06-05
I think I found an answer to the 'Load Legacy OPROM' boot option here:

[http://www.tomshardware.co.uk/forum/322019-30-what-legacy-option-boot-section-bios](http://www.tomshardware.co.uk/forum/322019-30-what-legacy-option-boot-section-bios)

This section specifically:

"If the OPROM format is set to "Legacy ROM" it will always use the legacy  OM on the device, if it is set to "EFI Compatible" it will use the  newer EFI ROM if one is present and the Legacy ROM if one is not."

I interpret the above as if I should disable the 'Load Legacy OPROM' option, as I always want it to boot in EFI mode (Ubuntu Live-DVD for instance).

Anyone who might confirm this?

Thanks.

//Veroslav

---

### Post by fantab on 2013-06-05
OPROM or Option ROM is. lets say 'firmware' on the MoBo. In other words its the 'legacy boot' as opposed to 'Efi boot'.

It appears that you have GUID partition table aka. GPT (I would like to see a screenshot of partitions from Windows Disk Management). Windows will not boot from GPT in Legacy mode AFAIK. If you have GPT with Windows, then it boots in EFI mode.
To confirm this post the output of:
```
sudo parted -l
``` 
from Ubuntu or Ubuntu DVD/USB.

---

### Post by veroslav on 2013-06-05
Hi and thank you for replying fantab!

I can confirm what you mentioned about Option ROM, that it is some kind of legacy boot mode. For instance, while I was launching the Partition Wizard cd, I had to have it ON, because otherwise I couldn't boot the cd. On the other hand, while I had it ON I couldn't boot Windows 8 as there was no boot entry for it in this mode.

Now the good news: I managed to dual-boot Ubuntu 12.04.2 and Windows 8 in EFI mode! So happy!! :D

For everybody who is attempting to do the same thing on Dell XPS 8500, this is what I did:

1. In the boot menu, I set the following:

Secure Boot state: Disabled (Default was Enabled)
Secure Boot: Disabled (Default was Enabled)
Load Legacy OPROM: Disabled (Default was Enabled)
Boot Mode: UEFI (Default was Legacy)

2. Disabled 'quick start' from within Windows 8
3. Defragmented Windows 8
4. Used 'Partition Wizard' to shrink Windows 8 partition
5. Rebooted Ubuntu 12.04.2 Live-DVD in EFI mode
6. Chose 'Something else' in the installer (for some reason the installer didn't detect Windows 8 at this point)
7. Created new root (/) partition and swap
8. Installed Ubuntu
9. After first reboot, it went straight to Ubuntu with no option to boot Windows 8
10. Installed boot-repair in Ubuntu and ran the default repair option
11. Rebooted and I could now choose between Windows 8 and Ubuntu (verified that both boot without issues)

Now the next goal is to install Kubuntu 12.04.2!

Thank you all.

Kind Regards,
Veroslav

---

### Post by fantab on 2013-06-05
Great. Now mark the thread as 'Solved'.

---

### Post by veroslav on 2013-06-06
Done! Also installed Kubuntu without issues :)

Thank you.

//Veroslav

---

