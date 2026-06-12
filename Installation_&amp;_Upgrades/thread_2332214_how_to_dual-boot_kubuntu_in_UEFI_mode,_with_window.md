---
title: "how to dual-boot kubuntu in UEFI mode, with windows 10 and two ssd hard drives?"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by gonzobilbao on 2016-07-29
Hi,

I have an HP envy 4 laptop that I have recently upgraded with a 750 GB ssd ( + the additional built-in 32 gb ssd). I have installed windows 10 in the 750 gb drive, in UEFI mode (legacy is completely disabled in the BIOS options), letting windows use 100 GB. The windows installation went fine and it is working ok, and it has created the typical 100mb ESP partition plus a "System" and "C.\" partitions.

Now I am trying to install kubuntu in the remaining space. My goal is to install the / partition in the 32 gb in-built drive, and the rest (home +a 16gb swap) in the spare space of the 750gb ssd.

To do so I am partitioning manually the two drives using the installer option. I am making sure that kubuntu sees the EFI partition already created by windows. I add home and swap in the 750ssd as indicated above. In the 32 gb ssd, I am creating a 250MB ESP partition and using the remaining space for a / partition. The installation goes ok and I reboot the computer. Only windows 10 is detected. 

I start the live kubuntu usb, install boot-repair and run the recommended repair. At some point I get the message:

```
Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].
```

However the separate /boot/efi partition option is checked.

I have read the available ubuntu documentation on UEFI, but I must be doing something wrong. Normally this documentation deals with single-drive dual-boot systems. I have read also that it is necessary to install a ESP partition on any drive. Fastboot is disabled. I don't have secure boot.

Any help please?

---

### Post by oldfred on 2016-07-29
Which drive is seen as sda? And/or then which seems to be locked.
Post this:
sudo parted -l

Grub only installs to ESP on sda. When I install to sdb or external drive, it overwrites my main Ubuntu's ESP entry. Quickly learned to backup ESP.

Back up your ESP('s).
Some locked ESP, just need chkdsk from Windows or dosfsck from Linux. From live installer you can run dosfsck on both ESPs.
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]https://bbs.archlinux.org/viewtopic.php?id=164185

      [/URL]
 Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.
Another possible work around. HP Pavalion G7
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273) 
    [URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]
[/URL] HPs are also hard coded UEFI to boot by description and only valid description is "Windows Boot Manager". UEFI spec does not allow that, but it seems more vendors are now using it.

HP may have a way to boot see if you have a way to get to "Custom" UEFI entries.
Some details in this thread.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076) 

Most use one or two work arounds. One is the default hard drive entry or "fallback" entry which is /EFI/Boot/bootx64.efi. That normally is just a copy of Windows .efi file, but we make it shim and then booting hard drive boots grub/Ubuntu.
If you run Boot-Repair and tick/check the "use the standard EFI file" in Adbanced options it will backup bootx64.efi and copy shim. It may not make the UEFI entry. Some UEFI auto add it or have it already.
Boot-Repair also fixes the read only ESP issue, by changing entry in fstab.


 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 


      
 [http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Also see link in my signature for more info and many details.

---

### Post by gonzobilbao on 2016-08-02
Hello oldfred, thank you for the reply. I tried what you suggested and it worked with the installation I had a that moment (see code bellow). I was able to start kubuntu, but I had to go on the bios menu each time (It wouldn´t go directly into grub). Also, It would start kubuntu in tty mode. Knowing that dosfsck could help with that was already an advantage. SO then I tried installing / and /home directly on the sda (750gb) with windows right next to it, and leave the entire 32 gb ssd for swap (I know, huge swap). Things didn´t work right away with boot-repair so I had to run again dosfsck and then boot-repair. And know I everything works perfectly. My computer goes straight into GRUB (which displays many entries I have never seen before :confused:) but I am able to use both my OSs.

*sudo parted -l* gave 

```
Model: ATA Crucial_CT750MX3 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  473MB  472MB   ntfs            Basic data partition          hidden, diag
 2      473MB   578MB  105MB   fat32           EFI system partition          boot, esp
 3      578MB   595MB  16.8MB                  Microsoft reserved partition  msftres
 4      595MB   104GB  103GB   ntfs            Basic data partition          msftdata
 5      104GB   105GB  890MB   ntfs                                          hidden, diag
 6      105GB   733GB  628GB   ext4
 7      733GB   750GB  17.0GB  linux-swap(v1)


Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  250MB   249MB   fat32              boot, esp
 2      250MB   32.0GB  31.8GB  ext4


Model: TDKMedia Trans-It Drive (scsi)  #LIVE USB WITH KUBUNTU#
Disk /dev/sdc: 3869MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  3869MB  3868MB  primary  fat32        boot, lba


Model: SD  (sd/mmc)       #A SD CARD#
Disk /dev/mmcblk0: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  32.0GB  32.0GB  primary  fat32        lba

```


Thanks again for helping!

---

### Post by oldfred on 2016-08-02
Boot-Repair sees all the HP .efi files in the ESP and adds a 25_custom for all of them.
You rarely or may not need them. Not sure with HP if you can directly boot them from UEFI.
Most houseclean most or all of 25_custom.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 

 [http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)

---

