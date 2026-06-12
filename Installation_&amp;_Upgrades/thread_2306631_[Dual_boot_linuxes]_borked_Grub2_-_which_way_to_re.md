---
title: "[Dual boot linuxes] borked Grub2 - which way to recover?"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by lliseil on 2015-12-17
Hi, installing a dual boot Ubuntu Trusty and Mageia 5 GNOME on a brand new rig for an old man. 

Note: As suggested by the dates on my profile I'm not an Ubuntu crack though I have a >ten years old GNU/Linux Xperience. 

In short:

[LIST=1]
[*] Decide in advance which Linux is to be in charge of the boot loader: Ubuntu (since LTS has the longer live support it should preferably be in charge of the bootloader management)
[*] Partitionned the disks, MBR/msdos, logical volumes but for /boot
[*] Installed **Mageia 5 x86_64 **from the Network ISO, Grub leagacy on the MBR, rebooted: all is fine.
[*] Installed **Ubuntu Gnome x86_64** from the Network ISO, rebooted, GRUB2 « do you wanna update Grub (installed) and replace it on the MBR? » yeap, rebooted: no OS entry will boot. a check shows the most borked grub.cfg of all times
[*] Any attempt to update-grub2 resulted in a similarily borked, unusable bootloader; *SuperGrub2Disk* (Ubuntu = busybox, Mageia OK); from Mageia (os-prober and Grub2); and from chrooted Ubuntu (LVM related error on update-grub2)
[/LIST]

Some details
If something's missing just say it please, I'll add ASAP (have running ssh access to the box)

Box and Partitions
------------------------------

It's a nice simple office station with a Pentium(R) CPU G3250, 4096 MB DDR3 RAM, and a MSI MS-7817.

```
120 GB SSD KINGSTON SV300S37A120G 
+-------+-----------------------------------+-------+
| /boot | VG1 (lv_{mageia,ubuntu,home,swap} | libre |
+-------+-----------------------------------+-------+

500 GB Seagate Barracuda 7200.14
+-------+-------------------------------------------+----------+
| /sdb1 | VG2 (lv_data)                             | libre    |
+-------+-------------------------------------------+----------+
```
blkid
```
/dev/sda1: LABEL="boot" UUID="c78bb5cd-a401-4cd2-aa32-69222d8c6876" TYPE="ext4" PARTUUID="ffc2da47-01"
/dev/sda2: UUID="MBob8w-JQaI-p9Li-bWxA-ypoM-bOV8-7XDV6J" TYPE="LVM2_member" PARTUUID="ffc2da47-02"
/dev/sdb1: LABEL="boot2" UUID="7727dafa-4b8f-4faf-b28a-fc236c576d21" TYPE="ext4" PARTUUID="7970ac30-01"
/dev/sdb2: UUID="mYYRMi-sOUq-89Dq-7TVo-mroS-oexp-s5btOv" TYPE="LVM2_member" PARTUUID="7970ac30-02"
/dev/mapper/vg_ssd-mandriva: UUID="8c0524c8-ca40-4766-9d6f-fa674f689898" TYPE="ext4"
/dev/mapper/vg_hdd-donnees: LABEL="donnees" UUID="e67fcf28-4946-40e9-bd58-9f10e77f949c" TYPE="ext4"
/dev/mapper/vg_hdd-swap: LABEL="swap" UUID="3d509caf-23f3-4640-ad24-19147cedd470" TYPE="swap"
/dev/mapper/vg_ssd-ubuntu: UUID="f6bcbea1-1f09-4a10-a1b4-12a6a8605c32" TYPE="ext4"
/dev/mapper/vg_ssd-home: LABEL="home" UUID="49ae653b-8c70-429c-b31c-c2d1fd03e1c1" TYPE="ext4"
```

OSes 
---------------
100% default install. Only configured the users, S.M.A.R.T. monitoring and ssh.
Couldn't boot into Ubuntu but through a chroot

**/boot/grub/menu.lst** by Mageia 5
```
timeout 10                                                                                                                                                              
color black/cyan yellow/cyan                                                     
gfxmenu (hd0,0)/gfxmenu                                                          
default 0                                                                        
 
title linux                                                                      
kernel (hd0,0)/vmlinuz BOOT_IMAGE=linux root=/dev/vg_ssd/mandriva  splash quiet noiswmd
root (hd0,0)                                                                     
initrd /initrd.img                                                               
 
title failsafe                                                                   
kernel (hd0,0)/vmlinuz BOOT_IMAGE=failsafe root=/dev/vg_ssd/mandriva  failsafe noiswmd
root (hd0,0)                                                                     
initrd /initrd.img
```

**/boot/grub/grub.cfg** by Ubuntu 15.10 (full 700 lines availbale [https://ptpb.pw/3RMs](https://ptpb.pw/3RMs))
```
<SNIP>
### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f6bcbea1-1f09-4a10-a1b4-12a6a8605c32' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1 --hint='hd1,msdos1'  c78bb5cd-a401-4cd2-aa32-69222d8c6876
	else
	  search --no-floppy --fs-uuid --set=root c78bb5cd-a401-4cd2-aa32-69222d8c6876
	fi
	linux	/vmlinuz-desktop root=/dev/mapper/vg_ssd-ubuntu ro  splash quiet $vt_handoff
	initrd	/initrd-desktop.img
}
submenu 'Options avancées pour Ubuntu' $menuentry_id_option 'gnulinux-advanced-f6bcbea1-1f09-4a10-a1b4-12a6a8605c32' {
	menuentry 'Ubuntu, avec Linux desktop' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-desktop-advanced-f6bcbea1-1f09-4a10-a1b4-12a6a8605c32' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1 --hint='hd1,msdos1'  c78bb5cd-a401-4cd2-aa32-69222d8c6876
		else
		  search --no-floppy --fs-uuid --set=root c78bb5cd-a401-4cd2-aa32-69222d8c6876
		fi
		echo	'Chargement de Linux desktop&#8230;'
		linux	/vmlinuz-desktop root=/dev/mapper/vg_ssd-ubuntu ro  splash quiet $vt_handoff
		echo	'Chargement du disque mémoire initial&#8230;'
		initrd	/initrd-desktop.img
	}
	menuentry 'Ubuntu, with Linux desktop (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-desktop-init-upstart-f6bcbea1-1f09-4a10-a1b4-12a6a8605c32' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1 --hint='hd1,msdos1'  c78bb5cd-a401-4cd2-aa32-69222d8c6876
		else
		  search --no-floppy --fs-uuid --set=root c78bb5cd-a401-4cd2-aa32-69222d8c6876
		fi
		echo	'Chargement de Linux desktop&#8230;'
		linux	/vmlinuz-desktop root=/dev/mapper/vg_ssd-ubuntu ro  splash quiet $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial&#8230;'
		initrd	/initrd-desktop.img
	}
	menuentry 'Ubuntu, with Linux desktop (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-desktop-recovery-f6bcbea1-1f09-4a10-a1b4-12a6a8605c32' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1 --hint='hd1,msdos1'  c78bb5cd-a401-4cd2-aa32-69222d8c6876
		else
		  search --no-floppy --fs-uuid --set=root c78bb5cd-a401-4cd2-aa32-69222d8c6876
		fi
		echo	'Chargement de Linux desktop&#8230;'
		linux	/vmlinuz-desktop root=/dev/mapper/vg_ssd-ubuntu ro recovery nomodeset 
		echo	'Chargement du disque mémoire initial&#8230;'
		initrd	/initrd-desktop.img
	}
<SNIP>
```

Refs I (should have) used
--------------------------------
- [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)  Unless I'm blind it lacks any information for dual booting Linuxes
- Mageia has a nice page on how to add another distro for an easy multi-booting choice (but it's Mageia driven) [http://www.mageialinux-online.org/wiki/gestionnaire-d-amorcage-grub-et-multiboot](http://www.mageialinux-online.org/wiki/gestionnaire-d-amorcage-grub-et-multiboot)
- Clear, seems I should have go like him: [https://letchap.github.io/2013/04/03/dual-boot-lubuntu-mageia-2-lxde/](https://letchap.github.io/2013/04/03/dual-boot-lubuntu-mageia-2-lxde/)

QUESTION
Any guess why did Ubuntu Grub2 produce this terrible grub.cfg
How would you handle this, preferably without a full reinstall of both OSes :-} THank you

---

### Post by oldfred on 2015-12-17
Best to see all the details. You can run from Ubuntu live installer, maybe from Mageia or from Boot-Repair's own live system?
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Are you using LVM because you want full drive encryption?

My own preference is not to use LVM logical partitions over MBR, and to use gpt partitioning anyway, but that is me.

---

### Post by lliseil on 2015-12-17
Yeah I saw Boot-repair but it's all graphical, so I couldn't include it yet. Is there a CLI version? For I have cli access to the box by chrooting in from the running Mageia. Am not physically close.

I'd like to know for the future. As I realise the version I installed via the Network Installer is Wily, when errrr we want *Trusty*. So it appears I'll have to install the proper Ubuntu anyway, hopefully keeping the other distro.

If so, what's the best way to avoid further troubles with the [dual] boot manager: Have the other distro uses its own on its PBR and then have Ubuntu's Grub2 chainloads it?

---

### Post by oldfred on 2015-12-17
With two drives, just be sure to keep each install totally on its own drive including its boot loader. Grub from each should find the other and in BIOS you can set which to boot by default.

Boot-Repair include a lot of additional info, and can reinstall grub. You can just boot Ubuntu installer and add Boot-Repair.

This is boot info script which Boot-Repair runs and is about the first third of Boot-Repairs report.

 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

With more than one install, or more than one drive, worthwhile to run bootinfoscript or Boot-Repair's report regularly. I actually run an update to bootinfoscript as part of my regular backup script.

---

### Post by lliseil on 2015-12-20
OK, here's the boot-info

Obtained it from ubuntu-gnome "Wily" also x86_64 (1)

[http://paste2.org/hZfYOewc](http://paste2.org/hZfYOewc)

It's super powerful indeed. Please do not take in account the Mageia configuration, which I edited ten minutes ago (two days after the initial issue)

> =================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-raid enable-lvm) and reinstall the grub2 of dm-2 into the MBRs of all disks (except USB without OS), using the following options:        sda1/boot,
The boot flag would be placed on mapper/vg_ssd-ubuntu.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems

I'll go with Ubuntu LTS install, but would reaaaly like to get what happened here, and why. Your view are welcome :}

(1) As for the delay I could not activate the network from the chrooted ubuntu system so here I am only now, at my father's place.

---

### Post by oldfred on 2015-12-20
I do not know LVM, but it looks like both installs are using sda1 as /boot. That normally leads to mass confusion on kernel and grub files. 
You need to make sure each drive is totally separate, if not specified correctly during a Something Else install, then better to just disconnect each drive for other install.

---

### Post by lliseil on 2015-12-21
Thanks oldfred though my way is to use SSD for systems, and spinning disks for the data.

Second Ubuntu install (this time with 14.04.3 Mini 64bit) gave me much more light on what happened.

The other Linux now has its /boot on its own partition, thus does not use /dev/sda1 as shown in its fstab:
```
# Entry for /dev/sda1 :
UUID=c78bb5cd-a401-4cd2-aa32-69222d8c6876 /mnt/sda1 ext4 noauto,noatime,acl 1 2
```

Ubuntu install went well. Only base packages then choose sda1 for /boot » format YES » install to /dev/sda YES. Reboot, removed the usb key. [COLOR="#FF0000"]Cannot start[/COLOR].

OK. But this time we know why it did so: As you can see from the [boot-info log]("http://paste2.org/f5PY3vsh") launched after booting with SuperGRUB2Disk , the Ubuntu Trusty installer did see the SSD as the *THIRD disk* of that machine:
```
# /boot was on /dev/sdc1 during installation
UUID=c78bb5cd-a401-4cd2-aa32-69222d8c6876 /boot ext4 noatime 0 2
```
While blkid, boot-info or the other Linux all see it as the *first disk*:
```
/dev/sda1: LABEL="boot" UUID="c78bb5cd-a401-4cd2-aa32-69222d8c6876" TYPE="ext4" PARTUUID="ffc2da47-01"
```
Thus where did it install the bootloader? In the MBR of... the USB stick used for install, Yeah :-({|=
Thus booting after installing Ubuntu succeeded yeah, if inserting one of the two stick!
Note: 
Looking at boot-info logs I noted that *Wily* acted the same creazy way!
As a result the two USB sticks I used were borked untill I reinstall syslinux on them.

Run boot-repair and Ubuntu booted. Log [http://paste.ubuntu.com/14120821/](http://paste.ubuntu.com/14120821/)

That's what I get atm. Now I can hardly imagine a nastier bootloader manageemnt. Took me hours: one to correct my initial single /boot setup which was wrong, and a few more to understand and correct the result I got by using the Ubuntu installer! Can't remember seeing another one mixing things like that amongst the ~two hundred distros I installed in the last decade. Think how a newcomer would have handled that?
Learnt three things: 1. Pay special attention if I have to mixing distro's /boot again. 2. Do not trust Ubuntu installer to handle GRUB2. 3. Yann's Boot-info/repair is amazing.

---

### Post by oldfred on 2015-12-21
We have seen a few systems that promote flash drive to first drive or hd0 in grub or sda in Ubuntu. And that leads to major issue as you found with default install of grub. Only with Something Else do you have the option on which drive to install grub2's boot loader into, and it still defaults to sda. I have installed too quickly and had it install to wrong drive, also.

But with both of my Desktops drive enumeration is strange. It seems I skipped a port on SATA port order. So sda is always sda, but flash drive which is sde or sdf (as I had added another drive), but on reboot flash drive becomes sdb and every drive changes up one letter. On newer UEFI system same thing as DVD was hd1 in UEFI but Ubuntu saw hard drive as sdb.

Also which ever drive you boot from is always hd0. Old system I booted from sdc or sdd and that was always hd0 and every other drive was in SATA port order.

I was only able to keep track and understand with bootinfoscript which now is part of Boot-Repair and Boot-Repair's Summary Report. Highly recommended for any system with multiple drives or multiple installs.

---

### Post by lliseil on 2015-12-21
Amen ;)

I'd like to check but AFAIK the Installer » Partitionning did show the internal SSD as sda --not a USB stick, thus installed Grub2 on sda1. And then proposed me /dev/sda to install the MBR... Thus choose the USB stick. Logic, I'd do the same if high on booze.

This is a flaw in the Ubuntu bootloader installer.

---

