---
title: "dual boot from 2 different disks"
date: 2019-05-06
forum: Installation &amp; Upgrades
---

### Post by m_a_k on 2019-05-06
Hi, I have currently have Ubuntu installed on my PC. I would like to add a new disk to this PC and install an image that I got from a different Linux box (completely different PC) and make both existing and new drive (with new image installed on it) booatable. I already added and installed the new image but the new OS is not booting. It cannot find the device to boot.  I did update-grub and it updated the grub file but still does not work. It looks like I need to find and replace the UUID with /dev/sd??  ?  Please keep in mind that the new OS is not Ubuntu. What would be the correct way to do this? Can any one help?

Thank you,
Mak

---

### Post by oldfred on 2019-05-06
This often has enough info:
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 

I often use a configfile entry which is not a chainload but just a load of another install's grub. Then you do not have to have all the parameters correct. I label my new disco install and boot it this way from my main working install of 18.04. The first set root, then is not really required with the label set root.
```

menuentry "Ubuntu 19.04 Disco  (on /dev/sdb8)" {
    set root=(hd1,gpt8)
    search --set=root --label disco --hint hd1,gpt8
    configfile /boot/grub/grub.cfg
}
```

---

### Post by m_a_k on 2019-05-15
Thank you for the help. I was out of office so I was not able to work on this problem. 

I have some questions that needs some shed light. Since I directly copied the image to the newly added second disk, how would I take care of "mounting the disk"? When I do fdisk -l, I do not see the second disk mounted automatically. I mounted the second disk manually (only the partition which has the linux installation) and run update-grub but the grub.cfg file has the old UUIDs and old /dev/sdxx entries from the original PC. I added a new menu entry as explained in your post but it does not find the disk. I get "Invalid EFI file path" or boot partitions not found errrors (for example /dev/disk/by-id/data-WDC_WD2000......-part5 not found). Any suggestions?

Thank you,

---

### Post by yancek on 2019-05-15
Is the old disk GPT or msdos?
Did you try sudo parted -l or gdisk instead of fdisk?
Did you check the connections on the old drive?

If you move a partition to another drive, check the UUIDs.  Run sudo blkid or lsblk to get correct UUIDs and compare them to what you have in the grub.cfg file.  Also, you forgto to post the boot repair link which you were previously asked to do.  Make sure you use the Create BootINfo Summary option and do NOT try to make any repairs.

---

### Post by oldfred on 2019-05-15
Since UEFI has been around since 2012, even old systems now may be UEFI.
Are both installs UEFI or both BIOS?
Best to run report from Boot-Repair and see what it says.

---

