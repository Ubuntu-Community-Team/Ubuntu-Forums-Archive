---
title: "Dual Boot Win/Ubuntu, No Grub menu anymore. How to get it back?"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by grailswebdev on 2016-04-11
Hello,

I'm having problems with a dual boot installtion of Windows 8.1 Pro 64-bit and Ubuntu 14.04 32-bit on Lenovo T530. 

Windows was preinstalled and I installed a LUKS encrypted Ubuntu 14.04 a while ago. Everything worked until yesterday and Ubuntu was hanging while booting. I also reset Windows 8.1 and now my Grub bootloader is gone and I can't even fix the not booting Ubuntu. I don't see any boot menu anymore and Windows is booting right away. 

I tried to use boot-repair to fix the issue but it didn't work. Windows is installed in UEFI boot mode. My BIOS is up-to-date and the settings for UEFI is set to "Both" that means Legacy and UEFI is enabled. Secure boot is disabled. I also tried a software called EasyBCD in Windows directly but it says the current session is in EFI mode so some options are disabled and can't be used. Meaning, I couldn't add a new entry for booting Ubuntu. Then I tried boot-repair-disk-64bit.iso as an USB disk but it says basically the same thing: EFI mode and I need to use boot-repair-iso in EFI mode. But how? I tried several things with enabling/disabling and switching UEFI options in the BIOS but this didn't work either. I created a boot-info report and put it on Pastebin. Can someone help explaining how to get back the Grub loader so I can access Ubuntu again?

[http://pastebin.com/ag43Bk7z](http://pastebin.com/ag43Bk7z)

---

### Post by oldfred on 2016-04-11
Only 64 bit Ubuntu (and Windows) is UEFI capable.
UEFI & BIOS are not really compatible. You can only dual boot from UEFI menu when systems are installed in different boot modes.

And with UEFI having its own boot menu, there is no reason for EasyBCD. You directly boot from UEFI, if you do not use grub.
But grub only boots systems installed in same boot mode. So if Ubuntu/grub is 32 bit/BIOS then it cannot offer to boot Windows.

You do not show grub installed to gpt's protective MBR for BIOS boot, so how were you booting?
Was grub actually on flash drive for BIOS boot?
It looks like the sdb1 partition is a /boot partition for Ubuntu/grub. But now sdb has syslinux which is a Windows type BIOS boot loader. You may be able to use Boot-Repairs advanced mode, make sure LVM/encrypted is mounted, it should ask for passphase, and reinstall grub to sdb for BIOS boot.

Long term better to have 64 bit Ubuntu in UEFI boot mode, but that is a new install.

---

### Post by grailswebdev on 2016-04-11
> **oldfred said:**
> 
You do not show grub installed to gpt's protective MBR for BIOS boot, so how were you booting?
Was grub actually on flash drive for BIOS boot?


Yes, I had GRUB on an USB stick that I used to boot Ubuntu. It always worked but not anymore. If I removed the GRUB-USB device Windows 8 was booting instead. Any ideas? What options in boot-repair should I set and try? I don't find this software very self-explaining...

---

### Post by oldfred on 2016-04-11
I have always done it manually.
But in Boot-Repair is an advanced option. And you want to choose your install and choose the flash drive (sdb?) as location to install boot loader.
You must mount /boot and / which is inside the LVM. So make sure LVM is mounted and unencrypted or it will not work.

---

### Post by grailswebdev on 2016-04-23
Hi,

I managed to get the Grub boot menu back but still can't start Ubuntu properly. This is what I did to get the grub back on my USB stick and it starts:

My BIOS settings are unchanged. First booting device in boot device order is from USB drive.

```
sudo vgscan
Reading all physical volumes. This may take a while...
Found volume group "vgubuntu" using metadata type lvm2

```

```
sudo vgchange -a y 
2 logical volume(s) in volume group "vgubuntu" now active

```

```
sudo lvscan

ACTIVE    '/dev/vgubuntu/swap' [9,77 GiB] inherit
ACTIVE    '/dev/vgubuntu/root' [292,19 GiB] inherit
```

Now I mount the partition with the root-directory (/) like this:

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/mapper/vgubuntu-root
```

Since my boot-partition is on a external USB drive, I do:

```
sudo mount /dev/sdc1/ /mnt/ubuntu/boot
```

Then:

```
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo mount -o bind /sys /mnt/ubuntu/sys
sudo mount -t proc /proc /mnt/ubuntu/proc
``` 

Then I did:
```
sudo chroot /mnt/ubuntu /bin/bash
```
So far so good. Next I tried:

```
grub-install /dev/sdc

grub-update
exit
```

All that worked. But, as mentioned, Ubuntu won't start properly.

I boot into the latest kernel but in the output I see:

can't open "vgubuntu-root" no such file

and /dev/mapper/vgubuntu/swap is not ready yet or none existend. Keep waiting or use >>S<< to skip or >>M<< to start a manual recovery

What can I do now? 

I tried to boot into Recovery mode. I come as far as entering the encryption password...

I should mention that my Home directory is encrypted as well. When I do an ls -al /home/myusername/ I see that I need to do some ecryptfs-mount-private. Is there a way to avoid this? I'm not sure if I still have to password-hash for this. :(

Any ideas on this? How can I fix this without losing the home directory?

---

### Post by grailswebdev on 2016-04-23
I solved it! I tried all kernels I had one by one, step by step. Luckily, one worked and I could log in again. Everything works fine now. 
Thanks for the help!

---

