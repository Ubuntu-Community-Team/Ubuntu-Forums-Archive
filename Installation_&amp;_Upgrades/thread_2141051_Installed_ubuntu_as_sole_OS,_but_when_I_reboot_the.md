---
title: "Installed ubuntu as sole OS, but when I reboot the computer does not detect an OS"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by pantabulosin on 2013-05-01
Hi all, I recently decided to install Ubuntu 13.04 and I had decided to remove Windows entirely, so I let Ubuntu take over the entire HDD and installed in the live session. However, upon rebooting I was prompted with a message that said "No Operating System Found". I then tried Boot repair ( link: [http://paste.ubuntu.com/5623317/](http://paste.ubuntu.com/5623317/) ) and it gave me the following recommendation:

*> Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!*

Honestly, I don't know how to do that last part and that's why I need your help, since the original problem persists. If it helps, I own a VAIO computer and I tried finding out what my motherboard model is through the command

```
sudo dmidecode -t 0
```

and the output was


```

# dmidecode 2.11
# SMBIOS entry point at 0xca81a418
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: R0201V5
    Release Date: 12/20/2012
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 5120 kB
    Characteristics:
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 2.1
    Firmware Revision: 2.1
```

I also tried going straight into the BIOS and the only menu I can think could help me is the one dealig with PK keys, but I honestly don't feel confident enough to fiddle with anything until I learn more about this.

Any help would be greatly appreciated. Thank you for your time

---

### Post by darkod on 2013-05-01
I would say don't even bother with uefi boot. It was needed for win7 to work on a disk with gpt table, but ubuntu can use legacy (bios) boot with gpt, unlike windows.

So, I would go into bios and see if I can disable bios boot. Make it only legacy boot, or what ever the option is called. Then reinstall again which will install in bios mode.

If you can't disable uefi boot, use the boot menu of the computer and select to boot the legacy cd/usb with ubuntu, not the uefi version which will have the uefi prefix. By booting the install media in bios mode it will make sure it installs in bios mode.

---

### Post by pantabulosin on 2013-05-01
Thanks for the reply. I was honestly considering this and maybe seeing if I could use my windows recovery discs in a VM if I ever needed Windows again. I'm still interested in finding out how to do make this EFI stuff work though, if only to learn more about my laptop and be able to dual boot should the need to do so arise.

---

### Post by oldfred on 2013-05-01
Do you have secure boot on? 
Boot-Repair must have seen the secure boot setting to install and configure system to boot with shim. Shim is the grub version with the Microsoft signed key to boot Ubuntu on Windows 8 systems with secure boot.
You do show some Windows boot files in the efi partition.

I prefer systems to have a smaller / (root) and larger /home or data partition(s) with very large drives like yours. But it should work.

If you want to convert to BIOS, you need to add a tiny 1MB unformatted partition anywhere on drive and add the bios_grub flag. Boot-Repair then will let you convert to BIOS/CSM boot by uninstalling grub-efi and installing grub-pc.

In your UEFI/BIOS system you should have several boot options.        /EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/shimx64.efi 

With secure boot off the grubx64 should boot and with secure boot on shim should boot from the ubuntu folder.
The Windows entries have no Windows to boot from so they will not work.

---

### Post by pantabulosin on 2013-05-01
Thanks for your input. I do have secure boot and UEFI boot enabled and I would like for ubuntu to work under these circumstances. What I don't understand is how I still have microsoft files given that I erased my entire hard drive and left it as an unformatted volume before running the disks utility and installing ubuntu.

I also appreciate your input on having separate / and /home partitions. I honestly thought about doing that, and the only thing that stopped me was that I expected things to go more smoothly if I just let the ubuntu installer do its thing automatically.

I'd rather not convert to BIOS to be honest, since I will eventually have to get onboard with Secure boot/UEFI I might as well bite the bullet and do it now. However, I don't know how to make my BIOS boot on a specific directory. Is there a way to fix this through the terminal? I looked into the options of my BIOS and none seem to let me navigate the file system to point to a file to boot into, so I'm at a loss.

Thanks again for replying.

---

### Post by pantabulosin on 2013-05-01
Hi again.

I'm not sure if this counts as a fix, but I just reinstalled through the "other" section of the installer. Basically, I made a new EFI partition that was much larger than the 98 MB Ubuntu originally set for me, left the original boot efi partition alone, made separate / and /home partitions and now I am running Ubuntu 13.04 from my hard drive. Basically, I have two EFI partitions and I am assuming that Ubuntu now boots from the new one. It's not perfect but it's not that bad either.

Thanks again for your input and hopefully this serves as a workaround for anyone who stumbles onto this problem

---

### Post by oldfred on 2013-05-01
You can only have one efi partition per hard drive. I thought UEFI got confused and did not boot if you have two?

If you reinstalled with secure boot on then it would install the secure boot signed versions of grub & the kernel. Boot-Repair should have done that, but it does depend on what flags you set and what settings UEFI is in when you run Boot-Repair.

Post this.
       sudo parted /dev/sda unit s print

---

### Post by darkod on 2013-05-02
Just for further reference, you don't actually have to get onboard with secure boot and uefi, not for a number of years to come. The problem is when you get a preinstalled machine with win8 with secure boot and uefi, and no reinstall media except the stupid restore partition on the hdd. You are very much stuck with them.

Since you seem to be doing your own installs of ubuntu now and probably windows later, there is nothing preventing you to install win8 in legacy mode and without secure boot. It works. I have installed it in VBox that has nothing to do with either uefi or secure boot.

I am just mentioning this in case you think win8 can't be installed that way.

And by the time you want to replace win8 with win9 or what ever, you will probably change the motherboard/computer before that, so it will be a different ball game. :)

In any case, it's good you managed to install it the way you want to. But I would look into the double efi partition thing, because i also thought there could be only one and windows might get confused in the future when you try to install it.

---

### Post by pantabulosin on 2013-05-02
Here is the output from the CLI command

Model: ATA WDC WD10JPVT-55A (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system     Name  Flags
 1      2048s        194559s      192512s      fat32                 boot
 2      194560s      780287s      585728s      fat32                 boot
 4      780288s      60780543s    60000256s    ext4
 5      60780544s    1937006591s  1876226048s  ext4
 3      1937006592s  1953523711s  16517120s    linux-swap(v1)

---

### Post by pantabulosin on 2013-05-02
Better format
```

Model: ATA WDC WD10JPVT-55A (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number     Start               End                    Size              File system        Name  Flags
 1            2048s             194559s             192512s             fat32                 boot
 2            194560s         780287s             585728s             fat32                 boot
 4            780288s         60780543s         60000256s         ext4
 5            60780544s      1937006591s    1876226048s         ext4
 3            1937006592s  1953523711s    16517120s           linux-swap(v1)
```

As an aside, while I can get the computer to boot I do have other problems that stem from this. For instance, I tried to "repair" my Ubuntu install because I messed up trying to install proprietary drivers for my hybrid card and the installer would not let me because the boot partitions pointed to the same place (or something along those lines, I don't remember). I also think that this might bite me if I ever want to find out which of the two partitions is used to boot ubuntu if I ever wanted to find out.

On the other hand, here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) is a section describing the creation of separate EFI partitions to boot windows and Ubuntu, and although using just one is supported since ubuntu 12.04, apparently this is not a terrible idea.

By the way, thank you for bringing up the possibility of installing Windows on legacy mode. Truth be told I was kind of expecting Windows to be a pain to install if I ever got around to it again and just imagined that requiring secure boot would be par for the course. I was also expecting Secure boot and UEFI to be a much bigger deal in about a year from now, and I figured I'd need to learn if I ever get to install linux on my firends/family computers.

Thanks again for all the help.

---

### Post by oldfred on 2013-05-02
I do not understand how your system works with two efi partitions. Your UEFI must somehow accommodate that as others have had issues. 
UEFI systems boot from the folders in the efi partition. And all the documentation I have seen has said it should be the first partition on a drive although Windows makes it second and there should only be one.
The info in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) may be saying to create a new one not a second one as some systems have efi partitions that are locked and cannot be written into.

From your UEFI menu do you see the folders from both efi partitions?

---

### Post by pantabulosin on 2013-05-02
Well, I don't understand either, and I admit that there is no reason for this to work any better than doing a single EFI partition through the automatic installer as I originally tried to do (except perhaps a bug?). Maybe it's just a kink in the installer that "fixed" my original EFI partition and I could easily erase that new partition now and be fine. 

For further reference I'm going to add the contents of my /etc/fstab file just in case someone here can gleam something out of it that I did not, just in case this turns out to be a bug or something.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=c61953f4-05fe-46a5-8a4d-d7789ad1e010 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=DEB6-CF0B  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda5 during installation
UUID=ff23995e-c25d-46e1-baf0-61797e23195e /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=7a48b7ee-6712-4782-8335-e1a6a5b269d3 none            swap    sw              0       0
```

I'll keep checking on this thread in case someone else has any input on the matter or wants me to show a CLI output.

Thanks for all your help. I actually learned a lot during this time.

---

### Post by darkod on 2013-05-02
If you compare the UUID of the efi partition in fstab, DEB6-CF0B that shows that you are actually using /dev/sda1. The first partition, not the second one.

That also complies with the requirement the efi partition to be first on the disk.

---

### Post by pantabulosin on 2013-05-02
Thanks for replying.

I can understand that it boots on sda1, but I don't get why my laptop couldn't find a drive until I reinstalled adding a new boot/efi partition. Basically, right now the issue is solved but I don't know what went wrong in the first place. I wonder if it's a bug or a fluke.

---

### Post by darkod on 2013-05-03
As we already mentioned, that message was from the bios in my opinion, not from ubuntu. It usually displays when bios can't see a partition with the boot flag.

Your sda1 partition did have the boot flag as needed, but it seems out of what ever reason bios wasn't seeing it. Now you have sda2 with boot flag too (when in theory you should have only one boot flag per disk), so my guess is that uefi works with sda1 as it's supposed to, and sda2 served only to display the boot flag to bios, which made that message go away.

Maybe just removing and adding the boot flag on sda1 would have helped, without sda2, if there was any issue not seeing that boot flag.

---

### Post by pantabulosin on 2013-05-03
Thanks for replying. I'll try playing with the boot flags (removing it from sda1 and sda2, readding it to sda1) assuming it wont' bork my installation again.

---

