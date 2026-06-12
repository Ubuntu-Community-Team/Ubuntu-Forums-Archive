---
title: "can't access Ubuntu 10.04 after Windows upgrade."
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by johnson094 on 2011-03-26
Hi, 
 
I have been using Widows XP and Ubuntu 10.04 on separate hard drives for some time without a problem.  On boot up I choose between the OS.  Recently, I upgraded to Windows Vista and now on boot up it goes directly to Windows.  I realize the MBR has changed, but as a novice I have no idea how to reset the boot program or Grub.
 
Any help or direction to a tutorial would be greatly appreciated.  I know I can just reinstall Ubuntu, but I'd rather learn to do it this way.
 
 
thanks 
 
david

---

### Post by Hedgehog1 on 2011-03-27
Reinstall Grub on Hard Drive from Live CD

Please boot off your LiveCD/LiveUSB, select TRY

Determine what partition holds your Ubuntu root.  In the examples below, the assume that /dev/sd**b1** is your Ubuntu partition.  Yours may be /dev/sd**b5** or /dev/sd**a3** or /dev/sd**b3** or whatever...  Use that.  Also note that your drive MAY be /dev/sd**b**.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**b1** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**b**
```

***The Hedge***

:KS

---

### Post by johnson094 on 2011-03-27
Hi,
 
Sorry for taking so long getting back, I am working on one computer trying to get Ubuntu working and responding on another.  Tried to give you some screen shots but the "try me disk" seems to be unstable and locks up when I try.  
 
Basically, I opened Gparted and found my root directory to be sdb1.  I copied and pasted your code as it is in your response.  End reult was "installation complete...no problems reported".  I closed, removed install disk and rebooted...it went straight to windows.
 
Noticed your 2nd code line referred to sdb rather than sdb1 , is that correct?
 
Appreciate your help
 
David

---

### Post by oldfred on 2011-03-27
You have installed grub2's boot loader to drive sdb's MBR, but then in BIOS or using a one time boot key to test (F12 on my system) you have to choose to boot sdb. 

BIOS is probably set to default to sda. BIOS loads rest of boot code from MBR - Master Boot Record. And MBR is small, so today all that does is call more boot code on the hard drive.

---

### Post by johnson094 on 2011-03-27
Thanks Oldfred,
 Are you saying go to BIOS and boot my secondary hard drive first?

---

### Post by johnson094 on 2011-03-27
That did it, thanks to Hedgehog and Oldfred , notice in posts you are always there to offer help.
 
David

---

### Post by oldfred on 2011-03-27
Glad it worked.:)

Grub has a nasty habit of installing to sda.

You may want to check where it thinks to reinstall when a grub update occurs.
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
It will show a hard drive by name like mine which I have to know is really my sdc:
```
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD6400AACS-00G8B1_WD-WCAUF1779071

```And if that is sda, then you can update it to remember to install to sdb:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You also can see the drives with this:
sudo lshw -C disk

The grub install device is the drive & serial number shown above.

---

### Post by johnson094 on 2011-03-28
oldfred
 
You lost me on that advice.  I take it that from time , update may tru to update my gub and I want to direct it to my root which is sdb1?  Sorry to be so lame but I missed your point.
 
David

---

### Post by oldfred on 2011-03-28
Grub has hidden away a setting on which drive to reinstall. You will eventually get an update that reinstalls grub to the MBR. The setting determines which drive. It may then reinstall to sda. You just need to check which drive and then change it if it is wrong.

If not sure post this:

sudo debconf-show grub-pc

and this:

sudo lshw -C disk

And tell us which drive is which. If not sure look in BIOS.

---

### Post by johnson094 on 2011-03-29
Okay here are the results:

[QUOTEdavid@david-desktop:~$ sudo debconf-show grub-pc
[sudo] password for david: 
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD2500JB-00REA0_WD-WMANK5909508
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/timeout: 10
david@david-desktop:~$ ^C
david@david-desktop:~$ 
][/QUOTE]

and the second result is :

> david@david-desktop:~$ sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: WDC WD2500JB-00R
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 20.0
       serial: WD-WMANK5909508
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b7b1b7b1
  *-disk:1
       description: ATA Disk
       product: WDC WD3000JB-00K
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 08.0
       serial: WD-WMAMR1479445
       size: 279GiB (300GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009b170
  *-cdrom:0
       description: DVD reader
       product: CDW/DVD TS-H492A
       vendor: TSSTcorp
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HP02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVD RW DRU-820A
       vendor: SONY
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.0b
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: Photosmart D110
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 1.00
       capabilities: removable
       configuration: ansiversion=5
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@3:0.0.1
       logical name: /dev/sde
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@3:0.0.2
       logical name: /dev/sdf
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@3:0.0.3
       logical name: /dev/sdg
david@david-desktop:~$ 


My Ubuntu hard drive is Drive 1 

-disk:1
       description: ATA Disk
       product: WDC WD3000JB-00K
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb

Is this the info you needed?

David

---

### Post by johnson094 on 2011-03-29
oldfred,

I went back and read your last posts a little closer and now understand what you were saying and after reading the output of the first code command, I see that  YES grub is set to install to Disc 0  my Windows hard drive.
> * grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD2500JB-00REA0_WD-WMANK5909508I need to change that in the grub2 commands, can you help me?

Thanks so much

David

I used your directions for changing the boot config  and was able to highlight the correct drive sdb but when I rechecked it remained sda.  I tried several times but it would not change.

---

### Post by oldfred on 2011-03-29
We had/have this a lot on external drives. Then users who fixed it wondered why it was broken later after a grub update.

This should solve it. It run the installer version on reinstall that should reset where to install.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then confirm that it has changed:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by johnson094 on 2011-03-29
Okay, I ran the command to reconfig, I highlighted the sdb drive, and hit "enter" and this was result

[QUOTEInstallation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
][/QUOTE]

I then tried to run the line to check results and got:

[QUOTEdavid@david-desktop:~$ - grub-pc/install_devices:
-: command not found
david@david-desktop:~$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD2500JB-00REA0_WD-WMANK5909508
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/timeout: 10
][/QUOTE]

The drive has not changed.
[IMG]file:///tmp/moz-screenshot.png[/IMG]


Sorry, oldfred......I realized I was not actually selecting the correct drive by using spacebar, I was just highlighting the drive.  I corrected this and rechecked and now the correct drive is shown.  I should be good to go.  Right?

Thanks again for your help and your patience.

David

---

### Post by oldfred on 2011-03-30
That should do it. 

You are welcome.

---

