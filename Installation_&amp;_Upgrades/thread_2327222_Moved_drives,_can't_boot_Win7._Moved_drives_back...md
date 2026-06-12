---
title: "Moved drives, can't boot Win7. Moved drives back... STILL can't boot Win7"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by sorceror171 on 2016-06-08
Trying to put in a new SSD. Already have Linux on an SSD, want to put Windows on one. I only have two 6Gbps SATA ports, so I moved the Windows boot drive to the last SATA port, and put the (blank) SSD in to replace it.

Could boot Ubuntu just fine, it can see the drives just fine. Figured I'd run "update-grub", it'd find the Windows drive in the new location, update the boot loader, and all set. So I rebooted, selected "Windows 7 (loader) (on /dev/sde1)" and... it claimed there was no such partition with UUID "7E9E43B09E435FAF" (even though gparted says that's the UUID and the boot flag is set). Also, "BOOTMGR is missing". I'm puzzled by this, but not horribly alarmed. I try a couple tweaks to the "40_custom" file in /etc/grub.d/, tossing in a "drivemap" command, things like that. No dice. I shut down and go to bed.

Today, I come home from work, put the Windows drive back in its old position, put the SSD in the last SATA port, boot Ubuntu, remove the stuff from 40_custom, and run update-grub. The entry in /boot/grub/grub.cfg reflects the correct position, and so far as I can tell is identical to the prior state:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-7E9E43B09E435FAF' {
        insmod part_msdos
        insmod ntfs
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  7E9E43B09E435FAF
        else
          search --no-floppy --fs-uuid --set=root 7E9E43B09E435FAF
        fi
        parttool ${root} hidden-
        chainloader +1
}
```

But... identical symptoms. I can boot Ubuntu 16.04 just fine, that's what I'm typing this from. But trying to boot Windows 7 gives me "error: no such device: 7E9E43B09E435FAF" and then "BOOTMGR is missing".

I can't understand why restoring the drive to its previous location wouldn't restore Grub2's ability to find and boot Windows. What the heck do I need to do to bring up Windows again? Is there some step after update-grub that I'm missing?

---

### Post by grahammechanical on 2016-06-08
> Trying to put in a new SSD. Already have Linux on an SSD, want to put Windows on one.

What is stopping you doing that? It needs a fresh install of Windows to do it. As for the other problem. Where is Grub  installed to? The Ubuntu SSD? Or the Windows 7 hard drive?  Or both? It may be that after running update-grub you may need to run

```
sudo grub-install /dev/sdx
```

where sdx is the Ubuntu SSD. I can tell you this that set root='hd1, msdos1' = second hard disk & first partition = sdb1. If the Windows drive is back into the first SATA slot then it it should be sda1 for Linux and 'hd0, msdos1' for Grub. When you run update-grub what does the printout show you? It should list the location of the Windows boot loader. 

Also, sometimes we stop os-prober from running when we update-grub by removing the ability of 30_os-prober to execute or run as a program. Sometimes we do that when we have a 40_custom file. Have you done that in the past? If 30_os-prober cannot execute or run as a program then no other OS will be detected. And the settings in grub.cfg may not be changed.

Regards.

---

### Post by oldfred on 2016-06-08
Lets see full configuration:

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sorceror171 on 2016-06-08
To be very precise, I had a total of four drives in the system before. I've added one more. Here's the (slightly trimmed) output of fdisk -l now, drives are listed in the order they are plugged into the SATA ports (total of 6, one occupied by optical drive, it doesn't show up here):

```

Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048  80687594  80685547 38.5G 83 Linux
/dev/sda2       80689152 500115455 419426304  200G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1  *     2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc1  *          2048  901119999  901117952 429.7G  7 HPFS/NTFS/exFAT
/dev/sdc2        901120000 1953523711 1052403712 501.8G  5 Extended
/dev/sdc5        901122048 1005979647  104857600    50G 83 Linux
/dev/sdc6       1005981696 1425412095  419430400   200G 83 Linux
/dev/sdc7       1425414144 1458968575   33554432    16G 82 Linux swap / Solaris
/dev/sdc8       1458970624 1953521663  494551040 235.8G 83 Linux


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Device      Start        End    Sectors  Size Type
/dev/sdd1      34     262177     262144  128M Microsoft reserved
/dev/sdd2  264192 3907028991 3906764800  1.8T Microsoft basic data


Disk /dev/sde: 465.8 GiB, 500107862016 bytes, 976773168 sectors

```

sda: SSD, Linux drive. Has always been the first drive. Grub's installed here.
sdb: Windows boot drive, up until last night. Was always in that position.
sdc: various data partitions, for various things.
sdd: more data (mostly Steam games)

sde is the new, completely unformatted SSD. Note that there are no partitions on it. I want to copy the Windows OS partition to this drive. (And it should be possible given some Windows utilities. I'm not asking about that move at all, this is certainly not the forum for it. I'm asking about booting.)

*Temporarily*, last night, I swapped sdb and sde. At that point, update-grub found the Windows install on what was then "sde", but when I tried to boot from it it failed. Now, I have restored the status quo above. The 1 TB drive is back as sdb; I have in no way modified the data in it. I have restored the 40_custom file to its previous state. This exact configuration worked fine before the swap. But now, even after I run update-grub, I can't boot Windows. I get the errors I mentioned.

I can tell that os-prober ran because, after I removed the 40_custom stuff, the custom menuentry disappeared when I booted into Grub. Here's the output of update-grub:

```
# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
```

It seems like os-prober is running...

---

### Post by oldfred on 2016-06-09
The script from Boot-Repair shows all the drives, but lots more detail on boot configuration.

---

### Post by sorceror171 on 2016-06-09
Our replies appear to have crossed. The boot info is available at: [http://paste2.org/XyzWOt6n](http://paste2.org/XyzWOt6n)

---

### Post by oldfred on 2016-06-09
Never seen this before:
>  /dev/block/251:0 2014-10-02-00-56-49-00 udf SAMSUNG SSD 



Did you dd the installer to the Samsung SSD?
UDF, I believe is the format of a DVD. And the dd copy to flash drive for an installer converts flash drive to a hybrid DVD/flash drive without partition table.
You have to erase MBR, first sector with dd, so you can create partition table and use MBR. 

But I prefer gpt for all Ubuntu only drives or data drives. If also Windows, Windows will only boot from gpt with UEFI, so if BIOS system, you have to keep Windows drive as MBR.

---

### Post by sorceror171 on 2016-06-09
No, that "SAMSUNG SSD", is, in fact, /dev/sr0, a BD-ROM optical drive. At this point, I have completely disconnected the new Samsung EVO 850 500GB SSD. It is not connected to any SATA port at all. The bootinfo covers only what was in the machine originally. Indeed, all disks are back in their original positions. This *exact* hardware configuration happily dual-booted two days ago.

For fun, this morning I disconnected the Hitachi SSD where Ubuntu's root partition resides (/dev/sda in the bootinfo) and tried to boot directly from the Windows disk. No dice. Note: I have made *no changes* to the Windows disk, besides briefly swapping the SATA port it was plugged into. I once mounted the lone partition on it, /dev/sdb1, under Ubuntu simply to confirm that I could communicate with the drive. I have not touched the MBR on that disk at all.

---

### Post by oldfred on 2016-06-09
I thought Windows had converted to something like Ubuntu's change from device like /mnt/sda1 to UUIDs. Or I also would expect it to boot ok.

I know with XP, its boot.ini was hard coded to a drive & partition and created big issues if drive moved. It even caused issues when booting sdb with grub and if no drivemap in grub chain boot to Windows would not be happy. It had to see from BIOS that boot drive was hd0.

I also know that UEFI loses boot entries if drive is disconnected. Is your system UEFI, even though your drives and installs are all BIOS? But would still think a BIOS boot of Windows would work. Just do not know details of what Windows uses/has in BCD and Linux cannot parse BCD to know.

---

### Post by sorceror171 on 2016-06-09
No, this MB is still in BIOS-boot mode. No EFI. I'm going to play around in the BIOS a tiny bit, try a couple different boot orders. The bootinfo notes some kind of MBR on sdd, maybe I'll try that.

If that fails, my current plan is to boot from a Windows 7 DVD and run its boot repair. This'll probably kill Grub, but I can use a live DVD to repair that. If anyone has alternate suggestions, I'm wide open to them...

---

### Post by oldfred on 2016-06-09
That probably is the best choice.
Best to have Windows boot loader in MBR of Windows drive, you may then be able to use f8 to get into its internal repairs. Otherwise your repair flash drive or installer's repair console are required.

Grub really only boots working Windows, and most Windows repairs cannot be done from Linux.

---

### Post by sorceror171 on 2016-06-09
Well, I got things resolved, and I didn't have to resort to boot repair disks. I finally went into the BIOS, and discovered that, when I had placed an unformatted disk in place of the Windows disk, it "helpfully" rearranged the boot priority on the drives. As soon as I'd restored the proper boot order, things worked just fine.

I've managed to boot Windows from the old disk, copy the OS partition to the new SSD, and boot then Windows from that. I really should have thought of this beforehand, but I'm old enough not to expect my BIOS to change settings on me automatically. Thanks for all the help!

---

### Post by sorceror171 on 2016-06-09
Well, I got things resolved, and I didn't have to resort to boot repair disks. I finally went into the BIOS, and discovered that, when I had placed an unformatted disk in place of the Windows disk, it "helpfully" rearranged the boot priority on the drives. As soon as I'd restored the proper boot order, things worked just fine.

I've managed to boot Windows from the old disk, copy the OS partition to the new SSD, and boot then Windows from that. I really should have thought of this beforehand, but I'm old enough not to expect my BIOS to change settings on me automatically. Thanks for all the help!

---

