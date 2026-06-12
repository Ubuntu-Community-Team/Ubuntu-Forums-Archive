---
title: "Install Ubuntu RAID 1 Software with mdadm"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by giobaxx on 2019-05-25
Hello Guy

I need to install an ubuntu desktop with RAID 1 Software and i need to clarify points that i discovered were not so clair in my mind. in the past i have used the Ubuntu Server installation to implement RAID 1 but one of my collegue told to try to use mdadm with ubuntu Desktop so i tried.....but i'm not able to run it. the Installation fails installing **executing** **grub-install /dev/md0p6.  ** i googled but i didnt find anything that helped me to understand where i made the mistake.

What i did is

 
[LIST=1]
[*]create two partition with gdisk.  I have to use 3TB Disk so i need to use GPT instead of MBR this does this imply using UEFI or i can still use legacy boot?
[*]run  ***mdadm --create  --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda  /dev/sdb***
[*]run the graphical installer tryng to install ubuntu on /dev/md0
[/LIST]

I tried at work with a Physical workstation and the installer t asked me to create a small **bios-boot partition,** because of the GPT disk that was not asked to do it in my VM test on VMWare workstation.

[h=1][SIZE=2] Could someone tell me how can i make works?[/SIZE][/h]

---

### Post by TheFu on 2019-05-25
I've never used SW RAID to boot, just for data.

Did you follow these instructions? [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
Those instructions don't mention support for LVM, so I would probably try to do an LVM install, then make it into a SW-RAID setup using LVM.

There's always this: [https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)
And a related bug: [https://bugs.launchpad.net/subiquity/+bug/1785332](https://bugs.launchpad.net/subiquity/+bug/1785332)

---

### Post by giobaxx on 2019-05-25
tanks for the links. from what i have understood you cannot install Ubuntu with RAID  using Ubuntu Desktop and mdadm.  you are forced to use Ubuntu Server??

---

### Post by oldfred on 2019-05-25
If using gpt with BIOS boot, you will need a bios_grub partition. It is 1 or 2MB unformatted with bios_grub partition. It needs to be in the first 2TiB of a drive, often first or second partition. If ever planning on using UEFI, since all computers since 2012 and release of Windows 8, you may want to include an ESP - efi system partition as first partition either for UEFI now or perhaps in future or testing. Then you do not have to totally redo drives to have ESP later.

I do not know server installs, but have seen that with Desktop, it will install with RAID, its just that grub does not seem to correctly install. So most seem to use server install & then add desktop of choice. You can manually install grub after Ubuntu install, but a bit of a hassle.

---

### Post by SeijiSensei on 2019-05-25
I never join entire drives with mdadm as you seem to be doing.  I partition the drives first (usually with fdisk), then use mdadm to join a pair of partitions.  At a minimum, I'd create a 512MB partition on each drive, and designate one of them for /boot during installation. I typically use ext2 for /boot since journalling is overkill for a simple filesystem like this.  In this model I would create /dev/sda1 and /dev/sdb1, each 512 MB in size, then /dev/sda2 and /dev/sdb2 spanning the remainder of the disk.  Join them with mdadm for RAID1.  (I also use fdisk to change the partition type of the RAID members to "fd".  This alerts the operating system that the partition is a RAID member and helps at boot.)

Most programs that don't use a GUI like mdadm don't care which version of Ubuntu you're running.  You might have to install mdadm manually on a desktop machine using apt or a software manager; I don't think it's bundled in the standard desktop distribution. Once installed, though, you use the same procedures to create a RAID array on either a desktop or a server.

---

### Post by giobaxx on 2019-05-25
I'm able easly to implement a raid software with mdadm but just for storage that we can mount in a already installed workstations,  but for the momento i'm not able to install ubuntu desktop because is failing to install. After the bootloader install fail i could have three option

1) choose different device to install booloader, 
2) Continue without install  booloader, that could be installed later
3) Leave the installation

but whatever i choose when i press OK nothing happend, so i have to reboot the system. 

Probably the only way too install is use the iso of ubuntu server....

---

### Post by TheFu on 2019-05-25
The links I provided earlier says to use the "Alternate Installer" distro.  [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)  It looks like that is a "server" install, though I've never consider it as that, since adding a lite GUI is my default for desktops. Still learning new things daily here. ;)

+1 for **partition the drives first**. If you don't, then why have GPT?  In this case you MUST partition the drives first to accomplish what you want.

According to this: [https://community.spiceworks.com/how_to/340-lvm-single-drive-to-lvm-raid-1-mirror-migration](https://community.spiceworks.com/how_to/340-lvm-single-drive-to-lvm-raid-1-mirror-migration) it is possible to do a normal install without RAID, but with LVM, then add a 2nd disk and convert the single-disk LVM to LVM+RAID1.  

  There was a brief conversation during a Q&A after a presentation with one of the Ars writers, who also works for a Linux/BSD storage company, about SW-RAID (mdadm vs LVM) last year at SELF. The same code is used for all the SW-RAID stuff in LVM as it is in mdadm, so there isn't any difference in performance. Plus you get the flexibility of LVM. He had tested both and found statistically insignificant differences from test run to run.  As a storage guy and BSD guy, he was pushing ZFS, of course.

---

### Post by giobaxx on 2019-05-26
i'm not a linux expert:-....too complicated the solution too convert from LVM to RAID. I've tried to use the Ubuntu Server  and then later add Ubuntu-Desktop. The solution seems to ne not so hard to implement

[https://www.youtube.com/watch?v=IWiXBCaBr_o](https://www.youtube.com/watch?v=IWiXBCaBr_o)

...but i face some one problems(around 1 m 07 sec of the video) after i create the first partition(as in the video) the option **create software RAID** become Grayed OUT and i don't know why!!!! :-(

---

### Post by rsteinmetz70112 on 2019-05-28
I've done this many times.

Format the drive, create a partition, use the entire drive or leave some space for other uses then joint the partitions to an mdadm device, create a filesystem on madam0 or use lvm and load Ubuntu. I find using the command line the easiest way.

---

