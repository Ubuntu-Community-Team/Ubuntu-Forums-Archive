---
title: "Unmount error for external HDD cloned from running OS."
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by Cbhihe on 2014-09-26
[FONT=arial][COLOR=#000000]Something eerie....
I just plugged in an external HDD containing a dual boot config with WinXP and Trusty 14.04. 

 I wanted to reformat that HDD to use it as backup storage. So I plugged it in through a usb-port on a laptop running its own fully stable Trusty 14.04. 
The external and internal disks happen to be bit-copied from one another. I.e. they are clones.  

What I saw and see:  
1) the usb-HDD disk started to spin uninterruptedly.  Still spinning after 2 hours.  
2) the WinXP partition on the usb-HDD was automatically mounted at */mnt/Win-xp*, while other partitions pertaining to Lx Trusty on the same usb-HDD were not. 
3) as I tried to unmount the WinXP partition using the GUI (with _*disks*_); I got:  
[FONT=courier new][I]  > Error unmounting /dev/sdc1:  
  > Command-line `umount  "/mnt/Win-xp"' exited with non-zero exit 
  > status 1: umount: /mnt/Win-xp: device is busy.  
  > (In some cases useful info about processes that use the device is 
  > found by lsof(8) or fuser(1))  (udisks-error-quark, 14)  
[/I][/FONT]
I think I know the reason for the snafu. But I don't know how to get around it.
The usb-HDD and the internal SSD being clones, my fstab config applies to both as they have exactly the same volume IDs. 
 fstab further specifies that, when booting, Trusty should always automatically mount the WinXP partition.  
_*udisks*_ shows exactly the same "device_file" names and identical mount points for both the usb-HDD (external) and the SSD (internal). That's logical and I should have thought of it earlier. [/COLOR][/FONT]:mad:         

[FONT=arial][COLOR=#000000]**Q: How do I reformat the (external) usb-HDD I want to squash ?** 
[FONT=arial][COLOR=#000000]I probably need to first modify volume IDs, but [/COLOR][/FONT]I don't have another OS on which to do it, otherwise it would be easy.  
Thanks.

-ced[/COLOR][/FONT]

---

### Post by oldfred on 2014-09-26
You should be able to use a live installer. You should have a current version repairCD or live version DVD or flash drive for every system you have installed just like this case where you need to make repairs.

You have duplicate UUIDs and need to change them on one drive or the other. Then update fstab and reinstall grub either with Boot-Repair or chroot into your system.

If plugged in when you boot it may randomly use whichever UUID partition it sees first. Generally I would think it might see the internal drive before the external but you could not rely on that.

       Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by Cbhihe on 2014-09-30
@oldfred, thanks ! 
Sorry for the late answer. Back from 3 days out, I finally just used 1 of many live DVDs that I have lying around. Next time I will pack one of them with my laptop.
I did as advised:
```
uuidgen -t   
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
```
for X=2;4;5;6;7, and then:
```
uuidgen -t   
sudo swaplabel -U numbergeneratedbyuuidgen /dev/sda3
```
on swap.

I had a little bit of trouble with the NTFS format of [FONT=courier new]/dev/sda1.[/FONT] It holds my vintage Win-XP OS. 
Its UUID's format is different from the type 4 UUIDs common for ext4 formated volumes and uuidgen
The command applicable to my case was found [here]("http://ubuntuforums.org/showthread.php?t=1240146&highlight=NTFS+UUID")[:]("http://ubuntuforums.org/showthread.php?t=1240146&highlight=NTFS+UUID):")
Use 
```
sudo blkid -L your-volume-label
```
to verify that the device volume you are going to act upon is the correct one.
```
sudo dd if=/dev/urandom of=/dev/sda1 bs=8 count=1 seek=9
```
That effectively replaces the UUID of the NTFS partition on /dev/sda1.

I updated [FONT=courier new]/etc/fstab[/FONT] and[FONT=courier new] /etc/initramfs-tools/conf.d/resume[/FONT] manually with vi (even though I tend not to use hibernation). Then I updated existing initramfs archives in [FONT=courier new]/boot[/FONT] for all kernels still there with:
```
sudo update-initramfs -u -k all
```

Once done, all that is left to be done is to rebuild grub. Will do that tomorrow and report only if I encounter problems. 
Thanks again for the pointers** oldfred**.

---

### Post by oldfred on 2014-09-30
You should only need to edit one entry in external's grub menu or may even be able to boot into external from internal directly using internal's grub. We normally do not edit grub.cfg, but you may be an exception. It may also be write protected. Once you edit first entry or boot into external you can run sudo update-grub to fix all entries in external.

Grub also remembers where to reinstall and may have the internal drive as where it would reinstall.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or if UEFI dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Cbhihe on 2014-10-01
... questions, definitely:

**Background**: after modifying UUIDs of every volume on a cloned dual boot system external device (an HDD) that can be mounted as a USB HDD, I need to re-install grub2 on it. 

Because that USB HDD and my running system (on an internal SSD) are clones, trying to determine where grub2 is located on my SSD, will also give me accurate  info on where to find it (from a live Ubuntu) on the external HDD.

```
> sudo debconf-show grub-pc
``` yields:

```
grub2/device_map_regenerated:
  grub-pc/install_devices_empty: false
  grub-pc/partition_description:
  grub-pc/install_devices_disks_changed:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_failed: false
  grub2/kfreebsd_cmdline:
  grub-pc/chainload_from_menu.lst: true
  grub2/linux_cmdline_default: quiet splash
  grub2/linux_cmdline:
* [COLOR=#ff0000]grub-pc/install_devices: /dev/disk/by-id/ata-ST9200420AS_5SH0ACMJ[/COLOR]
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/hidden_timeout: false
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/timeout: 10
  grub-pc/kopt_extracted: false

```

Looking at /dev/disk/by-id and doing '\ls -lsAF' gives no link to any device that matches [FONT=courier new]ata-ST9200420AS_5SH0ACMJ. [/FONT][B]

Q)[/B] How do I proceed with the device terminology highlighted in red,  [FONT=courier new]/dev/disk/by-id/ata-ST9200420AS_5SH0ACMJ[/FONT] ? 
I am really curious about that in fact. 
IF [FONT=courier new]grub-pc/install_devices[/FONT] is given that value, one would expect it to mean something.

```
> sudo grub-probe -t fs_uuid /boot/grub
```       however, yields the uuid for my /dev/sda3 with the label /boot. 
Not surprising, since my install of a dual boot was on a laptop with only one internal storage device AND that was also my first ever install of Lx on that machine.

---

### Post by Cbhihe on 2014-10-01
Got it.
Better to use chroot after booting from liveCD and mounting resources where/when appropriate, as detailed [here]("http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows/88432#88432"). 
Also used [this]("http://wiki.ubuntuusers.de/GRUB_2/Reparatur") as a handy reference (in German) for all commands useful in MBR and grub2 repairs. Something at least as comprehensive must be out there in English.

---

### Post by oldfred on 2014-10-01
The install device is the hard drive by model & serial. Since no device may be mounted it cannot use mounts.

This should show the drives and in BIOS, it usually shows by model.

sudo lshw -C Disk -short

---

### Post by Cbhihe on 2014-10-01
Ok, I executed:   ```
>  sudo lshw -C Disk
  *-disk
          description: ATA Disk
          product: Samsung SSD 840
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          [COLOR=#ff0000]logical name: /dev/sda[/COLOR]
          version: EXT0
          [COLOR=#ff0000]serial: S1DHNSAF108600H[/COLOR]
          size: 465GiB (500GB)
          ...
```
followed by info on each volume, from sda1 to sda7.
But then it only added to my confusion, as the serial number for dev/sda (in red) is actually its UUID and thus cannot match:
```
> sudo debconf-show grub-pc
...
grub-pc/install_devices: /dev/disk/by-id/[COLOR=#ff0000]ata-ST9200420AS_5SH0ACMJ[/COLOR]
...
```

I'm missing something. Will have a look at BIOS.

**Q) **In any case, when going the route of  '[FONT=courier new]sudo dpkg-reconfigure grub-pc[/FONT]' should I specify [FONT=courier new]/dev/sda[/FONT] or [FONT=courier new]/dev/sda3[/FONT] when asked for the grub2 install device ?
(The latter is the location of the original /boot/grub directory.)

---

### Post by oldfred on 2014-10-01
You almost never install grub to a partition like sda3, only to the MBR. BIOS boots from MBR, never partition boot sector. Only if you have another boot loader that must use partition to chain load to would installing to partition be required, but it still is not recommended by grub as it has to convert to blocklist or a less reliable way to install.

See post #4, you have to use tab, and space bar to turn on/off settings.

You either have or had a Seagate ST9200 or 200GB drive and that is where grub wants to reinstall on major update. If you do not have that drive or not booting from that drive then next major update where grub reinstalls will fail or install the new boot loader to a different drive.

---

