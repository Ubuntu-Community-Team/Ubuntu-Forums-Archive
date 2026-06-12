---
title: "After clean install, grubbed up"
date: 2019-12-03
forum: Installation &amp; Upgrades
---

### Post by C.Snyder on 2019-12-03
This is a continuation of my "unmet dependencies" thread [https://ubuntuforums.org/showthread.php?t=2429054&page=3&p=13903890#post13903890](https://ubuntuforums.org/showthread.php?t=2429054&page=3&p=13903890#post13903890)

**Impavidus and rsteinmetz**....

For the last few weeks I have been attempting to eliminate possible hardware issues that might be preventing the reinstall of 16.04 in my dual boot laptop.
I also talked with a local repair shop about the issues and possible remedies.
I got a SSD of the same size as the suspect HDD and successfully imaged the drive into the new item.  I do like the improvement the SSD provides.
With that done I tried to boot to a live DVD iso.  When I got an "[errno 5]" describing a possible faulty CD/DVD disc or drive and since the DVD had previously proven its function in an install into a desktop machine, I swapped out the drive for a spare one .
I then downloaded the 16.04.6 iso, verified the sha256sum and burned it a DVD using a win7 box at work.
Then: "Failed to open\EFI\Boot\mmx64.efi Not Found, Failed to load image \EFI\Boot mmx64.efi: Not found, Failed to start MokManager: Not Found, Something has gone seriously wrong: import_mok_state () failed".  I had the same results with both of the live DVDs.
After a bunch of searches, reading about not only the Ubuntu part of this but also the still functioning Windows 8.1 portion of the machine, I went down the dark path to eliminate any possible Windows influences that might be hanging up the Ubuntu install such as in disabling the secure boot.
Thus far I have made it to a "GNU GRUB version2.02~beta2-36Ubuntu3.22" header screen with grub> prompt.  I hit the TAB key and get a list of commands.  I have since been reading the Grub manual and playing with the commands.  The "help" command erupts with a description list that is longer than the screen height so I can only study the last portion of the list of explanations.  Any advice as how to pause this rapidly scrolling display would really be appreciated.
I did get the "Zfs-bootfs" to allow the"exit" command to boot back the the win partition.  I have been experimenting with other items in the command list but without sense of the proper syntax or file names it has been few hits and mostly error messages.  The grub manual does not appear to explain things at this grub prompt level.  Linux commands are not successful either.  I have also tried without success to use this grub prompt to find a grub.cfg file or where in the SSD grub itself is located.
If you can point to a better explanation of how to use this interface please post.

---

### Post by oldfred on 2019-12-03
Often SSD need firmware updates, even if new. 
       Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.  

Not sure if your Ubuntu installer was created correctly. For UEFI boot you should have the mmx64.efi. But that file is only required if installing in UEFI Secure Boot mode and need to set your own key for proprietary software like nVidia driver. Ubuntu cannot provide a key for software it does not know about, but a user can.

Most just copy grubx64.efi into /EFI/Boot and rename to mmx64.efi. Full install will have that file.
      
 System fails to boot with \EFI\BOOT\mmx64.efi - Not Found

May be your selection in Rufus to make Ubuntu installer.
      
 Rufus Create bootable USB drives the easy way  From Windows create Linux installer may have mmx64.efi error
rufus  select gpt (uefi non csm) 
If you select MBR csm(UEFI) that is BIOS boot.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 
    
       
 Can't install Ubuntu 18.10 on XPS 15 9570 - EFI\BOOT\mmx64.efi not found
[URL="https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found"]https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found


[/URL] 

        
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

---

### Post by C.Snyder on 2019-12-03
**oldfred**,
Thank you for answering my thread.
During my research, I have read some of your comprehensive responses to other posts.  At this point I can only aspire to the level of understanding that you share with the Ubuntu students like me.  The link to the Ask Ubuntu forum is one that I previously looked at but had not explored.
Over the last weeks one of the items I read into was firmware updates to the UFEI.  I had not considered updates to the new SSD but that is now on the list.
The suggestion about "Rufus":  I had not run into that one before.  Since the 16.04.x live DVDs will no longer boot, getting in through the still functional Win partition is another approach I had not considered.  Over the last decade I have rarely "opened up the windows" so the necessity of actually learning how to navigate 8.1 has been an added challenge.  
While auditing my backups that have been stored in flash drives, I found what I thought was a 16.04 iso that when I figured out how to boot it to the USB port turned out to be a Super Grub Disc.  I did try the Boot Repair function.  It did not help with the Ubuntu boot from the SSD.  The prize was in booting to a USB when I had never done so before and the fact that the UFEI did see the iso and allow for it's selection to first boot.  At the time, I was not sure that short of an upgrade the system would see the USB stick.
As a note to my previous post, I did look for a more complete Grub manual, and found a ver2.04 that explains the command prompt items.  Not to ignore your suggestions, but is there a path to the /boot file through the Grub command interface?  I ask only to evaluate the viability of my previous approach. 
Thanks

---

### Post by oldfred on 2019-12-04
Have not used SuperGrub for years. It was or is only for BIOS boot.
That site also has Rescutux which I have not used.
[https://www.supergrubdisk.org/](https://www.supergrubdisk.org/)

I also have rEFInd on an old tiny flash drive for emergency UEFI boot. That started with Mac as it was UEFI before Windows converted, but rEFInd works for any UEFI system.
       [URL="http://www.rodsbooks.com/refind/"]http://www.rodsbooks.com/refind/

      [/URL]Manual 2.04
[https://www.gnu.org/software/grub/manual/grub/grub.pdf](https://www.gnu.org/software/grub/manual/grub/grub.pdf)

Grub prompt is limited, but you can manually boot if it is only a grub issue and not something later in boot process.
For example if your install is in sda5.
       
 ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg
OR:
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot 
    
I have both drives similarly partitioned, but not identical.
So I often have to use ls to drill down to see details

       
 Adjust drive, partition to your install:
ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ? 
    
 I do not use Rufus, but noticed with some of the screen shots that it (now?) may have two modes to create flash drive. Ubuntu ISO is for both UEFI or BIOS boot. My systems shows both in UEFI boot menu. One is [noparse]UEFI:PMAP [/noparse] and other is just PMAP which then is just BIOS(CSM). Often PMAP is just name or label of flash drive, but depends on UEFI.
Rufus says MBR & CSM(UEFI) Some may think that is UEFI boot, but is only BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 
    Rufus also has gpt & UEFI .
The Ubuntu installer on flash drive can be either gpt or MBR(msdos), but gpt is normally used for full installs with UEFI boot.

    [URL="http://www.rodsbooks.com/refind/"]
[/URL]

---

