---
title: "Ubuntu 16.04 not Installing Grub2 UEFI GPT"
date: 2017-04-25
forum: Installation &amp; Upgrades
---

### Post by theonlytalkinggoat on 2017-04-25
I have been trying to install Ubuntu on a GPT disk, for 2 days, now. The installation goes perfect, no errors, but when I go to boot up, nothing. No bootable media found. I created a bios_grub and an ESP, bootable partition. I am sure it is a x64 usb key. Another querk is the installer will only allow me to put the boot record on /dev/sda, not /dev/sda1, the bootable ESP partition.
 
The installer, however, puts nothing in the ESP partition and, as far as I can tell, Nothing goes into the bios_grub partition, either, but it shouldn't need anything in the bios_grub, since this is a UEFI boot, not legacy. 

In an attempt to correct the issue, these are the steps I've taken, to try to manually install grub. 

 ```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
EFI boot on HDD
```

```
sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 97F58661-5F72-4C9F-BF37-81D0D0C36643
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2029 sectors (1014.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          391167   190.0 MiB   EF00  
   2          411648         8742911   4.0 GiB     8200  
   3         8742912       218458111   100.0 GiB   8300  
   4       218458112       976773119   361.6 GiB   8300  
   5          391168          411647   10.0 MiB    EF02  

```



```
efibootmgr
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0001,0002,0007,0005,0006,0000
Boot0000* ubuntu
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0007* UEFI: JetFlashTranscend 16GB 1100
```

```
sudo efibootmgr -b 0 -B
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0001,0002,0007,0005,0006
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0007* UEFI: JetFlashTranscend 16GB 1100
```

```
sudo efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0000,0001,0002,0007,0005,0006
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0007* UEFI: JetFlashTranscend 16GB 1100
Boot0000* ubuntu
```

```
mount /dev/sda3 /mnt
sudo mkdir /mnt/efi
sodu mount /dev/sda1 /mnt/efi
```

```
sudo apt-get install grub-efi-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-efi-amd64-bin
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
  grub-efi-amd64 grub-efi-amd64-bin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B/724 kB of archives.
After this operation, 2,426 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 grub-efi-amd64-bin amd64 2.02~beta2-36ubuntu3.7 [658 kB]
Get:2 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 grub-efi-amd64 amd64 2.02~beta2-36ubuntu3.7 [66.1 kB]
Preconfiguring packages ...
(Reading database ... 193482 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.7) ...
Removing grub-pc (2.02~beta2-36ubuntu3.7) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package grub-efi-amd64-bin.
(Reading database ... 193462 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-36ubuntu3.7) ...
Selecting previously unselected package grub-efi-amd64.
Preparing to unpack .../grub-efi-amd64_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-36ubuntu3.7) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.7) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.7) ...
```

```
sudo rm -rf /mnt/boot/grub
```

```
sudo grub-install --boot-directory /mnt/boot --bootloader-id=ubuntu --target=x86_64-efi --efi-directory=/mnt/efi/ --recheck --debug /dev/sda1
grub-install: info: adding a relocation entry for 0xcbd8.
grub-install: info: adding a relocation entry for 0xcbe8.
grub-install: info: adding a relocation entry for 0xcbf0.
grub-install: info: adding 192 padding fixup entries.
grub-install: info: writing 904 bytes of a fixup block starting at 0xc000.
grub-install: info: reading /usr/lib/grub/x86_64-efi/fshelp.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/ext2.mod.
grub-install: info: reading /usr/lib/grub/x86_64-efi/part_gpt.mod.
grub-install: info: kernel_img=0x236ec10, kernel_size=0x18800.
grub-install: info: the core size is 0x1c5d0.
grub-install: info: writing 0x1d800 bytes.
grub-install: info: copying `/mnt/boot/grub/x86_64-efi/core.efi' -> `/mnt/efi/EFI/ubuntu/grubx64.efi'.
grub-install: info: Registering with EFI: distributor = `ubuntu', path = `\EFI\ubuntu\grubx64.efi', ESP at hostdisk//dev/sda,gpt1.
grub-install: info: executing efibootmgr --version </dev/null >/dev/null.
grub-install: info: executing modprobe -q efivars.
grub-install: info: executing efibootmgr -b 0000 -B.
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0001,0002,0007,0005,0006
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0007* UEFI: JetFlashTranscend 16GB 1100
grub-install: info: executing efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\grubx64.efi.
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0000,0001,0002,0007,0005,0006
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0007* UEFI: JetFlashTranscend 16GB 1100
Boot0000* ubuntu
Installation finished. No error reported.

```

```
ubuntu@ubuntu:/mnt/boot$ ls
abi-4.8.0-36-generic         memtest86+.bin
config-4.8.0-36-generic      memtest86+.elf
efi                          memtest86+_multiboot.bin
grub                         System.map-4.8.0-36-generic
initrd.img-4.8.0-36-generic  vmlinuz-4.8.0-36-generic
```

This is the new grub folder...
```
ubuntu@ubuntu:/mnt/boot/grub$ ls
fonts  grubenv  locale  x86_64-efi
```

This is the EFI folder on the ESP partition
```
ubuntu@ubuntu:/mnt/efi/EFI/ubuntu$ ls
grubx64.efi
```

```
for i in /sys /proc /run /dev; do sudo mount --bind "$i" "/mnt$i"; done
sudo chroot /mnt
update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Adding boot menu entry for EFI firmware configuration
done

```
```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
EFI boot on HDD
```

Results of /etc/fstab:
```
UUID=8ad57035-0736-40bd-a119-9bf0f8f9282d /               ext4    errors=remoun$
# /boot/efi was on /dev/sda1 during installation
UUID=0E4C-314A  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda4 during installation
UUID=a30fd7f5-ed94-446a-8835-c896f5403919 /home           ext4    defaults     $
# swap was on /dev/sda2 during installation
UUID=c489e270-c9e1-445e-8e4b-4062b52fb3b0 none            swap    sw           $
```

```
sudo blkid
...
/dev/sda1: UUID="0E4C-314A" TYPE="vfat" PARTUUID="b2953c8b-9474-488d-82bc-982127abb50a"
...
```

Even after all that, STILL, no boot.

---

### Post by ajgreeny on 2017-04-25
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by theonlytalkinggoat on 2017-04-25
Too long to post. Here is the link to Pastebin...

[https://paste.ubuntu.com/24453957/](https://paste.ubuntu.com/24453957/)

---

### Post by Dennis N on 2017-04-25
When doing a UEFI install, grub will be installed /dev/sda. The installer will find your ESP partition on sda, and put grub boot files on it in a folder named Ubuntu. In fact, any other selection you make is ignored by the installer.

With UEFI, you don't need bios grub partition, but it makes no difference if it is there.

efibootmgr should be configured with 'ubuntu' entry first in boot order. That also should be automatically handled by the installer.  

If you run **sudo efibootmgr -v** 
you can see details, including the partition number the UEFI boot manager it is looking at for EFI system partition, and the specific file.

---

### Post by oldfred on 2017-04-25
I would in Boot-Repair's advanced mode run the full uninstall/reinstall of grub.
Be sure to be in UEFI boot mode as  you were when you ran Summary Report.

It does also show grub installed to gpt's protective MBR for BIOS boot and core.img in first sector of bios_grub. The bios_grub only has to be 1 or 2MB.
Just do not boot in BIOS mode, but it may actually work until updates get thing out of sync.
There are a few threads on making systems boot with both UEFI & BIOS which looks you have have or will have once booting.

What brand/model system or what motherboard?
What video card/chip?

---

### Post by theonlytalkinggoat on 2017-04-25
> **Dennis N said:**
> When doing a UEFI install, grub will be installed /dev/sda. The installer will find your ESP partition on sda, and put grub boot files on it in a folder named Ubuntu. In fact, any other selection you make is ignored by the installer.

With UEFI, you don't need bios grub partition, but it makes no difference if it is there.

efibootmgr should be configured with 'ubuntu' entry first in boot order. That also should be automatically handled by the installer.  

If you run **sudo efibootmgr -v** 
you can see details, including the partition number the UEFI boot manager it is looking at for EFI system partition, and the specific file.

Here is the result of sudo efibootmgr -v

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0001,0002,0007,0005,0006,0000
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
Boot0005  USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)..BO
Boot0006  Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)..BO
Boot0007* UEFI: JetFlashTranscend 16GB 1100    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x32,0x800,0x1d6b800)..BO




```

---

### Post by theonlytalkinggoat on 2017-04-25
> **oldfred said:**
> I would in Boot-Repair's advanced mode run the full uninstall/reinstall of grub.
Be sure to be in UEFI boot mode as  you were when you ran Summary Report.

It does also show grub installed to gpt's protective MBR for BIOS boot and core.img in first sector of bios_grub. The bios_grub only has to be 1 or 2MB.
Just do not boot in BIOS mode, but it may actually work until updates get thing out of sync.
There are a few threads on making systems boot with both UEFI & BIOS which looks you have have or will have once booting.

What brand/model system or what motherboard?
What video card/chip?

It is an HP Pavilion 20, all in one.

Can't I delete bios_grub and use the esp partition? Am I correct that bios_grub is only used for legacy bios installations?

---

### Post by Dennis N on 2017-04-25
> Here is the result of sudo efibootmgr -v

In reference to your display in post #6, it is not what I expected. Some details are missing. So that you can see what I was talking about, all my machines here give an output like this:

```
dmn@Sydney:~$ sudo efibootmgr -v
[sudo] password for dmn: 
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0007,000A,000B,000D,000C,000E,000F,0010,0011,0005
Boot0000* ubuntu	HD(1,GPT,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Manjaro	HD(1,GPT,8e6dba8f-5bdf-4b99-b7a4-2730717b1dba,0x800,0x64000)/File(\EFI\MANJARO\GRUBX64.EFI)
Boot0007* Korora	HD(14,GPT,20ebbadc-6db4-43c6-b77c-ba4c3a6139d1,0x2042c800,0x28000)/File(\EFI\FEDORA\SHIM.EFI)
Boot000E* ubuntu	HD(1,GPT,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1,0x800,0x100000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot000F* UEFI OS	HD(1,GPT,8e6dba8f-5bdf-4b99-b7a4-2730717b1dba,0x800,0x64000)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0010* UEFI OS	HD(10,GPT,23ba857f-57de-4a5e-ada4-c25ca0f4515a,0x16bac800,0x28000)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0011* UEFI OS	HD(14,GPT,20ebbadc-6db4-43c6-b77c-ba4c3a6139d1,0x2042c800,0x28000)/File(\EFI\BOOT\BOOTX64.EFI)..BO

```
Some garbage entries omitted here.

From this I can read the partition number of the EFI system partition, and the path to the boot file. For ubuntu, partition is #1 (first number inside the parentheses), and path is \EFI\UBUNTU\SHIMX64.EFI.

This currently boots to Manjaro's grub (ESP is part 1 on sdb - notice different UUID for the partition), but if I wanted to boot Ubuntu's grub, I would need to switch boot order to get 0000 first:

**sudo efibootmgr -o 0000,0001,0007** 

Entry 000E should also boot Ubuntu.

---

### Post by oldfred on 2017-04-25
Your Ubuntu entry with efibootmgr may be the BIOS boot option. Not exactly sure how BIOS boot shows in efibootmgr.

But as Dennis N shows you do not have the typical UEFI ubuntu boot entries.

And you do not need bios_grub with UEFI boot. But I have most of my drives configured for both the ESP & bios_grub as first two partitions as neither is really large.

But with HP having the Ubuntu UEFI entry may not matter.
HP violates UEFI standards and uses description as part of boot. And only valid description is "Windows Boot Manager" for some reason.
If only booting Ubuntu we can make a UEFI entry that says the Windows description but boots shim or grub.
If dual booting we make a fallback or hard drive UEFI boot entry. Many HP already have the UEFI entry. And now Boot-Repair copies shimx64.efi to /EFI/Boot/bootx64.efi which is a hard drive default or fallback boot.

Run the Boot-Repair full reinstall of grub. And check the "use the standard efi file" option. That does the file copy.
Always check with 
sudo efibootmgr -b

       sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi" 

efibootmgr defaults to sda1, more in case others see thread and ESP is not sda1.
      sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition , if sda2 for example
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sda -p 2 

If that does not work you can add Windows entry the same way.
      
 If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file': 
    
See also link in my signature for some other alternative ways to get difficult systems to boot. The rEFInd boot manage is also popular.

---

### Post by theonlytalkinggoat on 2017-04-25
I'm not disagreeing with you... believe me. The question is, why is it doing that? 

I deleted the ubuntu entry, using ```
sudo efibootmgr -b 0 - B
```, which worked. I then ran the efibootmgr command, used by grub-install, ```
sudo efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\grubx64.efi
``` then ran ```
sudo efibootmgr -v
``` Here is the output. I'll reboot and see if that entry stays there.

```
sudo efibootmgr -v
BootCurrent: 0007
Timeout: 2 seconds
BootOrder: 0003,0001,0002,0007,0005,0006
Boot0001* USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
Boot0003* ubuntu    HD(1,GPT,b2953c8b-9474-488d-82bc-982127abb50a,0x800,0x5f000)/File(EFIubuntugrubx64.efi) <- Notice how there are no "\". I wonder if grub-install is not putting them, as well. I enclosed the path in quotes and it now shows, correctly. 
Boot0005  USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)..BO
Boot0006  Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)..BO
Boot0007* UEFI: JetFlashTranscend 16GB 1100    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x32,0x800,0x1d6b800)..BO
```

After a reboot, it's back to the same thing.

```
sudo efibootmgr -v
Timeout: 2 seconds
BootOrder: 0001,0002,0007,0005,0006,0000
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
Boot0005  USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)..BO
Boot0006  Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)..BO
Boot0007* UEFI: JetFlashTranscend 16GB 1100    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x32,0x800,0x1d6b800)..BO
```

Here's something else to ponder... there is an option in the "bios" menu to run an EFI application. When I do that, it asks me to choose a hard drive, then shows the path of the EFI folder and, eventually, the grubx64.efi. When I select it, Ubuntu boots from the hard drive. I suspect the issue is whatever is causing the EFI to re-write the entry.

Oh, I'm manually selecting the UEFI record, "ubuntu" in the boot menu, to make sure I get that one. I didn't ignore the comment about setting 0000, first in the list of the boot order.

---

### Post by oldfred on 2017-04-25
I do not believe slashes matter. Some have them some have forward slashes & some back slashes, many have no slashes. All seem to be ok.

It is HP and its UEFI. I have not really seen anyone with HP that could make the ubuntu entry consistenly work.
Some just use the UEFI boot menu to boot which is a one time or each time you have to use it. And other use one of the many work arounds.
Some have not come back with what they did, not sure if they just gave up or it worked and they  never posted.

---

### Post by theonlytalkinggoat on 2017-04-25
oldfred, you are absolutely right. HP's have the Micro$oft bootloader hard-coded into their UEFI firmware. The fix I used will not allow dual boot, but I don't use Windows, anyway. 

First, my installation mounts /dev/sda1 (my EFI/ESP partition) to /boot/EFI If you're using a live cd, you'll need to mount /dev/sda1 to mnt or somewhere similar. For example:

```
sudo mount /dev/sda1 /mnt
```

Inside the EFI partition, there should be an EFI folder, with the path and file EFI/ubuntu/grubx64.efi.
Create new folders, with the tree EFI/Microsoft/Boot and place grubx64.efi into the Boot folder. 
Now, you should have EFI/Microsoft/Boot/grubx64.efi. 
Rename grubx64 to bootmgfw.efi

Delete the old entry, for example:

```
sudo efibootmgr -v
Timeout: 2 seconds
BootOrder: 0001,0002,0007,0005,0006,0000
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
Boot0005  USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)..BO
Boot0006  Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)..BO
Boot0007* UEFI: JetFlashTranscend 16GB 1100    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x32,0x800,0x1d6b800)..BO
```

To delete the "ubuntu" entry, use the command:

```
sudo efibootmgr -b 0 -B
```

Run: ```
sudo efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu_grub -l "\EFI\Microsoft\Boot\bootmgfw.efi"
```

Now, when you run the efibootmgr -v command, you should see:

```
sudo efibootmgr -v
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0003,0001,0002,0005,0006
Boot0001* USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
**Boot0003* ubuntu_grub    HD(1,GPT,b2953c8b-9474-488d-82bc-982127abb50a,0x800,0x5f000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)**
Boot0005  USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)..BO
Boot0006  Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)..BO
```

Problem solved, for now. Thanks for all your help.

---

### Post by oldfred on 2017-04-25
We used to rename the Windows file a lot. But typically do not now. Either fallback entry or use Windows description on grub or shim files.
It seems they only check description, not actual boot file.

But those dual booting lost the grub file on Windows updates as it would overwrite the grub file with a new Windows file.

But if not dual booting, your version should work.

If grub does a major update, you may want to copy again, just in case grub file changes.

---

