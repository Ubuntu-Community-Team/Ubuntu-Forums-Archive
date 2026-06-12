---
title: "Grub Installation Failed"
date: 2019-02-06
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2019-02-06
I'm replacing a hard drive in a System76 Meerkat computer.
It has an SSD (boot and root) and this new HD I put in  (Home)
I used GParted to format and create one partition on the 500GB drive before moving on to the Ubuntu installation screens.
I was following the semi-automated Ubuntu install screens. I selected "something else"
[[IMG]https://i.ibb.co/9qHgJfF/Grub-failed-to-install-2019-02-06-15-55-16.png[/IMG]]("https://ibb.co/9qHgJfF")

sda                                                                           
&#9492;&#9472;sda1 ext4 (home)                              1855dbe1-722f-4f38-949a-4b8a3acb1803 
sdb                                                                           
&#9500;&#9472;sdb1 ext4 (boot)                             e9b2fe93-f5b5-49ce-b04c-8f797d8602aa 
&#9492;&#9472;sdb2 ext4 (root)                             a0c7a2b0-e853-4c7d-b490-c466fd7abbbf 

```

ubuntu@ubuntu:~$ df -h |grep -sv loop
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           787M  1.7M  785M   1% /run
/dev/sdc1        29G   18G   12G  61% /isodevice
/cow            3.9G  472M  3.4G  12% /
tmpfs           3.9G   41M  3.8G   2% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           3.9G   17M  3.9G   1% /tmp
tmpfs           787M   40K  787M   1% /run/user/999
ubuntu@ubuntu:~$ lsblk -af |grep -sv loop
NAME   FSTYPE   LABEL                    UUID                                 MOUNTPOINT
sda                                                                           
&#9492;&#9472;sda1 ext4                              1855dbe1-722f-4f38-949a-4b8a3acb1803 
sdb                                                                           
&#9500;&#9472;sdb1 ext4                              e9b2fe93-f5b5-49ce-b04c-8f797d8602aa 
&#9492;&#9472;sdb2 ext4                              a0c7a2b0-e853-4c7d-b490-c466fd7abbbf 
sdc                                                                           
&#9500;&#9472;sdc1 vfat     MULTISYSTEM              7F5D-E59C                            /isodevice
&#9492;&#9472;sdc2 ext4     Tom                      eb47bc29-aa23-4b83-a52e-543930de014c 



```

On second attempt I get 
$ ubi-partman failed with exit code 10
[[IMG]https://i.ibb.co/pbQJ4Z4/ubi-partman-failed-v01.png[/IMG]]("https://ibb.co/pbQJ4Z4")

/var/log/syslog
```

Feb  6 21:11:42 ubuntu dbus-daemon[1820]: [session uid=999 pid=1820] Successfully activated service 'org.gnome.Nautilus'
Feb  6 21:11:43 ubuntu dbus-daemon[1350]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.122' (uid=999 pid=22581 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Feb  6 21:11:43 ubuntu systemd[1]: Starting Hostname Service...
Feb  6 21:11:43 ubuntu gvfsd-metadata[4942]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Feb  6 21:11:43 ubuntu gvfsd-metadata[4942]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Feb  6 21:11:43 ubuntu dbus-daemon[1350]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb  6 21:11:43 ubuntu systemd[1]: Started Hostname Service.
Feb  6 21:11:43 ubuntu nautilus[22581]: Called "net usershare info" but it failed: 'net usershare' returned error 255: mkdir failed on directory /var/run/samba/msg.lock: Permission denied#012net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory#012Please ask your system administrator to enable user sharing.
Feb  6 21:11:48 ubuntu gvfsd-metadata[4942]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed

```

---

### Post by oldfred on 2019-02-06
You are not showing an ESP - efi system partition.
So you will get the error on trying to install the UEFI boot version of grub - grub-efi-amd64 to ESP as you do not have am ESP.

It looks like you have the older BIOS with MBR configuration, but hardware must be newer to install in UEFI mode.
UEFI normally uses gpt partitioning also.

Unless you want to totally backup all your data and totally reconfigure drives, by converting from the now 35 year old MBR to the newer gpt partitioning, just boot installer in BIOS boot mode.
The install has two boot modes, one UEFI and one BIOS. The UEFI one usually is clearly UEFI:flash and the BIOS boot is normally just flash where flash is a name or label of your flash drive installer.

So you know how you booted:
 Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by webmanoffesto on 2019-02-06
Based on the pictures at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) I think that when the computer worked correctly it booted in BIOS/CSM/Legacy mode.
Now, booting off a flash drive, it boots in U[COLOR=#333333][FONT=Ubuntu]EFI mode.
I'll follow the directions on the above web page tomorrow.[/FONT][/COLOR]

---

### Post by webmanoffesto on 2019-02-07
> **oldfred said:**
> You are not showing an ESP - efi system partition.
So you will get the error on trying to install the UEFI boot version of grub - grub-efi-amd64 to ESP as you do not have am ESP.

This is a System76 Meerkat. It has Intel Visual BIOS. It seems to be set for Legacy Boot. UEFI Boot is set for "No boot drive". So should I make it a Legacy install (and how) or should I make it an EFI install (and how).

[[img]https://i.ibb.co/3TyDtYB/20190207-081059.jpg[/img]](https://ibb.co/3TyDtYB) [[img]https://i.ibb.co/252kGkP/20190207-081107.jpg[/img]](https://ibb.co/252kGkP) [[img]https://i.ibb.co/qgCp7gP/20190207-081136.jpg[/img]](https://ibb.co/qgCp7gP) [[img]https://i.ibb.co/p2HCYvK/20190207-081146.jpg[/img]](https://ibb.co/p2HCYvK) [[img]https://i.ibb.co/WKKfbyR/20190207-081209.jpg[/img]](https://ibb.co/WKKfbyR) [[img]https://i.ibb.co/ZJYh5gy/20190207-081221.jpg[/img]](https://ibb.co/ZJYh5gy) [[img]https://i.ibb.co/Y735SzF/20190207-081225.jpg[/img]](https://ibb.co/Y735SzF)

---

### Post by oldfred on 2019-02-07
Because your drive is MBR and not gpt and then does not have an ESP, your system will not have a UEFI boot option.

But boot of internal system, is separate from the one time boot of an external flash drive or DVD installer.
The installer should have two options, one UEFI and one not UEFI, but maybe not as clearly labeled that is is the BIOS boot option.

---

### Post by webmanoffesto on 2019-02-08
> **oldfred said:**
> Because your drive is MBR and not gpt and then does not have an ESP, your system will not have a UEFI boot option.
Okay, but what do I do so that I can install Ubuntu on this?

---

### Post by oldfred on 2019-02-08
You boot using the BIOS/Legacy boot option of the live installer, then you can install grub in BIOS boot mode to MBR.
Unless you want to totally re-install everything in UEFI boot mode to gpt drive and restore all data from backups?

---

### Post by webmanoffesto on 2019-02-10
Okay, in this image you can see I'm in GParted and I set sdb1 formatted to fat32 and flags set to "boot" and "esp"
 [[IMG]https://i.ibb.co/ry79cw8/GParted-sdb1-fat32-boot-and-esp-2019-02-10-16-16-05.png[/IMG]]("https://ibb.co/ry79cw8")

Installing to fat32 /boot/efi

[[IMG]https://i.ibb.co/Dt5YrKk/FSHome-FSBoot-FSefi-root-2019-02-10-19-39-51.png[/IMG]]("https://ibb.co/Dt5YrKk")

/dev/sda1 ... ext4 ... /home ... 500000MB
/dev/sdb1 ... fat32 ... /boot/efi ... 6001MB
/dev/sdb2 ... ext4 ... / ... 26014MB

Device for bootloader installation: /dev/sdb1

Next:
Error: No efi system partition found:
 [[IMG]https://i.ibb.co/njMG8HY/No-EFI-System-Partition-was-found-2019-02-10-19-45-51.png[/IMG]]("https://ibb.co/njMG8HY") 


I clicked "continue"
Then I got the error message "The attempt to mount a file system with type vfat in scsi3 (0,0,0), partition #1 (sdb) at /boot/efi failed. You may resume partitioning from the partition menu." 
[[img]https://i.ibb.co/9bQwpwy/The-attempt-to-mount-a-file-system-2019-02-10-15-35-48.png[/img]](https://ibb.co/9bQwpwy)

---

### Post by oldfred on 2019-02-10
I have tried for years to get Ubuntu's grub to install to some other ESP than the one on sda. It will not.
I just installed disco to see if fixed yet, it said it was installing to sdb as I specified, but overwrote my /EFI/ubuntu folder on sda.

Or, for now, you must have an ESP on the first drive seen as sda.

And with UEFI, you should be using gpt partitioning.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface
      [/URL]
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
    
       This erases drive, I normally do this first thing with every new drive or larger flash drive.
I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. 

    
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]
[/URL]

---

### Post by webmanoffesto on 2019-02-11
[COLOR=#383838][FONT=gotham]Ubuntu Installed
What finally worked:[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]Resize sdb1 to 512MB, format: fat32, Flags: esp, boot
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]Install bootloader to sdb1: /boot/efi[/FONT][/COLOR]

---

