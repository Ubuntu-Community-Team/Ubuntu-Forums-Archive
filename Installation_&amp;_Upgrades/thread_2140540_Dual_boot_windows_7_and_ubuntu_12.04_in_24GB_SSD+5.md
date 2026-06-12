---
title: "Dual boot windows 7 and ubuntu 12.04 in 24GB SSD+500GB HDD"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by deepla on 2013-04-30
HI 
Is it possible to dual boot Windows 7 and ubuntu in 24GB SSD+500GB HDD ultrabook  (lenovo u310)? Most of the posts describe about SSDs that are about 128GB. If it is not possible to put both in SSD ,which would be better ? Windows in ssd and ubuntu on hdd or ubuntu on ssd and windows on hdd ? 

This is for my friend and he uses at present windows mostly but would be shifting to Ubuntu mostly after sometime. Should i choose the option " install ubuntu alongside windows " when i install ubuntu ? Where should I store the boot grub.

Thanks in advance
Deepla

---

### Post by carl4926 on 2013-04-30
There isn't much left on the ssd if windows is there. Even if you only put / of ubuntu on the ssd
How much space is free on the ssd
Which do you use more win or linux?

---

### Post by fantab on 2013-04-30
What are the system specs? Does it have UEFI enabled? Did Windows come pre-installed? Which is your FIRST boot device, HDD or SSD?

With only 24GB SSD you have very limited options. You cannot install Windows on ONLY 24GB, it needs a minimum of 40-50GB for optimal run. But Ubuntu can run beautifully with 24GB. Grub shoud be installed to the Disk which has Ubuntu.

---

### Post by oldfred on 2013-04-30
UltraBooks do not have anything installed on the SSD. It uses Intel SRT and RAID (somehow) to cache Windows on the SSD to make Windows faster.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

Some install Ubuntu / (root) into SSD and make Ubuntu fast but then cannot use Intel SRT. Some turn off SRT  (and remove RAID from drives), install Ubuntu into hard drive and then turn SRT back on. It just depends on whether you want Windows or Ubuntu to be the quicker system.

 Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by deepla on 2013-05-02
Thank you carl4926, fantab and oldfred for your replys. 

This is a lenovo ultrabook U310 with 3rd gen core i3 , 4GB ram , 500 GB HDD and 25 GB SSD. It came with windows 7 home basic preinstalled. C drive is in the HDD and is the only partition there. SSD has some lenovo drivers and nothing else ( when the drive is opend in windows). SSD is sda and HDD is sdb. sda1 is 4 GB and sda2 is 18.3 GB. This is what gparted shows when i boot from a ubuntu bootable usb drive. The devices that are shown in nautilus are System, Windows and Lenovo. UEFI is enabled. He will be using mostly ubuntu if i can set it up....

---

### Post by fantab on 2013-05-02
Enter the BIOS setup and check it there is "Secure Boot" (I doubt it has since its Win7). Most importantly you will look for SATA mode and check it has RAID enabled...  also check if it has "Intel SRT" and is it enabled. It will be difficult to install Ubuntu with both RAID and especially with Intel SRT enabled. Read more about this from the link oldfred gave you in post #4

---

### Post by deepla on 2013-05-02
Thank you fantab,
I will check about secure boot. I went through some of the links oldfred gave and see that i need to disable iRST and change SATA to AHCI . iRST is at present enabled and SATA is in RAID mode. I also understand i need to get bootrepair done after installiing ubuntu. My question is with the above mentioned changes to AHCI and iRST, will i be able to install ubuntu to SSD and expect the original windows 7 to be intact ? If i can save it that would be good. The warning in one of the posts that, if original OEM is removed that would void the warranty , makes my friend somewhat uneasy.If there is no other go we are willing to do a clean install of windows. If I install ubuntu to HDD (normal), would it disturb the windows 7 ? ( i know that it would be slow to boot , that is ok as long as it is working).....

---

### Post by fantab on 2013-05-02
I haven't personally dealt with RAID, so I ain't the guy to guide you with that.  But it changes to AHCI. And you have to disable ISRT. Wait for more confirmed response to this.

No, Installing Ubuntu to HDD will not disturb Windows... Why don't you talk to the ultrabook "customer support"? and tell then that you want to install Ubuntu/Linux along with Windows and listen to what they have to say.

---

### Post by oldfred on 2013-05-02
Backups are always a good idea. Then you can restore system. A few users accidentally overwrite entire drive including recovery partition or otherwise damage recovery partition and cannot restore from that.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by deepla on 2013-05-04
In the end I was able to install Ubuntu 12.04 64 bit. iRST was disabled and RAID mode of the HDD was changed to AHCI. The HDD already had 4 primary partitions. System, Windows, Lenovo and one named 'OEM partition'. I tried creating an extended partition after shrinking  the Windows partition and releasing some unallocated space. However this was unsuccessful in Windows disk management tool and gparted (run through an bootable ubuntu usb drive). So I deleted the primary partition named 'Lenovo' which had a folder named 'drivers' and another one named 'applications'. This (along with the unallocated space released through shrinking Windows partition) was used to creat an extended partition for ubuntu (ext 4) and another NTFS partion. Didn't allot any swap partition and i think i should have done it.Ubuntu installation went without any hitch. I think there was a warning saying the UEFI is enabled but no EFI partition was not found or something. I ignored it and went ahead. On rebooting it booted into Windows 7 without any sign of ubuntu. Bootrepair cd was run and this asked where Grub should be installed ? i was not sure so I installed it both in SSD (sda) and HDD (sdb). It found the windows that was in sdb 1 . Anyway everything went well and it is working now. Windows 7 is intact and ubuntu is fine. 

Thank you so much for all the help
Deepla

---

