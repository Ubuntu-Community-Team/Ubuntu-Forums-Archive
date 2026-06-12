---
title: "Ubuntu 12.04 install onto external USB drive"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by ray5 on 2013-09-25
I have a new Samsung external USB disk on which I wish to install 3 Linux distros; Ubuntu 12.04, Lubuntu 13.04 and Mint.   I have partitioned the Samsung USB drive using Gparted, creating 2 primary and 1 extended partition with the extended partition containing several logical partitions.          

So I have      

/dev/sdc        Samsung 1TB drive     
/dev/sdc1      ntfs partitioned     
/dev/sdc5      ext2 partition for Ubuntu 12.04 
    /dev/sdc6      ext2 Partition for Lubuntu 13.04     
/dev/sdc7      ext2 Partition for Linux Mint 
    /dev/sdc8      ext2 Data partition      
/dev/sdc2      Linux Swap         

I want to allocated to swap space partition to be used by each of the Linux o/s.          

The Ubuntu 12.04 Installation failed at the end    with error message   &#8220;Unable to install GRUB in /dev/sdc5&#8221; 

         I tried setting the partition to choose /dev/sdc as the partition to install the bootloader into,  but the same error message was again the result.      

What do I do to get the bootloader to install on this disk ( an external USB drive ) ?          

Thanks     
Ray     
NB the os on the internal drive is Windows Vista.

---

### Post by ray5 on 2013-09-25
I have tried re-formatting the post but it just don't re-format!

---

### Post by ray5 on 2013-09-25
original forum post now reformatted ( from a different PC )

---

### Post by ubfan1 on 2013-09-25
For non-UEFI machines, selecting /dev/sdc should install the bootloader to your USB disk.  Other complications arise with gpt partitioning, but you don't use that.  For UEFI machines, sometimes selecting the actual partition for the EFI bootloader installation works, sometimes it doesn't, but again, that is probably not your case.

---

### Post by sudodus on 2013-09-25
> **ray5 said:**
> I have a new Samsung external USB disk on which I wish to install 3 Linux distros; Ubuntu 12.04, Lubuntu 13.04 and Mint.   I have partitioned the Samsung USB drive using Gparted, creating 2 primary and 1 extended partition with the extended partition containing several logical partitions.          

So I have      

/dev/sdc        Samsung 1TB drive     
/dev/sdc1      ntfs partitioned     
/dev/sdc5      ext2 partition for Ubuntu 12.04 
    /dev/sdc6      ext2 Partition for Lubuntu 13.04     
/dev/sdc7      ext2 Partition for Linux Mint 
    /dev/sdc8      ext2 Data partition      
/dev/sdc2      Linux Swap         

I want to allocated to swap space partition to be used by each of the Linux o/s.          

[COLOR=#ff0000]The Ubuntu 12.04 Installation failed at the end    with error message   “Unable to install GRUB in /dev/sdc5” 
[/COLOR]
         I tried setting the partition to choose /dev/sdc as the partition to install the bootloader into,  but the same error message was again the result.      

What do I do to get the bootloader to install on this disk ( an external USB drive ) ?          

Thanks     
Ray     
NB the os on the internal drive is Windows Vista.

Assuming BIOS not UEFI: You should select to install the bootloader into the head end of the device, in your case /dev/sdc (not into the partition /dev/sdc5). Maybe that partition was mounted when you tried, but it would have been wrong anyway.

Afterwards you can fix the bootloader and grub according to these links.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Good luck :-)

---

### Post by oldfred on 2013-09-27
I think someone else that used ext2 had issues. 

I might also use ext4 as it includes a journal and would be more reliable and can run fsck much quicker.
If sharing swap, you cannot hibernate as that would use swap for that system, but other system would overwrite it.

Whichever system you install last will be the one who has its boot loader in the MBR. Then you can choose which is your prime system and install its boot loader to the MBR, by booting into it and just install grub to MBR.

If still sdc:
       sudo grub-install /dev/sdc

 sudo update-grub

You do know Windows does not run from external drives?

---

