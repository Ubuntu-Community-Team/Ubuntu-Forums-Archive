---
title: "Upgraded to 11.04, Need to get the old bootloader back"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by racshot65 on 2011-05-02
Hi,

I'll tell you my setup, 

I have Windows 7 and Ubuntu installed and have the Windows installation encrypted with Truecrypt

I upgraded my Ubuntu installation today to 11.04 from the previous version (sorry can't remember its number / name) but I have a problem.

Because I had my Windows installation encrypted with Truecrypt I have to go through Truecrypts bootloader or I can't access Windows.

The upgrade to the latest version of Ubuntu replaced Truecrypts bootloader with Ubuntu's (GRUB 2 I assume) and now I can't access Windows.

Is there a way to restore the old bootloader ? 


Thanks

---

### Post by MAFoElffen on 2011-05-02
> **racshot65 said:**
> Hi,

I'll tell you my setup, 

I have Windows 7 and Ubuntu installed and have the Windows installation encrypted with Truecrypt

I upgraded my Ubuntu installation today to 11.04 from the previous version (sorry can't remember its number / name) but I have a problem.

Because I had my Windows installation encrypted with Truecrypt I have to go through Truecrypts bootloader or I can't access Windows.

The upgrade to the latest version of Ubuntu replaced Truecrypts bootloader with Ubuntu's (GRUB 2 I assume) and now I can't access Windows.

Is there a way to restore the old bootloader ? 


Thanks
As far as I can remember, there is still an open bug with/at Truecrypt (6 months ago / could be wrong at this time) where Truecript could chainload to Grub legacy and Grub2, but Grub could not start Truecript...and Truecript had some problems reading ext4 partitions.

The workaround for Truecript, Grub2 and Ext4 partitions was to install grub to the linux partion (sdax) instead of the MBR (sda)...  Restore the backup Window's MBR (google search on that brings up various methods or use testdisk)... press esc while booting Truecript (instead of the password) and it will find/chainload the next partition's bootloader.

In this workaround still the most current method?

**Edit:** Found these on Booting Truecript from Grub.
> **double1116 said:**
> I got this to work by getting grub2 to boot  the TrueCrypt rescue ISO. However, the above link isn't exactly what you  need.

1. Copy the rescue ISO to /boot
2. sudo apt-get install syslinux
3. sudo cp /usr/lib/syslinux/memdisk /boot
4. Add /etc/grub.d/40_windows_truecrypt:
#!/bin/sh
exec tail -n +3 $0
# Windows with TrueCrypt
menuentry "Microsoft Windows" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    linux16 ($root)/memdisk iso raw
    initrd16 ($root)/truecrypt.iso
}

Step 4 will add the entry whenever updating grub. You'll have to modify  some of this to fit your situation. Such as the (hd0,msdos3) partition  is your /boot, and the numbers start at 1. 

Hope this helps.
or something similar to 
```

menuentry "Windows" { 
search --set=root --fs-uuid 67e61837-c1a4-417c-9ac4-403c85406ea8 
linux16 /memdisk iso 
initrd16 /TrueCrypt_Descue_Disk.iso boot 
}

```Using 
```

sudo blkid

```
to find the UUID...

---

