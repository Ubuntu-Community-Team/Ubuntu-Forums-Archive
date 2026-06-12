---
title: "Stuck on 'Grub Rescue' while upgrading to Windows 10 from Windows 7"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by Rinjo on 2015-08-04
Hi All,

I was running Ubuntu 14.10 and Windows 7 as dual boot on my HP Pavilion G6 laptop. 
With the new Windows 10 update being provided for Windows 7 users I too opted to upgrade to Windows 10.
Initial part of the upgrade went fine till Windows was copying all the required files and then trouble.
It looks like Windows 10 installer deleted the grub and now while booting I am stuck in 'grub rescue' prompt!

I have gone through some other posts in this forum that tell about using either 'Boot-repair' cd/dvd to repair the grub
or boot into Windows 7 boot disk do a fixmbr. However, none of these options are currently working for me. 

My system is not listing cd/dvd drive or usb as one of the devices to boot from in the boot menu.
I have changed the BIOS settings for both Legacy and UEFI to boot from internal cd/dvd and usb, but this did not help.
The only options that I am getting on the boot menu are 'boot from efi' and 'boot from hard disk'! :(

I need to get my system to boot from the cd/dvd or usb to fix the mess caused by the Windows 10 installer... :mad:
Can anyone let me know how fix this issue?

regards,
Rinjo

---

### Post by oldfred on 2015-08-04
Is Windows & Ubuntu in UEFI boot mode or BIOS/CSM boot mode?
You cannot change back and forth. You must stick with which ever mode your system is booting as that is the only one that will work.

Some systems get confused with too many reboots. Sometimes a full power off or cold boot resets UEFI so you can get into UEFI or reset to use other devices. Some even had to open system and jumper reset pins.

Is secure boot off?

Only if you have a bootable DVD or bootable flash drive plugged in will it offer to boot that device.

HP has always had issues booting Ubuntu. They modify UEFI to also use description. If you were dual booting, you either modified some files in ESP - efi system partition or installed Ubuntu in BIOS mode and only switched boot modes using UEFI boot menu.

We really cannot help without knowing more about your system configuration.

---

### Post by Rinjo on 2015-08-05
Hi Oldfred,

Thanks for your quick reply. I will check the BIOS settings that you mentioned in your reply once I am back home.
Hoping that with those changes I will be able to boot on the cd/dvd or the usb.

Keep fingers crossed...

--Rinjo

---

### Post by Rinjo on 2015-08-05
Hi Oldfred,

Thanks for you suggestions. I was able to disable 'secure boot' in BIOS and was able to boot using a boot-disk.
From the boot disk I was able to boot into the windows partition and complete the Windows 10 installation that had got stuck half way.
Windows 10 installation was successful, but after completion it delete the grub completely and I can only boot into Windows 10 now! :(

Please let me know the steps for get the dual boot back...
If I a get into Windows command prompt and do a fixmbr, will the UEFI loader be able to recognize my Ubuntu installation?

regards,
Rinjo

---

### Post by oldfred on 2015-08-05
Did you make good backups of your data in the Linux partition(s)?
Windows update has worked for many, but a few are having major issues.

You may just need to restore grub to MBR, or Windows may have re-written MBR partition table without the Linux partition. 

Best to see details before you make any more changes.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

