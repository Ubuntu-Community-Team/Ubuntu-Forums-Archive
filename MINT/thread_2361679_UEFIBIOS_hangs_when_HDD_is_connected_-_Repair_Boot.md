---
title: "UEFI/BIOS hangs when HDD is connected - Repair Boot Loader?"
date: 2017-05-19
forum: MINT
---

### Post by g-zindel on 2017-05-19
Hi to everyone. who reads this.

I have a problem with my system. All of a sudden, it does not boot any more. It already stops booting, right after showing the ASUS UEFI/BIOS screen, which tells me to press DEL or F2 to enter the UEFI, but even if i do this, nothing happens.

My analysis so far:
- With all peripherals disconnected (except display to see something :-) ) the effect is still there.
- When i disconnect the internal SATA-HDD, the system is able to boot from Live DVD or USB
  -> i think, the HDD is the problem (it contains a dual boot Windows 10, Ubuntu (Mint at the moment) and a data partition
- i already bought a HDD to backup the whole HDD by using dd a week ago, but i did not backup the whole HDD yet (but i have the critical data on another HDD, so its only the systems installation, which is at stake...). When i connect this new HDD at the same connector as the System-HDD, the system still boots, so it seems not to be a problem of the SATA-port.
- i then bought a 3,5'' external case for the System-HDD and connected it after booting an Ubuntu-Live-DVD using the USB cable. Voila, i can see all partitions using gparted and i can access the data (as far as i have seen)
- now i thought, i could just copy the data using dd copying the whole disk to the new disk. but after starting the copy-task in the evening and going to the computer in the morning, i saw some error messages, which i dont remember in detail, but it started with error messages after copying about 560 of 1000 GB, so the boot sector should have been copied as far as i know, so i tried to boot from the new disk now...
- booting from the new disk showed the same effect as with the old disk, the UEFI hangs before i can do ANYthing
- ut now i had a solution again, i put that new disk in the external housing, started ubuntu from a live-USB and erased all partitions from the disk using gparted and now after a reboot, the HDD does no longer stop the UEFI from booting

So my conclusion is, that there has to be something on that HDD (most likely in the boot area), that stops the UEFI from working. i would like to repair that, but i am no professional in repairing a boot-sector. So i tried using the tool boot-repair, but it did not bring any positive or negative effect. I have a boot-info, created by the tool and could upload it here, if it helps and someone likes to help.

Any ideas on how to fix the problem without having to reinstall all systems from scratch would be very helpful.

Thank you for reading until here :-)
Best regards
Gunnar

---

### Post by oldfred on 2017-05-19
If UEFI, there is not a MBR, but an ESP - efi system partition. That is a FAT32 formatted partition with the boot flag.
And you use gpt partitioning.

With gpt best to only use dd with an entire drive and dd is only for same size to same size drives. Once copied you cannot connect both drives as you have duplicate UUID & GUIDs creating conflicts. Some changes may actually be on one drive and some on the other drive make both unusable.

And with UEFI when you disconnect a drive, UEFI loses the entries in its NVRAM for booting. Most will rediscover entries in the ESP, but some need you to run efibootmgr to add entries back into UEFI.

From Ubuntu live installer add Boot-Repair ppa:
       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by g-zindel on 2017-05-19
Hi and thank you for your reply, oldfred

i fear, i dont understand everything you wrote, as i am not familiar with all the abbreviations, you used. But i try to answer.

I think, my HDD has a MBR, at least, that is, what i read from the logs of my boot-info (see [https://paste2.org/wd6JHAgW](https://paste2.org/wd6JHAgW)) 

I wanted to do a dd for an entire disk, and i have two identical disks to do that. So there should not be a size problem during backup.Thank you for the information, that i should not connect both disks after copying the main disk, i did not know that yet.

So i gave my info about the boot-info at [https://paste2.org/wd6JHAgW](https://paste2.org/wd6JHAgW)  . If you can read something from that, that helps, i would be very happy.

For more info: 
- sda is the empty new disk of the same size as my system-HDD
- sdb is the live-ubuntu-USB-stick
- sdc is my system-HDD, that causes the problem during startup

---

### Post by oldfred on 2017-05-19
You have Mint, so moved to MINT sub-forum.

And you do have BIOS boot with MBR partitioning.

dd is not for beginners. Its nickname is data destroyer.
 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
"I have become dd, the destroyer of data." Unix Proverb 
[https://en.wikipedia.org/wiki/Dd_%28Unix%29](https://en.wikipedia.org/wiki/Dd_%28Unix%29) 

Your sda is only slightly shown as having grub installed to partition boot sector. Or as if corrupted or defective.

SATA port order can be important. I found that drive order can change when rebooting with my sdf flash drive and it became sdb. It was because I skipped a SATA port. So keep main working drive in SATA0 or first port, check manual if order not clear. And plug hard drives into motherboard in SATA port order.

With multiple drives do not run Boot-Repair auto fix. That installs grub to all drives and you only ever want grub installed to same drive as Ubuntu install unless you want another drive as default for boot. But rarely want all drives to have grub boot loader. I think Boot-Repair does that for those that do not know or know how to change BIOS to boot correct drive. Boot-Repair's advanced mode lets you choose an install and a drive for boot loader.

---

