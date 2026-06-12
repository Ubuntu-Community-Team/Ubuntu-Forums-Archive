---
title: "Ubuntu install fails to correctly configure GRUB with RAID + LUKS in UEFI mode"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by anatoli2 on 2014-01-26
Hi!
 
We are trying to install Ubuntu 12.04.3 x64 Alternate (ubuntu-12.04.3-alternate-amd64.iso) on one IBM machine (IBM System x3100 M4) with 2 x SATA 1TB WD RE4 booting from an USB drive in UEFI mode. At all steps we choose the most basic/default options.
 
At the Partition disks step we create 3 partitions on each disk (GPT partition table): the 1st one is EFI Boot Partition (200Mb), a 2nd partition of 100Mb, and a 3rd partition of 10Gb. Then we create 2 RAID1 arrays on the 2nd and 3rd partitions (md0 and md1 respectively) and then we create an encrypted partition (md1_crypt, with the default options) on top of the 2nd array. We format the 1st RAID array for ext2 and assign it /boot mounting point and the 2nd one (the LUKS partition) is formatted for ext4 for / mounting point. 

The layout looks this way:

```
Encrypted volume (md1_crypt) - 10.0 GB Linux device-mapper (crypt)
>     #1     10.0 GB     F  ext4          /
RAID1 device #0 - 99.5 MB Linux Software RAID Array
>     #1     99.5 MB     F  ext2          /boot
RAID1 device #1 - 10.0 GB Software RAID device
>     #1     10.0 GB     K  crypto        (md1_crypt)
>            512.0 B        unusable
SCSI2 (0,0,0) (sda) - 1.0 TB ATA WDC WD1003FBYZ-0
>             1.0 MB        FREE SPACE
>     #1    199.2 MB  B  K  EFIboot
>     #2     99.6 MB     K  raid
>     #3     10.0 GB     K  raid
>           989.9 GB        FREE SPACE
SCSI4 (0,0,0) (sdb) - 1.0 TB ATA WDC WD1003FBYZ-0
>             1.0 MB        FREE SPACE
>     #1    199.2 MB  B  K  EFIboot
>     #2     99.6 MB     K  raid
>     #3     10.0 GB     K  raid
>           989.9 GB        FREE SPACE
```
 
Then we proceed with the rest of the install using the most basic options. After the reboot an error flashes for an instant: "error: efidisk read error" and we get a grub> prompt.
 
We figured out there are 2 problems: one with the RAID boot in EFI mode (see a known bug here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)) and the encrypted / partition. We managed to solve the RAID problem (see the details here: [http://ubuntuforums.org/showthread.php?t=2201239](http://ubuntuforums.org/showthread.php?t=2201239)), but no luck with the encryption.
 
After fixing the RAID problem, we see the GRUB menu for the OS (normal and recovery). If we choose normal, the screen turns black with a blinking cursor at the top left corner and the keyboard stops to respond (not even capslock, numlock or ctrl+alt+del). 

If we choose recovery option, it shows a lot of output, then it shows a prompt for the LUKS password, but the keyboard doesn't respond as in the normal option.
 
 
The last 4 lines read:
 
```
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ...
Unlocking the disk /dev/disk/by-uuid/427...009c (md1_crypt)
Enter passphrase: 
```
 
Please see a photo of the screen attached.
 
The system actually doesn't freeze as some 30s later messages about usb devices start to appear with some 15s of delay between each.

Any idea how to solve this? Thanks in advance!

---

### Post by anatoli2 on 2014-01-27
OK, we solved this problem as well. It was that initramfs was not loading the device drivers for USB keyboards. It was looking like the system had frozen/hanged, because the initial GRUB list of the OS boot options was working ok with the same keyboard and there was no keyboard response at LUKS passphrase step (which is the ramfs step).
 
The OS boot process, in simple terms, looks this way: GRUB boot loader is executed by the BIOS/EFI firmware, then it loads a RAM file system (/boot/initrd.img prepared by initramfs-tools) and this part decrypts the filesystem and loads the kernel. Each of these parts has its own modules, drivers, scripts, etc. and it's perfectly possible for the same hardware to function correctly in one of them and not to function in another.
 
So, it was happening that the initramfs-tools was not correctly preparing the initrd.img. Better to say, the OS installer was not indicating it correctly what drivers to include. This issue affects a lot of distributions, RedHat, Suse, Debian, Ubuntu, Arch.. Google for "usb keyboard luks hid" and you'll find hundreds of posts about this problem, tens of bug-reports in all OS bug-reporting databases.
 
A simple fix is the following: you should add your keyboard driver name to the /etc/initramfs-tools/modules file and update the initrd.img with update-initramfs -u.
 
What drivers to add, depends on your keyboard firmware manufacturer. You can look for a name in this list: ```
ls -la /lib/modules/`uname -r`/kernel/drivers/hid
```
 
For our case we added the most common drivers as well as a special Logitech driver, and a couple of others (just in case another keyboard is connected in the future), here is the list (it's the same to use dashes or underscores in the names, initramfs-tools converts them to underscores):
 
ehci_hcd
ehci_pci
hid
hid_apple
hid_generic
hid_logitech
hid_microsoft
mac_hid
ohci_hcd
ohci_pci
uhci_hcd
usb_common
usbcore
usbhid
xhci_hcd
 
So just execute these commands inside the OS to fix this problem:
```
echo -e "ehci_hcd\nehci_pci\nhid\nhid_apple\nhid_generic\nhid_logitech\nhid_logitech_dj\nhid_microsoft\nmac_hid\nohci_hcd\nohci_pci\nuhci_hcd\nusb_common\nusbcore\nusbhid\nxhci_hcd" >> /etc/initramfs-tools/modules
update-initramfs -u
```
 
 
If you want to fix this problem directly during the installation process, then at about 50% of the "Installing the base system" step (just after partitioning disks), switch (with Alt+F2/F3) to another console and check if the /target/etc/initramfs-tools/modules file already exists:
 
```
ls -la /target/etc/initramfs-tools/modules
```
 
When you detect it's there, just run this command:
 
```
echo -e "ehci_hcd\nehci_pci\nhid\nhid_apple\nhid_generic\nhid_logitech\nhid_logitech_dj\nhid_microsoft\nmac_hid\nohci_hcd\nohci_pci\nuhci_hcd\nusb_common\nusbcore\nusbhid\nxhci_hcd" >> /target/etc/initramfs-tools/modules
```
 
(For convenience, you could select the network-console package at "(Down)Load installer components" step and continue the installation from another computer (e.g. with PuTTY) where you could copy-paste the necessary commands to prevent any typo and leave the monitor of the computer with the installer at the installer log console (Alt+F4))
 
The installer will execute the update-initramfs script at later steps so you don't need to worry about that.

---

