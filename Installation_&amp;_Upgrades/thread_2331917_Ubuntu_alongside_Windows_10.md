---
title: "Ubuntu alongside Windows 10"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-07-26
I've decided to dual boot Ubuntu and Windows 10, on my new Acer desktop but I was wondering if I choose to install **alongside Windows **will I be given the option on how much **disk space **that partition will have that Ubuntu will be installed on?  or will it decide for me. Thanks so much

---

### Post by QDR06VV9 on 2016-07-26
@RobGoss this worth a look with Recovery Options: [http://technozed.com/install-ubuntu-linux-alongside-windows-10/](http://technozed.com/install-ubuntu-linux-alongside-windows-10/)

---

### Post by RobGoss on 2016-07-26
> **runrickus said:**
> @RobGoss this worth a look with Recovery Options: [http://technozed.com/install-ubuntu-linux-alongside-windows-10/](http://technozed.com/install-ubuntu-linux-alongside-windows-10/)

Are you suggesting recovery option with in Windows 10?

---

### Post by QDR06VV9 on 2016-07-26
Read it First is all i am suggesting.
 But Creating a recovery drive is just good sense IMHO
And No I have not done this, you have a windows free guy here:P

---

### Post by RobGoss on 2016-07-26
> **runrickus said:**
> Read it First is all i am suggesting.
 But Creating a recovery drive is just good sense IMHO
And No I have not done this, you have a windows free guy here:P

Thanks so much will do, I'm trying to move away from Windows my self I have** 5 **machines already running Linux this is number **6,** but it's my wife machine which see does not use so I decided to make good use of it and dual boot it for now.. \\:D/ I will look that link over

---

### Post by sudodus on 2016-07-26
I suggest that you also read about installing in UEFI mode (unless you know about it already). It can be tricky compared to installing in BIOS mode - and it is varies a lot between computers depending on the version of UEFI/BIOS system. You can start with the following links (and links from them).

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

[booting with UEFI](https://help.ubuntu.com/community/UEFI)

[UEFI Installing - Tips.](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by RobGoss on 2016-07-26
> [COLOR=#000000]I suggest that you also read about installing in UEFI mode (unless you know about it already).[/COLOR]

Thanks **Sudodus**, Yes I'm aware of** UEFI** I have a few machines that already have this feature, I was just wondering if I choose to install along side of Windows will I have the option to choose how much disl space that partition will have. The last time I dual booted I can't remember if it gave me this option

---

### Post by sudodus on 2016-07-26
I prefer to ***use Windows to shrink the Windows partition***. Let there be enough workspace left for Windows, at least 30% free space in the NTFS partition, maybe 50% to allow some accumulation of data before it get crowded and defragmenting.

Leave the unallocated space and reboot into an Ubuntu live drive.

***Use gparted to create partitions for Ubuntu and maybe a common partition for data***. This way you 'see' what you do.

After that you ***start the installer*** and select ***Something else*** at the partitioning window. Select the partitions, that you created with gparted.

This way you have much better control of what you are doing.

Good luck :-)

***Edit:*** Remember to turn off hibernation (including fast boot) in Windows and reboot it to let it fix and accept the new size of the Windows partition, otherwise Ubuntu will have problems to read the NTFS partition(s) including an optional common data partition.

---

### Post by RobGoss on 2016-07-26
Sudodus, Yes you are correct this is what I was thinking but I was also thinking I wanted to make sure I installed the GRUB on the right partition so I would have the option to choose between which OS I wanted to boot

I have trouble with one of my dual boots it does not give me the GRUB menu to choose but that's ok because I don't really use Windows on that machine so I did not want to correct it

---

### Post by sudodus on 2016-07-26
You can create an efi partition of 300 MB with FAT32 and a boot flag, but I think it is best to share the existing EFI partition, that Windows created. I *think* the installer will select that partition automatically (in UEFI mode).

-o-

You can invoke the grub menu afterwards. See this link: [Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

Edit [B]/etc/default/grub
[/B]
> GRUB_HIDDEN_TIMEOUT=

    No value entered after the = sign
    The menu will be displayed for the number of seconds designated by GRUB_TIMEOUT. 

Run ```
sudo update-grub
```

---

### Post by RobGoss on 2016-07-26
Thanks so much Sudodus I will look in to this

---

### Post by sudodus on 2016-07-26
I just started thinking, that if Windows was recognized, when grub was configured and/or updated, there should be a dual boot condition and the menu should be displayed.

Maybe Windows was not recognized.

- It could be because Windows was hibernated, semi-hibernated (fast boot),
- or there were errors in the NTFS file system, so that linux would refuse to mount it and read it
- or Ubuntu was installed in BIOS mode while Windows was installed in UEFI mode or *vice versa*
- or something else, that I cannot think of now.

---

### Post by RobGoss on 2016-07-26
Yes I think that was my first dual boot and I installed Ubuntu In Legacy and not UEFI, I did not think much about it but realized my mistake but by then Ubuntu was running so good I did not want to risk messing it up and until today it' still running like a champ a year later :)

But this next machine I want the GRUB working as it should in case the misses want to crank it up she will have the option to choose Windows I'm hoping she just give me the machine and I can just wipe it

---

### Post by oldfred on 2016-07-26
You never (almost never) install grub to a partition like sda1, but always to a drive like sda.
With UEFI it knows that boot loader .efi files go into the ESP - efi system partition. And with UEFI, it only installs to the ESP on sda, no matter what drive you install Ubuntu into. The ESP is the FAT32 formatted partition with the boot flag. Best to only have one per device. UEFI spec says more than one can be used, but very few systems seem to work with two efi partitions.

With BIOS you specify drive and it then knows to install boot loader code in the MBR of that drive. 
The ESP is somewhat like the MBR, but allows multiple boot loaders to share the ESP, where MBR can only have one boot loader.

---

