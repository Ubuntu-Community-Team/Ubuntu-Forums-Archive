---
title: "trouble with dual booting 12.04 and 13.04"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by boregard on 2013-05-20
Hello,I have tried to install 13.04 alongside 12.04 twice for dual booting both OS's. both times i have been greeted with a black screen that says insert proper boot media. I'am going to try to partion the free space with gparted before i give it one more try. Having trouble finding info on how to partition  13.04 for dual booting. Will i need another swap and boot/efi or bios/grub on new partition? My 12.04 OS has gpt/efi partitions. Thanks in advance for any help. best regards

---

### Post by oldfred on 2013-05-20
Are you booting installer in UEFI mode?
Proper Boot Media sounds like a UEFI/BIOS message that installer is not correctly configured or bootable. 

Did you verify download with md5sum?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You can only have one efi partition per hard drive. You can reuse swap, but then cannot hibernate, which if dual booting is not recommended anyway. Ubuntu boots pretty fast so hibernation often does not save much boot time anyway.

I might backup efi partition before install. I would expect new install to just update grub's efi files in the efi partition and then you will be booting new install by default, but do not know. Grub menu then should let you boot any installs you have.

You still may need Boot-Repair.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by boregard on 2013-05-20
thanks for reply, i  verified download with md5sum. not really sure if i was booting installer in efi mode, that may be my problem. i will start over with new bootable usb drive and make sure i am in efi mode. i'll post back and let you know how it went.

---

### Post by boregard on 2013-05-21
well i reinstalled 13.04 and made sure installer was in efi mode, tried boot-repair, still getting reboot and select proper boot device. tried to update grub from live cd and ge( unable to resolve host). dont know what else to try. here is link to boot-info [http://paste.debian.net/5542/](http://paste.debian.net/5542/)

---

### Post by oldfred on 2013-05-21
You have an efi partition. And both fstabs mount the efi partition.

But you have grub in the protective MBR and no bios_grub partition, so it does not install correctly to boot in BIOS mode.

It looks like Boot-Repair wants to repair a BIOS mode, but that may be just because you booted it in BIOS mode?

You should be able to boot with either BIOS or UEFI.

If you want BIOS you can add a 1MB unformatted partition anywhere on drive with gparted. Right click manage flags and set bios_grub flag.
Or you can use Boot-Repair in UEFI mode and reinstall grub-efi.

There are two versions of grub. grub-pc (BIOS) and grub-efi (UEFI). Then with efi installs you can have signed versions of grub & kernel to boot in secure boot mode. Secure boot is really only required with those Windows 8 systems that only boot with secure boot.

---

### Post by boregard on 2013-05-22
thanks for your help oldfred. what i find strange is, i had bios_grub  partition and 1MB unformatted partition but boot-repair wasn't detecting  them. i could open gparted and see them. i had a working 12.04 install  that was using them when i tried to install 13.04. the installer  detected 12.04 and i chose the option to install alongside 12.04. i  seriously think the installer does not work well with efi installs. the  problems may allso be with my intel hardware. tried to reinstall  grub-efi with boot-repair and still didn't work. so for time being i  just reinstalled 12.04 and will try again at some point in the future,  after researching this more. best regards

---

### Post by oldfred on 2013-05-22
I am not sure your bios_grub is correct if it is sda4. Gparted will show it with an error as it is unformatted.

It should show like this with 
sudo parted -l

> Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal


Because it is unformatted it will not show in some lists and your does show that way. but your also

---

### Post by boregard on 2013-05-22
that maybe what my problem is,mine is not  sda4 but  sda3. think i  should reinstall and correct this and try again? i have trouble with  installer when installing 12.04 and have to partition in advance then  choose something option just to get 12.04 to work. as you can see from  screenshot below i have left plenty of space to try other ubuntu's. does  13.04 have a shim to work with secure-boot computers? not that i need  it, my computer is efi but doesn't have secure boot. i thought i saw an  option when installing 13.04 about oem manufacturer. anyways thanks for  going extra mile to help me. best regards

---

