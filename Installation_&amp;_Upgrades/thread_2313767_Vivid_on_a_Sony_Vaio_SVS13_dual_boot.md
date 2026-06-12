---
title: "Vivid on a Sony Vaio SVS13 dual boot"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by martin191 on 2016-02-15
Hello everyone,

after nearly 3 days of trying alone to solve the problem, I'm seeking for your help. What I'm trying to achieve is to get a dual boot of Ubuntu along windows 10. I need both of them and virtualizing is unfortunately out of the picture. What I've achieved so far was to install Ubuntu and then install back Windows 10. (I'm not sure I've taken the right path, but with the UEFI mode and what I've read about viao's and Ubuntu, it seemed to be the only way.) Whenever I turn on the computer, no operating system is found, although I'm still able to boot Ubuntu with help of grub from a USB stick: I press ESC on the boot menu to access grub and enter the following:
```
set prefix=(hd1,2)/boot/grub
set root=(h1,2)
configfile /boot/grub/grub.cfg
```
which enables me to boot on Ubuntu.

What I've done then to recover Ubuntu was to use boot-repair from a live USB with Ubuntu 15.04 on it. By the way, under vivid if you cannot install boot-repair, I found a graphical way to fix it: once you've added the repository, open the software center, edit -> software sources, edit the source [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) and instead of vivid for the distribution, write wily. (Hopefully this can help somebody...) I've tried to use the recommended repair, which did not work. I've tried then to play around with the different options but no success. Re installing grub from Ubuntu located on the partition I want to use was not helpful as well.

I guess all the trouble comes from the SSD I have and from my sketchy procedure to try to get the dual boot working. So here's a little explanation of the mess. First of all, a list of my hard drives:
```
Disk /dev/sda: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: E3A5CB0A-C981-4909-81BC-A1B95BCF29BE

Device         Start       End   Sectors  Size Type
/dev/sda1       6144   1050623   1044480  510M BIOS boot
/dev/sda2    1050624 108515327 107464704 51.2G Linux filesystem
/dev/sda3  108515328 125044735  16529408  7.9G Linux swap


Disk /dev/sdb: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 78543D6B-88CF-482A-92D4-2698DDD3748F

Device     Start       End   Sectors  Size Type
/dev/sdb2  34816 125044735 125009920 59.6G Microsoft basic data


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 8ACAD1F0-F76D-470C-A7D3-69D8AB62AD75

Device      Start        End    Sectors   Size Type
/dev/sdc1      34     262177     262144   128M EFI System
/dev/sdc2  264192 1953523711 1953259520 931.4G Microsoft basic data

Partition 1 does not start on physical sector boundary.

```

The drives /sda and /sdb were actually one unique ssd under windows when I bought the laptop. Opening it, they are really looking like two USB sticks placed on a PCB. The drive /sdc is an HDD I just bought that replaces the optical drive there was. What I obviously want is to have Ubuntu and Windows on both SSDs. After the Ubuntu installation, they somehow got disentangled. You can see that I've reserved some space on each for a UEFI partition. The problem is that from the BIOS, both are united as one and only one drive. You can see as well that I tried to create as well a partition on the HDD to maybe boot from there.

So my question would be, do you think there is a clean way to get around all this ? I guess that in the worst case, I could install a light distribution on the HDD and install there grub.

I'd be happy for any feedback, and obviously can send some more informations about all this mess, such as for example the log of the boot-repair procedure which might prove useful...

Thanks a lot in advance !

---

### Post by oldfred on 2016-02-16
Sony is one of now uses Description as part of UEFI boot. Only valid description is "Windows".  That is specifically not allowed per UEFI spec, but perhap some large operating system vendor is giving discounts.  But there are multiple work arounds.

Both Windows & Ubuntu install in the same way you boot install media, either UEFI or BIOS. So you want to boot installers in UEFI mode.
I know Windows in BIOS mode installs all boot files to drive set as default in BIOS, not sure about UEFI.
Ubuntu always installs grub's efi boot files to drive seen as sda, but if separate drives I like to have an ESP - efi system partition on every drive, and I manually copy /EFI/ubuntu folder back to Ubuntu drive. Then may be able to boot that drive without sda drive.
Some disconnect one drive and just do an install to that, to make sure systems are separate. For both Windows & Ubuntu, but if you do keep Windows as first SATA port 0 so seen as sda. It likes to be first.

If you have a bios_grub partition that is only for BIOS boot.

 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

Now older version of Ubuntu, newer should work better.
Sony Vaio  - EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

        Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)

    Alternative work arounds for Sony & HP, also in link below in my signature
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by martin191 on 2016-02-17
Dear oldfred,

Thanks a lot. I was able to install the dual boot and configure grub. Placing windows as the first partition on the disk and copying the boot directory worked as explained in [http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378](http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378)

Best,

Martin

---

### Post by oldfred on 2016-02-17
That thread from 2013 copies grub & shim to boot /EFI/Boot and /EFI/Microsoft/Boot/bootmgfw.efi.
I do not recommend replacing the Windows efi boot file with shim, but only replacing /EFI/Boot/bootx64.efi. 
Boot-Repair used to replace Windows efi boot file back then, but does not anymore.

Microsoft on updates will overwrite the /EFI/Microsoft boot file and if you are using that to boot into grub, then it stops working.

Better to only copy shimx64.efi to bootx64.efi and boot hard drive entry from UEFI.

---

