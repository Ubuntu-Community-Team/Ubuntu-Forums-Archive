---
title: "Ubuntu 14.04 64bit setup doesn't get to GUI"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by abhinav5 on 2014-06-15
I recently built a new desktop, with the following config:
Core i7 4690
Asus Z97 Pro motherboard
NVIDIA GTX 770
256GB Samsung Pro SSD connected to the onboard ASMedia SATA controller
4 x 3TB HDDs on RAID5 connected to the onboard Intel SATA controller (SATA mode set to RAID)
SecureBoot is disabled, and the Platform Key is unloaded. The mode as reported by the BIOS is 'Windows UEFI'

I'm trying to dual boot the system with windows 8.1, with Ubuntu to be installed to an unallocated region on the SSD. 
I've tried starting the installer in both UEFI and legacy modes. In both cases the installer doesn't get to the GUI. I've tried combinations of nomodeset, nodmraid, acpi off, all to no avail. The last error message I'm able to see (when quiet and splash params to the kernel are removed) is that Ubuntu is unable to restore SATA connection after discovering USB devices, SStatus and SControl both being set to FFFFFFFF. The system tends to become unresponsive after this. I've also tried 13.10, 12.04.4 as well and both face similar issues. 

Can anyone suggest a solution here?

---

### Post by JohnAreBee on 2014-09-19
Have you tested the install media (USB, DVD) and RAM? If you can try it out on another, or a few other machines, and see if you can get into the installer.

Make sure you are running the latest motherboard firmware, [as of this post the latest is 1304.]("http://dlcdnet.asus.com/pub/ASUS/mb/LGA1150/Z97-PRO/Z97-PRO-ASUS-1304.zip")

Disable the onboard gfx, or set the GTX 770 as the primary. I am not sure how your BIOS is setup, but if it is one of those with that dumb Lucid MVP stuff disable that also, it's a waste.
There is quite a few options in BIOS if not set correctly can cause issues, so go threw it and double check your settings.

Disabling the ASMedia controller will most likely solve your issue, but I have had a lot of experience playing with Ubuntu and tons of different HDD, SDD, RAID, and JBOD configurations so here is some info that may help you to make a decision. Now ASMedia controllers are know to be buggy as all hell, they can cause all sorts of issues and it is best to even disable them in the BIOS, but if you have to have the additional SATA slots, I would definitely not use the ASMedia SATA as boot controller.

***NOTE that the ASMedia SATA Channels do not support ATAPI so Optical Drives will not work either, disabling the channels all together is your best bet.***

I looked at your motherboard specs, and you should connect all your drives to the Z97 chipset SATA Channels 1-6. Connect your SSD to SATA6G_6 and setup a RAID with the 4 remaining 3TB disks. This does not mean that you have to put the SSD in the RAID array, just think of it as connecting SSD to a RAID controller but using it as a single drive.
    
Why use a RAID5 on a fake RAID, performance is terrible. Fake RAIDs are really only good for 0, 1, or 10. Now its your machine and you do what you think is best but I would not run a RAID5 on fakeraid. With fakeRAID5 you CPU is going to be doing all the work, it just doesn't make sense from a performance point of view and they are much much slower than real RAID5 hardware controller.

Here are the 2 options I would suggest. 

    
[LIST=1]
[*]Have your SSD in the SATA6G_6 channel, and your 4 - 3TB drives on SATA Channels SATA6G_1, SATA6G_2, SATA6G_3, and SATA6G_4. Go to your RAID utility make sure the SSD is set as Non-RAID Disk, and that your 4x3TB array is picked up correctly. Then make sure you set the correct hard drive priority list and boot list in BIOS so it boots from the SSD. 
[*]Have the SSD and the 3TB drives in the same channels as option 1, but this time include the SSD in the array. You should be able to (not completely sure it has been a while since I have used Intel fakeRAID) set the SSD to accelerate the 4drive RAID5 array under Acceleration options. That will make up for the very poor performance of Intel RAID5 how much performance will it make up, couldn't tell you gonna have to test to find out. 
[/LIST]
 
There are so many different combinations you can setup, but as long as you disable ASMedia controller you should be fine. Then you can play around with different setups and what not to figure out what combo performs the best for the work you do.

---

