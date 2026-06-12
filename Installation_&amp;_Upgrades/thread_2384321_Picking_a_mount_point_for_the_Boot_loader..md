---
title: "Picking a mount point for the Boot loader."
date: 2018-02-05
forum: Installation &amp; Upgrades
---

### Post by irv on 2018-02-05
I got behind on my upgrades and I am sitting at 17.04, unsupported. I was going to upgrade from a USB with 17.10.1. I have the option to upgrade the 17.04 to 17.10 but it is asking me to pick a partition for the bootloader. I thought I would ask before I install which one do I pick? Here is my window from Gparted.
[ATTACH=CONFIG]278447[/ATTACH] 
I am thinking it is /dev/sda2, EFI System partition, the fat32?
It is the one that the windows and I believe the grub is loading from right now. I do need to know if this is the case before I do the upgrade?

---

### Post by oldfred on 2018-02-05
If you are using  UEFI, it really does not matter what you pick.
Generally you pick the drive like sda. And you should.

But with UEFI it only installs to the ESP - efi system partition on drive seen as sda. Which is not always right or desired, but you cannot change it.
Other distributions do allow you to choose.

---

### Post by irv on 2018-02-05
oldfread, doesn't it look like it is booting from /dev/sda2, EFI System partition, the fat32? I am running Window and Ubuntu in EFI right now. Would Grub be in sda2 or would it be in sda? For some reason I just can't get this straight in my head? Is sda the drive and sda2 a partition. And does the grub need to be on the drive and does it have to be bootable?

---

### Post by ubfan1 on 2018-02-05
In UEFI, the bootloaders are just files.  grub's executable is usually located on the EFI partition (mounted at /boot/efi) at .../EFI/ubuntu/grubx64.efi.  If secure boot is enabled, the bootloader is shimx64.efi, and grubx64.efi must be present in the same directory.  A fallback location is set up at .../EFI/Boot/bootx64.efi, which is just a copy of the bootloader in use.  Possibly, some other grub executable is used, but the only difference is where it looks for the grub.cfg file. So the bootloaders are all in sda2, the EFI partition.

---

### Post by oldfred on 2018-02-05
Just as when you install in BIOS mode and choose a drive like sda, with UEFI you choose a drive like sda, but grub only then installs its boot files into the ESP - efi system partition on drive seen as sda.

With UEFI there are no boot files in the gpt drive's protective MBR. MBR with gpt only exists to have one entry saying full drive is gpt, so old MBR only partitioning tools do not see an empty drive and then create issues.

All installs then have boot files in the ESP in different folders.

---

### Post by irv on 2018-02-06
I am going to do the upgrade this morning and will set to boot from sda. If all goes well I will be back, If not I will be repairing the damage.

---

### Post by irv on 2018-02-06
Well, I went ahead with the upgrade and I picked sda to boot from. It told me when I got into the install that there was something wrong and that the grub would not load.
From that point it was a nightmare It would not boot. I ended up doing a clean install of Ubuntu but it still would not boot. The only way I can get into Ubuntu or Windows is using a Super Grub boot stick.
I was going to make a Boot Repair USB but the Unetbootin will not work Here is the error I get
[ATTACH=CONFIG]278456[/ATTACH]
I tried to do this on my other laptop which is running 17.10.1 as well and I get the same error.
I tried running unetbootin from the prompt at the command line and I get this.
[ATTACH=CONFIG]278457[/ATTACH]
Where do I go from here?

---

### Post by oldfred on 2018-02-06
If you want an UEFI only bootable flash drive, you do not need any installer.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by ubfan1 on 2018-02-06
Check the ownership on all your home directory "dot" files, the only root owner should be on ..
ls -la 
Running X programs with sudo causes various problems.

---

### Post by irv on 2018-02-06
I don't care what I do I can't get the bootloader to install at the end of the install. I can't believe I am having this much trouble installing Ubuntu.
OK when the install finishes I get this message
> The 'grub-efi-amd64-signed' package failed to install into the /target/ without grub boot loader the installed system will not boot.
I tried to do a grub repair following these [instructions]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") but when I get to the point where I do the command
```
grub-install /dev/sda5
```
It tells me that there is no EFI directory.
sda5 is where I have installed Ubuntu and made it the mount point

EDIT: here is my boot directory.
[ATTACH=CONFIG]278458[/ATTACH]

---

### Post by oldfred on 2018-02-06
You (almost) never install  grub to a partition. Your sda5 is a partition.
You should have an ESP - efi system partition which is the FAT32 with boot flag.

Often for users not familiar with command line:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by bcschmerker on 2018-02-06
[@irv](https://ubuntuforums.org/member.php?u=47460)  **How many partitions your system, what sizes, and where?**  I'm used to multiple hard drives on the Hot Rod gPC&#8482;; as of February 2018 it packs a Western Digital® WD1600JS (/dev/sda; sda1 as /boot, sda2 subdivided to sda5 as / and sda6 as /tmp) on SATA 0 and three Toshiba® MQ01ABD050's (/dev/sdb, /dev/sdc, /dev/sdd) on SATA 1 through 3.  All have multiple ext4 partitions except /dev/sdd, which bears /home as a BTrFS partition, all under the old Master Boot Record format due to ubuntu® 16.04-LTS installation-tool limitations.  (Advance plans call for re-format of all HDDs as GUID Partitions to integrate with the Unified Extensible Firmware Interface - Gigabyte® GA-MA78GM-S2HP BIOS F6D can do UEFI - and Intel® Advanced Host Controller Interface&#8482; as part of the ubuntu® 16.04.5-LTS-to-18.04.0-LTS major dist-upgrade.)

The GUID Partition Table formatting during initial installation of ubuntu® 16.10 or later makes a GUID-Partition-Tabled /dev/sda1 across the entire primary drive, with the master boot record of /dev/sda so indicating.  This /dev/sda1 can be subdivided into multiple mount points.

---

### Post by irv on 2018-02-06
Every time I go to install I get this warning.
[ATTACH=CONFIG]278460[/ATTACH]

I included my gparted window so you can see my partitions.

EDIT:  I tried to make a mount point then it tells me I have two.

---

### Post by oldfred on 2018-02-06
Your sda2 is the ESP.
Not sure why you are getting errors, but some have had to run repairs on the FAT32 partition.

You can mount ESP in Windows repair console and run chkdsk.

Or from Ubuntu live installer:
       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by irv on 2018-02-06
I am not sure what the problem was but I got around it. Here is what I ended up doing.
After trying to install 17.10.1 I am going to guess 15+ times. No matter what I did it didn't work.
I even wipe everything off the hard drive and reformated and created new partitions. The last time I got this:
[ATTACH=CONFIG]278466[/ATTACH]
I quit trying to install 17.10.1. Instead, I installed 16.04 and it went like clockwork. I made sure everything was up to date and then I did upgrade to 17.10.1 from within 16.04.
I am now running 17.10.1 and all I have to do now is install all my programs and set up my settings.
I will mark it as solved but it was a hard way to go. It took me over 10 hours to just do the upgrade and I have to remove Windows 10.
I filed a bug report I for some reason the install for 17.10.1 just would not work,

---

