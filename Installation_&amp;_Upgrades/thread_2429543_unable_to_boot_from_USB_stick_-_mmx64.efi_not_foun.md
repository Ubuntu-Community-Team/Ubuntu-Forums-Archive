---
title: "unable to boot from USB stick - mmx64.efi not found"
date: 2019-10-19
forum: Installation &amp; Upgrades
---

### Post by fred63 on 2019-10-19
Greetings

I have a new but I suspect not quite pristine Dell Inspiron 15 5584 laptop that came preinstalled with Windows 10.

I have created a bootable USB stick from the file **ubuntu-mate-18.04.3-desktop-amd64.iso **following the instructions at [B][https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0).
[/B]
Now when I try to boot from the USB I immediately get the following message in text mode before the installer loads...
[B]Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start MokManager: Not Fond
Something has gone seriously wrong: import_mok_state() failed

[/B]At one point, I could actually boot from the USB and run the installer, but I got held up and had to abort the install. This leads me to believe that something happened on my solid state drive. It has no EFI folder or partition I also tried installing Debian 10.1 the same way with the same experience. Windows still works fine. I tried running a system restore but it didn't help.

I googled several examples of similar problems with the same error message, but found a definite lack of consensus on the solution. Also most were under slightly different circumstances. So, I decided to create a new thread.

Any suggestions?

---

### Post by oldfred on 2019-10-19
Most just copy a file into /EFI/Boot and rename to mmx64.efi.
[https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found)
Once installed you will have that file.
That file is for managing keys in UEFI Secure boot.
Are you booting with UEFI Secure Boot on?

Dell typically needs UEFI update, if SSD, SSD firmware update.
It needs RAID/Intel RST changed to AHCI, but if dual booting Windows add AHCI driver into Windows first.

Issues with Dell seem to be very common across all models, bigger difference if Intel or AMD.
Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)

General UEFI install instructions in link in my signature.

How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

### Post by fred63 on 2019-10-19
> **oldfred said:**
> Most just copy a file into /EFI/Boot and rename to mmx64.efi.
[https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found)


I read that page and I found the conflicting posts confusing. Could you please be explicit. Copy what file from where exactly (SSD? USB?) to where exactly. (SSD? USB)

Thanks

---

### Post by oldfred on 2019-10-19
If you have an Ubuntu install, anywhere, you can copy it from /boot/efi/EFI/Boot. You may have to change permissions on mount in fstab to be able to see that partition. My install of 19.10 created these:
```
fred@Bionic-Z170N:/media/fred/ESP_B/EFI/BOOT$ ll
-rw-r--r-- 1 fred fred 1334816 Oct 15 14:00 BOOTX64.EFI
-rw-r--r-- 1 fred fred 1213032 Oct 15 14:00 fbx64.efi
-rw-r--r-- 1 fred fred 1269496 Oct 15 14:00 mmx64.efi


```

If you just have live installer, it should be in the /EFI/BOOT/ folder on your flash drive.
My ISO for 19.10 shows this, do not now normally use flash drives, but you should have same files in flash drive:

```
fred@Bionic-Z170N:/media/fred/Ubuntu 19.10 amd64/EFI/BOOT$ ll
total 3922
dr-xr-xr-x 1 fred fred    2048 Oct 14 16:02 ./
dr-xr-xr-x 1 fred fred    2048 Oct 14 16:02 ../
-r--r--r-- 1 fred fred 1334816 Oct 14 16:02 BOOTx64.EFI
-r--r--r-- 1 fred fred 1406840 Oct 14 16:02 grubx64.efi
-r--r--r-- 1 fred fred 1269496 Oct 14 16:02 mmx64.efi

```

If file is really there in your flash drive installer, then change UEFI settings. Or try a different tool to create installer.
Some now have settings that may make it UEFI only or BIOS only, and then you have to be sure to boot flash drive in that mode.
You really want to boot in UEFI boot mode.

---

### Post by fred63 on 2019-10-19
> **oldfred said:**
> If you have an Ubuntu install, anywhere, you can copy it from /boot/efi/EFI/Boot. You may have to change permissions on mount in fstab to be able to see that partition. 
.
.
.


oldfred, my knowledge of the technical side of Linux is a little weak, I'm hoping you'll bear with me.

As a matter of fact I do have a second laptop with Ubuntu Mate 18.04.3 Installed. When I look at the file system using Caja i see there is a directory **boot **off the root, the only subdirectory I see is **grub**. I presume this is where changing the permissions on mount in fstab comes in. This is what the file /etc/fstab looks like. It's not at all clear to me how I should go about editing this. If you can show me what changes I should make, I can edit the real thing, after making a backup copy of course.

Regards,
Another old Fred

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=1704d3b3-1d47-41e6-8d8a-4001adfa5842 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0

```

---

### Post by ubfan1 on 2019-10-19
Your other Mate install is legacy, not UEFI, so /boot/efi/EFI/... simply does not exist.  Get the file off the USB installer you used. As oldfred said, on the USB, there is a directory named EFI, and under it should be anoher directory named BOOT, containing the mmx64.efi file.

---

### Post by fred63 on 2019-10-19
> **ubfan1 said:**
> Your other Mate install is legacy, not UEFI, so /boot/efi/EFI/... simply does not exist.  Get the file off the USB installer you used. As oldfred said, on the USB, there is a directory named EFI, and under it should be anoher directory named BOOT, containing the mmx64.efi file.

You're missing the point. The file mmx64.efi does not exist in the \efi\boot directory on the USB. There is only bootx64.efi and grubx64.efi

The same thing happens with Debian

---

### Post by ubfan1 on 2019-10-19
Oops, sorry, 19.04 was the first to include the mmx64.efi in the iso.  The file is in the shim package, so you may get it from there on your running 18.04 system, or use a 19.04 or 19.10 ISO (mount example for a loopback mount: "sudo mount -tiso9660 -oloop  myiso.iso /mnt/lb )

---

### Post by fred63 on 2019-10-19
ubfan1, I ran Synaptic Package Manager on my Running 18.04 system, and I see that the shim package is not installed. I'm a little leery installing a boot loader package. Is it safe?

Also, there is shim and there is shim-signed, which is a version of the bootloader binary signed by the Microsoft UEFI CA

---

### Post by fred63 on 2019-10-19
> **fred63 said:**
> ubfan1, I ran Synaptic Package Manager on my Running 18.04 system, and I see that the shim package is not installed. I'm a little leery installing a boot loader package. Is it safe?

Also, there is shim and there is shim-signed, which is a version of the bootloader binary signed by the Microsoft UEFI CA

Never mind, I downloaded the shim package using **apt download shim**, and extracted mmx64.efi. What I don't understand is what I'm supposed to do with it. I figure there are two possibilities...

1. copy it to the efi/boot directory on a [SIZE=3]read-only[/SIZE] USB boot drive

2. copy it too a efi \boot partition , a partition which [SIZE=4]doesn't exist[/SIZE] according to Windows Disk Manager. That;s the thing. I think that somehow during one of my aborted installs, when I could boot from the USB, my efi partition got boffed.

---

### Post by Dennis N on 2019-10-19
> As a matter of fact I do have a second laptop with Ubuntu Mate 18.04.3 Installed. When I look at the file system using Caja i see there is a directory boot off the root, the only subdirectory I see is grub

You need to look in **/boot/efi** for the file. If and only if you have UEFI installation, the folders under that are as shown below in the output of tree command. The file mmx64.efi is in two places, and you can cd down to either location. I had to be root to open /boot/efi. This is Ubuntu 19.04, so your output may vary.

```
dmn@Sydney-vm:~$ sudo -i
root@Sydney-vm:~# cd /boot/efi
root@Sydney-vm:/boot/efi# tree
.
&#9492;&#9472;&#9472; EFI
    &#9500;&#9472;&#9472; BOOT
    &#9474;** &#9500;&#9472;&#9472; BOOTX64.EFI
    &#9474;** &#9500;&#9472;&#9472; fbx64.efi
    &#9474;** &#9492;&#9472;&#9472; mmx64.efi
    &#9492;&#9472;&#9472; ubuntu
        &#9500;&#9472;&#9472; BOOTX64.CSV
        &#9500;&#9472;&#9472; grub.cfg
        &#9500;&#9472;&#9472; grubx64.efi
        &#9500;&#9472;&#9472; mmx64.efi
        &#9492;&#9472;&#9472; shimx64.efi

3 directories, 8 files
root@Sydney-vm:/boot/efi# exit
logout

```
So you can then copy the file from one of those locations to wherever you need it.

---

### Post by fred63 on 2019-10-19
Thanks Dennis. Please note in a subsequent post that I obtained the mmx64.efi in a different way, by downloading the package shim, using apt, and extracting the file.

---

### Post by fred63 on 2019-10-19
I now have a bootable USB stick. I'm not sure that this is the best solution but at least I got somewhere. This is how I did it....


[LIST=1]
[*]create a UEFI-only bootable live media using the instructions found here [https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media/](https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media/)  . I used the "Copy files from the ISO" method, Example via GUI
[*]download the package **shim **using **apt download** from my working 18.04 laptop. This package contains **mmx64.efi **
[*]extract the files from the package, and copy mmx64.efi to the EFI/BOOT directory on the USB stick.
[/LIST]

I can now boot from USB and at least start loading Ubuntu Live (Try Ubuntu without installing from the Grub menu)

However part way through the loading of Ubuntu Live, the process halts. I get a string of ACPI BIOS Errors and ACPI errors then at the end I get...

[B](initramfs) Unable to find a medium containing a live file System.
[/B]
Googling this last error turns up plenty of hits, including at least one here on ubuntuforums. So I will do some research and get back to you. I would like to leave this thread open for now, pending a better way to create a bootable USB.

cheers!

---

### Post by oldfred on 2019-10-19
Did you extract and copy all the files from the ISO into one FAT32 partition with the boot flag? No other FAT32 partitions on USB flash drive?

Some just have needed to use a different port on system, or a different flash drive. No consistent issue.

---

### Post by fred63 on 2019-10-20
> **oldfred said:**
> Did you extract and copy all the files from the ISO into one FAT32 partition with the boot flag? No other FAT32 partitions on USB flash drive?

Some just have needed to use a different port on system, or a different flash drive. No consistent issue.


Yes, one and only one FAT32 partition. I didn't actually extract the files. I mounted the iso file with the app Disk Image Mounter, displayed hidden files, did a select all and a copy and paste to the USB.

Three files would not copy. 

error copying "stable" and "unstable" to USB disk/dists
error copying "ubuntu" to /USB Disk

in all three cases the message was **Filesystem does not support symbolic links**.

I don't like my solution, and this is why. Do we agree that the file mmx64.efi does not normally appear on the bootable USB? I think the original "file not found" error means the installer is looking for the file on the SSD and can't find it., not the USB. Maybe that is the meaning of the **initramfs Unable to find a medium containing a live file system. **&#8203;Just a hunch.

As an experiment I created a UEFI only USB from a Debian iso. All the files copied without error, and I was able to boot completely into Debian Live. I then ran the installer.  When it came time to deal with Partitions, The installer only recognized the USB as a storage device. Because that's where the mmx64.efi file was? Just a guess.

---

### Post by ubfan1 on 2019-10-20
I think the mmx64.efi is for managing keys in the secure database, so since my normal machine is UEFI, but without secure boot capability, I've never had to use it.  If you wanted to run secure boot with the Nvidia drivers (unsigned by 
Canonical), you need to go through the procedure of signing them yourself and register your key (something I've never done).This self-signing procedure may be included in the 19.x installers, hence the inclusion of the mmx64.efi program.

---

### Post by fred63 on 2019-10-21
I'm not exactly sure what solved it, but post #13 holds the key

---

### Post by sudodus on 2019-10-21
> **fred63 said:**
> ...

I don't like my solution, and this is why. Do we agree that the file mmx64.efi does not normally appear on the bootable USB? I think the original "file not found" error means the installer is looking for the file on the SSD and can't find it., not the USB. Maybe that is the meaning of the **initramfs Unable to find a medium containing a live file system. **&#8203;Just a hunch

...

Which tool/method did you use to create your USB boot drive?

If you want a live-only USB boot drive it is best to use a **cloning tool**,

- in Windows: Win32 Disk Imager or Rufus in 'dd-mode'
- in Ubuntu 16.04 LTS and newer versions: Startup Disk Creator
- in other linux distros: Disks alias gnome-disks or [mkusb](https://help.ubuntu.com/community/mkusb)

If you want a **persistent** live USB boot drive I suggest that you use [mkusb](https://help.ubuntu.com/community/mkusb). It works with all current versions of Ubuntu and Ubuntu family flavours.

mkusb is a linux tool, you cannot use it in Windows, but you make a live-only USB boot drive with Ubuntu, boot into it, install mkusb and then make a persistent live drive in another USB drive.

---

