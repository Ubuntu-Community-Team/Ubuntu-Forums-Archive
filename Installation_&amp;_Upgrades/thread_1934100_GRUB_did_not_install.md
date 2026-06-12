---
title: "GRUB did not install"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by meanmrmustard on 2012-03-01
I've just installed Oneiric but it would not let me install GRUB in either the MBR or within the Oneiric installation on sdd.
Searches have turned up nothing relevant to my situation.

I have two other installs the first drive (sda) holds Natty and it's GRUB lists all other options for booting each of the other installations.

Can I simply add an entry for the newest installation into the GRUB menu there, or must I run the install command to get all installs recognized?

There is no Windows installation to muck things up further.

---

### Post by mikewhatever on 2012-03-01
Yes, make sure the hdd is connected, then in Natty, run 'sudo update-grub'. That will perform OS detection and add all it finds to the current menu.

---

### Post by meanmrmustard on 2012-03-01
> **mikewhatever said:**
> Yes, make sure the hdd is connected, then in Natty, run 'sudo update-grub'. That will perform OS detection and add all it finds to the current menu.

It found the 11.10 installation but gave this error:
"/usr/bin/grub-probe: error: cannot find a GRUB drive for /dev/sdd1 Check your device.map

I found no device.map in /boot/grub

This... [http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html) wasn't particularly helpful to a GRUB2 newb like me.

---

### Post by mikewhatever on 2012-03-01
Check what's in /boot/grub/ of the 11.10 installation. That's what the OS-probber looks for. If there is no /boot/grub, or there is nothing in there, you'll have to reinstall grub from the 11.10 installation media.

```
sudo mount /dev/sdd1 /mnt

sudo grub-install --root-directory=/mnt /dev/sdd
```

---

### Post by darkod on 2012-03-01
You can create new device.map with:
sudo grub-mkdevicemap

sdd not having a corresponding entry in device.map might be because it didn't want to install.

Creating a new updated device map should do the trick. And you can install grub on the MBR of sdd with the commands mike gave you above.

---

### Post by meanmrmustard on 2012-03-01
> **mikewhatever said:**
> Check what's in /boot/grub/ of the 11.10 installation. That's what the OS-probber looks for. If there is no /boot/grub, or there is nothing in there, you'll have to reinstall grub from the 11.10 installation media.

It's there but it's not empty there are - *.mod, *.lst, *.img and a  locale dir. but no device.map
> 
```
sudo mount /dev/sdd1 /mnt

sudo grub-install --root-directory=/mnt /dev/sdd
```

So running this now would install GRUB - replacing all the files that are in /boot/grub presently?

---

### Post by meanmrmustard on 2012-03-01
> **darkod said:**
> You can create new device.map with:
sudo grub-mkdevicemap

Create the device.map *then* run grub-install? Sorry just want to make sure I don't hose everything.

> 
sdd not having a corresponding entry in device.map might be because it didn't want to install.

Creating a new updated device map should do the trick. And you can install grub on the MBR of sdd with the commands mike gave you above.

..."a corresponding entry in device.map"? I found no device.map in either /boot/grub - either Oneiric or Natty - there is a drivemap.mod in each - not the same thing?

And this will also pick up the other installs?
I figured I should probably put GRUB on sda - but I suppose it doesn't matter as long as it finds all 3 installs.

---

### Post by darkod on 2012-03-01
> **meanmrmustard said:**
> It's there but it's not empty there are - *.mod, *.lst, *.img and a  locale dir. but no device.map


So running this now would install GRUB - replacing all the files that are in /boot/grub presently?

No, that will only add grub2 to the MBR of /dev/sdd. In order to work correctly, all files within the installation on /dev/sdd1 have to be OK.

In case the grub installation within the OS failed or is corrupted, you can enter sdd1 with chroot and completely remove and reinstall grub2.

First try these two commands, if it doesn't work you can go with the longer way.

EDIT: You only need one grub to boot. Whether you want to use grub from sda, sdd, etc it's your choice. If you already have a working grub2 on sda that can boot all OSs, use that. It really makes no difference.

---

### Post by meanmrmustard on 2012-03-01
OK I've run grub-install - from Natty (sda) and now find an entry in /boot/grub for the 11.10  install at /dev/sdd1

I can't reboot right now but what about this device.map? It's still not showing.

---

### Post by oldfred on 2012-03-01
I remember they added device map with grub2. Then they removed it in newer versions, but there was a comment about using it if found. It was just a text file listing hard drives, but as I remember it was by device like /dev/sda and they wanted everything to be by UUID. So system is supposed to find all the devices as part of the boot process and does not have to have device map. It this an external drive that might changed order?

Even if booting from sda, it does not hurt to have the grub for the install in sdd in the MBR of sdd. Then if you have hard drive issues with sda, you can in BIOS select to boot from sdd. Grub remembers which drive it installed into, so you should update entry on reinstall device.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

I just noticed it shows if a device_map was regenerated:

```
fred@fred-LT-A105:~$ sudo debconf-show grub-pc
[sudo] password for fred: 
  grub2/kfreebsd_cmdline:
  [COLOR=RoyalBlue]grub2/device_map_regenerated:[/COLOR]
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/timeout: 10
  grub-pc/kopt_extracted: false
* [COLOR=Red]grub-pc/install_devices: /dev/disk/by-id/ata-FUJITSU_MHV2160BT_PL_NY07T6A28HNP[/COLOR]
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/mixed_legacy_and_grub2: true
fred@fred-LT-A105:~$
```

---

### Post by meanmrmustard on 2012-03-01
Thanks for the input!

> **oldfred said:**
> I remember they added device map with grub2. Then they removed it in newer versions, but there was a comment about using it if found. It was just a text file listing hard drives, but as I remember it was by device like /dev/sda and they wanted everything to be by UUID. So system is supposed to find all the devices as part of the boot process and does not have to have device map. It this an external drive that might changed order?

Can't help but wonder why, if device.map was removed, does the message tell me to check it since it might not exist.:confused:

It is an external USB drive, one of two identical drives. The first is simply for backups with a single large partition (now, I'm not sure if that was a good idea) and they do change between /dev/sdc and dev/sdd when only one is plugged in.

> 
Even if booting from sda, it does not hurt to have the grub for the install in sdd in the MBR of sdd. Then if you have hard drive issues with sda, you can in BIOS select to boot from sdd. Grub remembers which drive it installed into, so you should update entry on reinstall device.

I was thinking the same.

> 
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc


I ran the dpkg command and made sure GRUB was installed to /dev/sdd.

The command finished saying:
```
 Found Ubuntu 11.10 (11.10) on /dev/sdd1
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sdd1.  Check your device.map.
done
```

What is a GRUB drive? ...and don't I also need to run update-grub or something?... or is that already taken care of?

Then running the debconf-show command: 

before showing grub on sda
```
curt@Cocobolo:/etc/default$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30VZ44D
``` 

and after, also showing it on sdd
```
curt@Cocobolo:/etc/default$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30VZ44D, /dev/disk/by-id/usb-Seagate_GoFlex_Desk_NA0M1KSL-0:0
```

Without rebooting, how do I determine if it is installed or not?
<...and I was just starting to get the hang of GRUB :roll:>

---

### Post by oldfred on 2012-03-02
I think the error on device map is just the left hand (error message) not talking to the right hand (grub changes). You could report it as a bug and someday it may get fixed, but I am sure it will not be a priority unless it actually prevent systems from working and multiple users report the bug.

Is the Hitachi your sda drive? And what is the external? 

What name does sdd show:

Hard drive info:
sudo hdparm -i /dev/sdd
sudo lshw -class disk

---

### Post by meanmrmustard on 2012-03-02
> **oldfred said:**
> I think the error on device map is just the left hand (error message) not talking to the right hand (grub changes). You could report it as a bug and someday it may get fixed, but I am sure it will not be a priority unless it actually prevent systems from working and multiple users report the bug.

Is the Hitachi your sda drive? And what is the external? 

Yes the Hitachi is sda and internal
The external, sdd is a Seagate GoFlex
> 
What name does sdd show:

Hard drive info:
sudo hdparm -i /dev/sdd

```

curt@Cocobolo:/etc/default$ sudo hdparm -i /dev/sdd
[sudo] password for curt: 

/dev/sdd:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument
 HDIO_GET_IDENTITY failed: Invalid argument

sudo lshw -class disk
 *-disk
       description: ATA Disk
       product: Hitachi HDS5C302
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: ML6O
       serial: ML0220F30VZ44D
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d1faa
  *-disk
       description: SCSI Disk
       product: GoFlex Desk
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@9:0.0.0
       logical name: /dev/sdc
       version: 0D19
       serial: NA0M1SGR
       size: 2794GiB (3TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005657d

*-disk
       description: SCSI Disk
       product: GoFlex Desk
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdd
       version: 0D19
       serial: NA0M1KSL
       size: 2794GiB (3TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00067761


```

Something missing from the "hdparm" command?

---

### Post by oldfred on 2012-03-02
What ever error hdparm is seeing must be what grub2 is also having.

It may be related to 3TB drive or are drives the new 4K sector drives? Are you formated gpt or mbr? Not sure how MBR will work with 4K drive, but if in 512 mode you have to have gpt.

How large is your / partition? There was a bug which I do not know if they have fixed on very large (over 500GB) / (root) partitions.

---

### Post by meanmrmustard on 2012-03-02
> **oldfred said:**
> What ever error hdparm is seeing must be what grub2 is also having.

It may be related to 3TB drive or are drives the new 4K sector drives? Are you formated gpt or mbr? Not sure how MBR will work with 4K drive, but if in 512 mode you have to have gpt.

I'm not finding anything at Seagate but one reviewer at an online store says they are 4K sectors.
I formatted mbr, and the first time chose "align to sectors" (or something similar, not remembering exactly) the second time, just left the default setting in place.
> 
How large is your / partition? There was a bug which I do not know if they have fixed on very large (over 500GB) / (root) partitions.

/ partition is 28 G.

I just ran df -h and found that after the:
```

sudo mount /dev/sdd1 /mnt

sudo grub-install --root-directory=/mnt /dev/sdd
```

command, that "/" partition is mounted twice.
Did I mis-interpret that command?

```
curt@Cocobolo:/etc/default$ sudo du -xhs /
[sudo] password for curt: 
du: WARNING: Circular directory structure.
This almost certainly means that you have a corrupted file system.
NOTIFY YOUR SYSTEM MANAGER.
The following directory is part of the cycle:
  `/mnt' 
```


```

curt@Cocobolo:/etc/default$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda1              28G  6.0G   21G  23% /[/COLOR]
none                  4.0G  744K  4.0G   1% /dev
none                  4.0G  1.9M  4.0G   1% /dev/shm
none                  4.0G  424K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
/dev/sda7              51G   38G   11G  78% /home
/dev/sdc1             2.7T  1.3T  1.4T  48% /media/databackup
/dev/sdd1              60G  2.3G   54G   5% /media/4ff1228b-c26c-4f0f-a98d-62497532b04f
/dev/sdd6             2.7T  202M  2.5T   1% /media/3dfc4518-571f-4a91-bf16-231654dbc1c4
/dev/sda5             1.8T  1.4T  317G  81% /media/a541741c-37b5-475a-af8d-760b818bb066
/dev/sdb2              28G  1.3G   26G   5% /media/041b17fc-cd43-437c-a689-8ed56e8fee8b
/dev/sdb1              19G  4.5G   13G  26% /media/28766018-7c89-49af-a802-1f046ef56ed6
[COLOR="Red"]/dev/sda1              28G  6.0G   21G  23% /mnt
[/COLOR]
```



So I umounted /mnt 



...also that I never ran "sudo grub-mkdevicemap" ... but, not important, right?
<I probably shouldn't have been doing this on so little sleep>

---

### Post by oldfred on 2012-03-02
The two line grub install is to install grub from the liveCD or USB by mounting the partition on the hard drive to find the grub files and install to the hard drive MBR. Yes you mounted / twice they way you did it. Not sure what that did. New systems with grub 1.99 have a slightly different command also using /boot instead of /.

But if you are in  working install and want to reinstall grub or install to another MBR.

sudo grub-install /dev/sdd
Where the /dev/sdd can be any drive and you can install to several so they all boot your main install. I just suggest having on the same drive as the Ubuntu install. 

Another way that also makes grub update an internal setting for where grub will reinstall on major updates.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc


The correct commands for a liveCD and install in sda5 and installing to sda:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by maxijuni0r on 2012-03-03
I have a similar problem. I installed Ubuntu 11.10 on a LIVE FLASH USB ,  everything worked fine ...until first reboot when I get : no boot  sector on usb . 
Can someone please help ?

---

### Post by maxijuni0r on 2012-03-03
I tried to use the live CD but I can't mount the USB in Gparted...

---

### Post by meanmrmustard on 2012-03-03
I took the easy way out and re-installed.
This time from the desktop DVD version, 64 bit (last time I used the alternate install 32 bit, which ended up showing both USB hds under CD-ROMS in the BIOS!)
The installer again complained about not being able to install grub but this time it gave me the option to choose another location - so I typed "/dev/sdd" and the installation finished.

On rebooting it would not start using either hd in the first position booting order.

After rebooting the Natty install, with both drives showing in the file manager,
"sudo debconf-show grub-pc"
showed no entries on the "grub-pc/install_devices:" line

I then ran the sudo grub-install command (from the 11.10 install media, after mounting both /dev/sda and /dev/sdd) at /mnt), using :
--boot-directory=/mnt/boot /dev/sdd and again with /dev/sda as the targets.
Both commands were reported as successfully installing grub with no errors.

Once again neither drive would boot to the Oneiric installation.
Again, sda is the drive that holds the Natty install and the start screen there does show an entry for 11.10 on sdd, but choosing it I see:

error: <I'm not remembering what this line was.>
error:  You must load the kernel first.
Press any key to continue.

Before installing the first time (I did it twice today) I used the Parted Magic live disc to set up the partitions choosing GPT for the partition table. The "/" partition was 80 GB a 6 GB swap area and the balance as the /home directory.
The Ubuntu installer then saw that drive in a completely different way.
It showed only a total of around 327 GB and the /root partition showed as 7.8 GB. There were also two smaller partitions, one of about 700 MB and another even smaller. I don't remember the number but the /home partition was at least closer to what I told the installer to do.
I abandon that and just allowed the Ubuntu installer to partition and format, first deleting all partitions from the previous attemt to install and chose "new partition table".


Right now in the file manager, "Computer" choice under "places" it shows two icons for the drive:
3.0 TB Hard Disk: 2.3 TB Filesystem
and:
3.0 TB Hard Disk: 646 GB Filesystem

I must still be doing something wrong but cannot see what my mistake might be.

---

### Post by meanmrmustard on 2012-03-03
> I have a similar problem. I installed Ubuntu 11.10 on a LIVE FLASH USB , everything worked fine ...until first reboot when I get : no boot sector on usb . 
Can someone please help ?

You will probably have better luck getting noticed if you post a separate thread, sorry, I haven't got a clue.
What you've done here is referred to as "thread hi-jacking" 
Not a good idea for several reasons.

---

### Post by oldfred on 2012-03-04
I have used gpt on my 160GB and a 16GB flash drive without issue, but you have to create a bios_grub partition for grub to correctly install. Since I am hoping to get a new  system with UEFI soon, now added a efi partition as my first partition (for use with UEFI) and a bios_grub for BIOS. Bios_grub will then not be used with UEFI.

Did installer switch to UEFI mode when you formated to gpt? If system is UEFI it can use the efi partition or revert to BIOS mode and use bios_grub. Always best to format in advance.

BIOS Boot Partitio only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

---

### Post by meanmrmustard on 2012-03-04
> **oldfred said:**
> I have used gpt on my 160GB and a 16GB flash drive without issue, but you have to create a bios_grub partition for grub to correctly install. Since I am hoping to get a new  system with UEFI soon, now added a efi partition as my first partition (for use with UEFI) and a bios_grub for BIOS. Bios_grub will then not be used with UEFI.

Did installer switch to UEFI mode when you formated to gpt? If system is UEFI it can use the efi partition or revert to BIOS mode and use bios_grub. Always best to format in advance.

I didn't notice any change.
It's not a UEFI system.

> 
BIOS Boot Partitio only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

I have already reformatted this morning as gpt. Just now deleted the / partition and created a 1 MiB there and the rest as /.
We'll see what happens.

> 
Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

Thanks for the info!
As a side note, I'd like to try to install to the external drive while still running this Natty install. Would this be a "network install" or something else - or is this maybe not possible?
MoBo is not UEFI and no windows on this machine.

---

### Post by oldfred on 2012-03-04
Install to a second or external drive is just like an install to an internal drive. But you have to use manual install so you get the choice on where to install the grub2 boot loader. The install on the external should have the grub boot loader on the external and keep the grub for the install on the internal for the Ubuntu on the internal. A sudo update-grub will find both installs from each install, but of course when the external is not installed that boot will not work from the internal. If you do not install any proprietary video, you then can boot the external from other computers.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by meanmrmustard on 2012-03-04
> **oldfred said:**
> Install to a second or external drive is just like an install to an internal drive. 

I do understand that and have done many installs internal and external, but not 11.10 adn this is my first time installing the OS to a USB drive. 
Adding the other 3 TB drive was simple as it is one partition and only for back up - no bootable partition needed.

I could have been more clear/precise in my question.
I was hoping there was some way to copy files to the pre-formatted partitions and run them from within my present install - more of an experiment than anything but so I could continue using Natty during the install. I'm guessing this is at least complicated if not impossible.

I have always made /, swap and /home partitions only, except for my very first install - long ago (Mandrake 7.0 or so), which was /, and swap only.

So for my fourth attempt on this 3 TB USB external,
I made the gpt part. table along with the 1 MB partition and set the flag for the biosgrub as you suggested and also made a /boot partition, of 258 MB and / of 50 or 60 GB - I forget now and the rest, 2.7 or so TB for /home.

I then booted to the 64 bit alternate install disc. At the partitioning step chose "manual" and it reports /dev/sdc as this:
```

SCSI9 (0,0,0) (sdc) - 375.1 GB Seagate GoFlex Desk
                   128.0 kB        FREE SPACE
     #1            131.1 kB    K   biosgrub
     #4             33.8 MB
     #5              9.9 GB
     #2            366.9 MB
     #3            364.8 GB
                    57.3 kB        FREE SPACE

```

As you can see this is not even close to what I did when formatting with Parted Magic
Previous attempts have also reported sizes that are not what I made also using Parted Magic.

Not sure why the installer sees the partitions this way or whether this install would be successful if I went ahead and used the space as it is, although 9.9 GB is much too small for a /root partition.

If you have no further suggestions, maybe I'll just go with it and see what happens. I'm basically experimenting to see what I think of 11.10 anyway but if it is successful I would probably repeat the same procedure using a different (2 TB) disk for actual use.

Thanks again for your assistance and time.

---

### Post by darkod on 2012-03-04
Is Parted Magic a windows program?

I understand some people might use windows software and that if it says it can create linux partition it should work, but it's always best to do it with linux tools.

How good are you with parted, or cfdisk?

If you have no important data on that disk, try writing a new GPT table with parted, and creating the four partitions you need (the three you mentioned you always use, and the biosgrub).

PS. Another option is not to use GPT at all. Simply use msdos table on this disk, and it should work much better. Just make sure there is no backup gpt table leftover which might create confusion and issues. The cfdisk I mentioned I think it works with msdos only, not with gpt.

---

### Post by meanmrmustard on 2012-03-04
> **darkod said:**
> Is Parted Magic a windows program?

No, just a comprehensive Linux tool.
From Distro Watch site:
Parted Magic is a small live CD/USB/PXE with its elemental purpose being to partition hard drives. Although GParted and Parted are the main programs, the CD/USB also offers other applications, such as Partition Image, TestDisk, fdisk, sfdisk, dd, ddrescue, etc

> 
How good are you with parted, or cfdisk?

I can use either/both but I've been led to believe that the large disk (3 TB)needs GPT for a bootable installation in order to recognize and make use of the full size. Is this incorrect?
Previous attempts have not been successful using mbr - or gpt for that matter.

And why is the installer partitioner not reporting the sizes I've made the partitions?
Got the same screwed up result whether gpt or mbr!!??

---

### Post by darkod on 2012-03-04
You are right, I missed the fact it's a 3TB disk. You need gpt for above 2TB.

I understand your frustration, but I would say try once more with a new clean gpt table and the parted command line tool, not Parted Magic. Just to see how it goes.

---

### Post by meanmrmustard on 2012-03-04
> **darkod said:**
> You are right, I missed the fact it's a 3TB disk. You need gpt for above 2TB.

I understand your frustration, but I would say try once more with a new clean gpt table and the parted command line tool, not Parted Magic. Just to see how it goes.

Which command line tool will do gpt... parted doesn't do gpt, unless I'm getting more confused than I think?

Oh gdisk I guess. sgdisc seems to have gone away.

edit: yeah it's a bit frustrating but I do love the learning process and finding out what does and doesn't work, so it's all good.

---

### Post by darkod on 2012-03-04
Yes, parted can do it. You can enter the parted prompt with:

sudo parted /dev/sdc

On the prompt you create new blank gpt table with:

mklabel gpt

For other commands, the manual is:
[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

---

### Post by oldfred on 2012-03-04
I remember someone else with a 4K drive and the drive was seen as much smaller. I think in that case it was a bug in the drive's internals that had to be updated. Or maybe some partitioning tools worked on the 4K sectors as 512? Did not save any notes so not sure now on issues.

---

### Post by meanmrmustard on 2012-03-04
> **darkod said:**
> Yes, parted can do it. You can enter the parted prompt with:

sudo parted /dev/sdc

On the prompt you create new blank gpt table with:

mklabel gpt

For other commands, the manual is:
[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

Cool, thanks.

I just issued df -h from my Natty install and see:
(irrelevant partitions snipped)
```

Filesystem            Size  Used Avail Use% Mounted on

/dev/sdc5              73G  180M   69G   1% /media/_root
/dev/sdc1             992K   24K  920K   3% /media/f4948c28-fdee-4bc1-a694-2d311fe0037f
/dev/sdc4             250M  152K  237M   1% /media/_boot
/dev/sdc3             2.7T  202M  2.5T   1% /media/87c1e48b-0f88-471a-89fd-58fa9dce5d35

```

...from my last attempt with Parted Magic.
This is actually what it should be reporting.
sdc1 should be the 1 MB with the bios_grub flag.

The only thing that doesn't look right is no sdc2 - That wouldn't be swap would it? 
I only made primary partitions.

Now when I try to run the installer, all partitions are showing the wrong sizes.
How can I proceed if the installer partitioner is telling me lies?

---

### Post by meanmrmustard on 2012-03-04
> **oldfred said:**
> I remember someone else with a 4K drive and the drive was seen as much smaller. I think in that case it was a bug in the drive's internals that had to be updated. Or maybe some partitioning tools worked on the 4K sectors as 512? Did not save any notes so not sure now on issues.

Thanks oldfred, I'll research that and see what I find.

---

### Post by kmas on 2012-03-05
Hey guys, I don't know the rules for thread hijacking, and I'm sorry if it seems like i'm doing so, with your permission can I post the link to my thread to see if I can also get some help from olfred.

I've been following your thread from the beginning but our problems became different when you were attempting to install on a 2nd external hard drive. from the first page all the way through the second, the steps we followed are similar and got same results.

---

### Post by meanmrmustard on 2012-03-05
> **kmas said:**
> Hey guys, I don't know the rules for thread hijacking, and I'm sorry if it seems like i'm doing so, with your permission can I post the link to my thread to see if I can also get some help from olfred.

I've been following your thread from the beginning but our problems became different when you were attempting to install on a 2nd external hard drive. from the first page all the way through the second, the steps we followed are similar and got same results.

I only meant to suggest that to get the most exposure for your issue you're better off making a thread so more users see it, it's very likely to be missed by most if you post it in this thread.
Feel free to link to this thread. If there are things here that will help you, it would be a good idea.
Good luck and I'll be checking your thread also to see what advice is offered.

---

### Post by meanmrmustard on 2012-03-07
> **maxijuni0r said:**
> I tried to use the live CD but I can't mount the USB in Gparted...

Are you referring to my USB situation? or Kmas' usb flash drive?

(here's where thread hijacking becomes an issue - things can get confusing)

---

### Post by darkod on 2012-03-07
Have you tried what parted says about your disks? And whether you see what you expect?

You can print all disks with parted with:

sudo parted /dev/sda print all

---

### Post by meanmrmustard on 2012-03-07
> **darkod said:**
> Have you tried what parted says about your disks? And whether you see what you expect?

You can print all disks with parted with:

sudo parted /dev/sda print all



Yes... and BTW thanks for asking.
Here is what I've done this time.
I used the parted live disc 0.12-0.2 to create this:
```

/sdc2 bios_grub   5 MB - 200kB used (the 5% reserved for root) set the bios_grub flag here.
/sdc3 /boot       600 MB 25.92 KB used set the boot flag here.
/sdc1 /home       466.61 with - 7.51 GB used  
/sdc4 /swap       2.93 GB
/sdc5 as /data    2.27 TB - 36.67 GB used

```

Formatting... bios_grub as ext2, /boot as ext3 /home and /data as ext4.

...and this is all with the partition table as gpt.

Edit: yeah, I forgot /root (even though ubiquity shows it!!, see below.


I then went to install - from the 64 bit dvd
Ubiquity reports the partitions as:
```

128.0 KB               FREE SPACE
6554  K     Biosgrub               /boot
78.6  MB  B                        /root
62.66 GB (blank spaces here and for the next line)
393.1 MB
84.5  kB                FREE SPACE
312.0 GB                            /data
512.0 B                 FREE SPACE

```
If you're wondering where /root came from - since it isn't in the parted finished report, I just now realized that I hadn't even defined /root at all - so I don't know where it came from either.

As you can see this is not even close to what parted did and ubiquity doesn't recognize any file systems at all.

I have tried with previous attempts (at this point) to adjust the partitions sizes and fs types from within ubiquity with some success but the install usually fails trying to format the /boot partition (I think) - says it is 100% completed but it just freezes there.

Can't remember for sure now and my notes didn't mention it but either the alternate disc or the desktop disc allowed me "unformatted" choice for the bios_grub partition - so I did so and I proceeded from there with the installation.

The present install (re-re-re-re install) is right now sitting at the stage you see above (the ubiquity report) and I'm thinking that I should go back to parted, /home (sdc1) delete it and remake the resulting free space as /home and /root, then I'll have to get back into parted live cd and make bios_grub as unformatted, then try the install again.
I'm also thinking that I'm not understanding the partitioning process when using gpt and the bios_grub partition but so far haven't found any explanation, except for oldfred's advice.


Any other advice? or best guesses?

---

### Post by darkod on 2012-03-07
OK, you are all over the place. Hit the brakes, and take it easy. I know you are probably trying to get this working for a long time, but being impatient and trying too many things only makes it worse.

Tell us this: Are you trying to keep a /home partition on this disk with your next install or not?

Apart from that:
1. The bios_grub partition you created should not be ext2. Leave it without any filesystem, just create it with parted.
2. Drop the /boot partition you are trying to create. Unless you really, really need it, there is no benefit from it and just creates confusion. If you can install without it, do that.

Don't post the ubiquity installer partitions, simply boot into live mode and post the result of:
sudo parted /dev/sdc print

if you are only interested in /dev/sdc.

Also, what I have noticed from earlier posts, you seem to be mounting your second ubuntu on your first. Why? Do you really need to access it? Why would you mount at boot all the partitions, including root and /boot. I understand mounting a shared data partition, but not all partitions including root.
But that's a different subject, lets see what is going on with /dev/sdc right now. Post the parted list and don't do any more changes for a while.

EDIT: Temporarily disable the entries in /etc/fstab (if you have them) mounting your second ubuntu into your first, until you sort it out.

---

### Post by meanmrmustard on 2012-03-07
> **darkod said:**
> OK, you are all over the place. Hit the brakes, and take it easy. I know you are probably trying to get this working for a long time, but being impatient and trying too many things only makes it worse.



Could you explain how I can  "make things worse", short of damaging the physical disc?
 
I've done many installs, the only thing different about this one is, it's to a USB drive that's larger than 2 TB.

I've been trying every way I could imagine from a basic install on for a few days now without success. 
It's no big deal, I have all the time in the world and it will most likely be nuked in the end anyway. It's simply a learning exercise.
From my experience with Linux that's a good way to learn (trying different ways of doing things) - the more mistakes I make the the more I learn. 

I've found one person, so far who attempted a bootable Ubuntu install using GUID partitioning on a large disc on a PC.
He knows worlds more about Linux than I do and tried everything I have so far and got the same results - although he was attempting to build a Raid array on his machine.

May I ask, have you done this yourself?
> 
Tell us this: Are you trying to keep a /home partition on this disk with your next install or not?

I've included a /home partition with every attempt including the last as I showed in my previous post, so yes, I am including /home on the install.

> 
Also, what I have noticed from earlier posts, you seem to be mounting your second ubuntu on your first. Why? Do you really need to access it? Why would you mount at boot all the partitions, including root and /boot. I understand mounting a shared data partition, but not all partitions including root.

I don't know any reason to do this.
If you could point to where I did it I'd appreciate it.
> 
EDIT: Temporarily disable the entries in /etc/fstab (if you have them) mounting your second ubuntu into your first, until you sort it out.


I do not mount sdc's partitions on my main (if that's what you mean by 'first' installation.
There are no entries in my Natty install (or the other one's) fstab for sdc.



> 
2. Drop the /boot partition you are trying to create. Unless you really, really need it, there is no benefit from it and just creates confusion. If you can install without it, do that.


Ok I included the /boot because I've never done it before and thought this would be a good time to experiment with it.
> 
Don't post the ubiquity installer partitions, simply boot into live mode and post the result of:
sudo parted /dev/sdc print

if you are only interested in /dev/sdc.


/dev/sdc is is the only drive I'm working with.
I included the ubiquity report to show how wildly different it reported the partitioning.
And to get some advice on installing when it's reported partitioning is so far off from what parted does... and why it doesn't recognize files systems that I made with parted.

So tell me please if you can, how do I continue with the install when - for instance - the /root partition I made 60 GB is only 8 GB during the install.
```

# Start   End    Size   FileSystem Name  Flags
2 1049kB  6291kB 5243kB            /boot bios_grub
3 6291kB  635MB  629MB             /root boot
1 635MB   502GB  501GB       
4 502GB   505GB  3145MB
5 505GB   3001GB 2496GB            /data

```

---

### Post by darkod on 2012-03-07
I was wrong about the mounting thing. You are using an external disk and that's why after plugging it it is mounting itself on /media/...

Boot into ubuntu live mode. Unmount the external hdd if it mounts automatically. Try deleting the /boot partition from parted, it would be something as:

sudo parted /dev/sdc
print (to show the partitions again)

If partition #3 is still the 629MB partition, delete it with:

rm 3
quit

That will delete it and quit parted.

Check again if the partitions look "normal" with parted.

Then open Gparted and check the /dev/sdc layout shown there. Is it the same?

EDIT: I noticed something that may be your problem. The partition #5 says the begin/end is 505GB 3001GB. It's a 3TB disk so the max should be 3000GB. It seems somehow the partition is outside the disk. Try also resizing it with:

sudo parted /dev/sdc
resize 5 505GB 3000GB
quit

Check if the end is now at 3000GB. (if after deleting #3 the last partition is not #5 any more, make sure you take this into account and work with the correct partition)

---

### Post by meanmrmustard on 2012-03-07
I repartitioned a while ago without a /boot partition. Also I left the bios_grub partition unformatted.
Now we have:
# Start   End     Size    File System Name Flags
1 1049kB  2079kB  1049kB                   bios_grub
2 2079kB  68.8GB  68.8 GB                  boot    
3 68.8GB  589GB   520GB
4 589GB   30001GB 2412GB

Afterward, I booted to the 11.04 install disc again, and stopped at the partitioning step. At that point I abandoned the install and rebooted to Parted Magic live disc, ran sudo parted /dev/sdc as you suggested and the above is what it reports, except both flags were gone.
I reset them.

gparted is now showing - ext2 for /dev/sdc1, ext3 for sdc2, ext4 for sdc3 and sdc4

Attempting to resize #4, I plugged in the correct values, "resize 4 589GB 3000GB" and it complained:
Error: Could not detect file system, after a rather long warning:

                                                    
(parted) resize 4 589GB 3000GB                                          
WARNING: you are attempting to use parted to operate on (resize) a file system.
parted's file system manipulation code is not as robust as what you'll find in
dedicated, file-system-specific packages like e2fsprogs.  We recommend
you use parted only to manipulate partition tables, whenever possible.
Support for performing most operations on most types of file systems
will be removed in an upcoming release.
Error: Could not detect file system.

---

### Post by oldfred on 2012-03-07
If you do not want to modify partitions include the -l parameter or 
man parted
```

fred@fred-LT-A105:~$ sudo parted /dev/sdb unit s print
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 31375360s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4
 3      14749696s  29327359s  14577664s  ext4
 4      29327360s  31373311s  2045952s   ntfs

```

Note that bios_grub is not formated. You still install grub to sdX or drive like sda, sdb etc

---

### Post by darkod on 2012-03-07
Don't set the boot flag.

For GPT disks you use bios_grub, you have it on #1.
For MSDOS disks you use boot. Don't use it for gpt.

Turn it off.

Since it can't resize #4 and you have no data on the disk, try deleting it in parted with:

rm 4

Lets hope it can delete it.

I am still puzzled why it is allowing you to set the boot flag since that flag doesn't exist on gpt disks. Or maybe parted allows you to set it anyway. I hope there is no confusion about the partition table, having both msdos and gtp mix up.

EDIT: Also, you should get rid of the ext2 on sdc1. The bios_grub partition shouldn't have any filesystem, we mentioned that many times already.
I'm not sure how you delete the ext2 now. I guess it's easier to delete the partition, and just create it in parted with mkpart. That command only creates a partition, with no filesystem. That's what you need. Small partition with no filesystem and the bios_grub flag set.

---

### Post by meanmrmustard on 2012-03-07
> **darkod said:**
> Don't set the boot flag.

For GPT disks you use bios_grub, you have it on #1.
For MSDOS disks you use boot. Don't use it for gpt.

It's on #1 because I set it. If I didn't you wouldn't see "bio_grub" at the end of that line.
> 
Since it can't resize #4 and you have no data on the disk, try deleting it in parted with:

rm 4

Lets hope it can delete it.

It's not an issue, I've deleted that and other partitions many time in the last few days
> 
I am still puzzled why it is allowing you to set the boot flag since that flag doesn't exist on gpt disks. Or maybe parted allows you to set it anyway. I hope there is no confusion about the partition table, having both msdos and gtp mix up.

The flag DOES exist on gpt. oldfred told me that it needs to be set.
There is the option, under "advanced" to set the flag as bios_grub.
> 
EDIT: Also, you should get rid of the ext2 on sdc1. The bios_grub partition shouldn't have any filesystem, we mentioned that many times already.

In my last post I said that I *did not* format it.
It showed up as ext2 after starting the install again, abandoning it and rebooting to the Parted Magic Live disc.

Here's the line:
> 
Afterward, I booted to the 11.04 install disc again, and stopped at the partitioning step. At that point I abandoned the install and rebooted to Parted Magic live disc, ran sudo parted /dev/sdc as you suggested and the above is what it reports, except both flags were gone.
I reset them.
...and ext2 was now on the bios_grub partition which I DID NOT FORMAT, it was left UNFORMATTED.

---

### Post by darkod on 2012-03-07
oldfred was only talking about the bios_grub flag, not about the boot flag. Look at his post #42. Where do you see the boot flag set?

You did set bios_grub on sdc1 and that is correct.
What is not correct, if I understand it, is the boot flag on sdc2 and that should be turned off.

The idea with deleting partition #4 was to get rid of the 3001GB end point. If you do delete it, and then create new partition with parted, does it say 3001GB or 3000GB?

Try to create it with:
mkpart primary 589GB 3000GB

After that when you print the partition list with parted, does it show 3001GB or 3000GB?

I am trying to eliminate the possibility that an error like 3001GB in the partition table is making different programs show the disk layout differently.

As far as ext2 and sdc1, maybe you didn't format it in one of your last tries, but the point is that with so many reinstalls, maybe there was a moment when it was formatted as ext2 so it stays that way until changed. The parted manual says that only creating partitions doesn't create a filesystem on them. Depending how sdc1 was created and when.

---

### Post by oldfred on 2012-03-07
You set a boot flag if it is efi partition for UEFI boot. A boot flag in gpt is not really a boot flag like in mbr, but a gpt code of ef00. Where a bios_grub is ef02. Parted does not show the codes, but gdisk will.

In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same).

```
fred@fred-LT-A105:~$ sudo gdisk -l /dev/sdb
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 31375360 sectors, 15.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ECD862C9-27C6-44EF-846C-5272FE5A465F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31375326
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  KingstonData
   2            4096        14749695   7.0 GiB     0700  
   3        14749696        29327359   7.0 GiB     0700  
   4        29327360        31373311   999.0 MiB   0700  
fred@fred-LT-A105:~$ 

```

---

### Post by meanmrmustard on 2012-03-07
> **darkod said:**
> oldfred was only talking about the bios_grub flag, not about the boot flag. Look at his post #42. Where do you see the boot flag set?

My mistake, I was misreading your comment.

after deleting #1 (dev/sdc1) using gparted, I remade a 1MB and set the bios_grub flag and unset boot flag on sdc2.

Now it reports:
```

# Start       End         Size      (last fields are 
1 1.05MB      2.10MB      1.05  MB      empty,     
2 2.10MB      68.8B       68.8GB     except the 
3 68.8GB      589GB       520GB        bios_grub  
4 589GB       3001GB      2412GB       flag on #1)

```

Originally #1 was 2MB but it only let me make the new one 1MB. 1MB empty space at the start of the disk I guess?
I deleted 4 and tried:
mkpart primary 589GB 3000GB but it comes out 589 to 3001.
But if I say 2999 instead of 3000, that's ok.
I then ran rm 4 and tried again to do 589GB 3000GB and I got:
Error: Invalid number.

For the below, I'm looking at gparted - strangely it shows file systems for all partitions except #1 bios_grub (well it does show ext2 but there is now an exclamation mark in front of the fs type), while parted does not show any fs for any partition.
It also shows a 1.48 GiB unallocated space at the end. (the last mkpart I ran was 589GB 2999GB)

Is there something else I'm missing?

Maybe blow them all away and start over?... or? something else?
Here's a thought... change the units to 's' and set the 4's End number to the max, less 1 MB? Not sure what that number would be.

---

### Post by darkod on 2012-03-08
The idea with unit s is very good. That would be best.

On top of that, I agree just blew it all away, create new empty table.

When you use MB or GB you can see that the end of one partition looks same as begin for the next.
But when you work in sectors the begin and end shouldn't be the same. And it gives you more control.

So if #1 end at sector 100, create #2 starting at 101, it should never be the same.

And it's much easier to tell the last sector, just look at the total number of sectors.

The problems you are getting with this disk are really weird.

EDIT: If you are unsure how to read in sectors, it would be like:
Enter parted prompt.
mklabel gpt (new blank gpt table)
unit s
print (this will print all data, look at the total number of sectors next to /dev/sdc in the title. also note if one sector is 512B, it usually is, but you might have a disk with 4KB sector)

Depending if a sector is 512B or 4KB, 1MB would be equivalent to 2048 sectors or 256 sectors. So just deduct that from the total number and create #4 with that end sector.

---

### Post by meanmrmustard on 2012-03-08
> **darkod said:**
> The idea with unit s is very good. That would be best.

Yeah, except there's still an unaccounted for 1 MB missing - not that that really matters.

A disk larger than 2 TB does use 4 k sectors - this is the reason a bootable install must have GUID rather than mbr to see all 3 GB - or 2.7 actually.


I've removed all partitions except the bios_grub and am formatting a 49 GB /root, 400GB /home and 2.29 TB /data for the fourth.

My guess is when ubiquity gets to the partitioning stage it is not going to show the full space on the disk - on previous attempts it has showed only 4 or 500 GB as the total size. That along with reporting the /root partition as much smaller than I made it and having one or two areas of blank space with hundreds of GB. In the past, I adjusted that from within ubiquity and may have to again, since although gparted makes the correct sizes, Ubuntu installer doesn't seem to recognize them.


I'll be getting to the install as soon as gparted is done setting it up and report back the results.

Well see what happens this time without /boot - might make a difference.

Two questions, do you know if ext4 for the /root partition a bad idea - seems like a while back it was not recommended - maybe it's not a problem today?

I have also asked if you have installed to a large (greater than 2 TB drive) before but you did not answer.

---

### Post by darkod on 2012-03-08
I am still running dual boot on 250GB disk. No money for 2TB. :)

ext4 is perfectly fine. Even before I think it wasn't an issue with problems, it was more of a precaution by some people not using ext4 immediately after it was released. I have used it since it was available, haven't seen any issues.

Lets hope your latest try works.

I am wondering if the live cd has some "issues" with your disk. One option would be trying with the alternate cd, with or without partitions created in advance.

---

### Post by meanmrmustard on 2012-03-08
> **darkod said:**
> I am still running dual boot on 250GB disk. No money for 2TB. :)

ext4 is perfectly fine. Even before I think it wasn't an issue with problems, it was more of a precaution by some people not using ext4 immediately after it was released. I have used it since it was available, haven't seen any issues.

Lets hope your latest try works.

I am wondering if the live cd has some "issues" with your disk. One option would be trying with the alternate cd, with or without partitions created in advance.

I started with the alternate install media. Got the same result from the desktop version too.
I'm starting to think it's the drive's firmware, but then, the one guy I talked to got the same results. I don't know if his hd was WD, Seagate, or something else. 3 TB is fairly new so there may be some issues with bootable installs. I  know the big drives are supposed to work with Windows 7, not Xp or anything else but I haven't read anyone who has done it with Windows.

I decided to try Linux Mint this time partitioning looked good but the sizes were incorrect maybe once it's done it will look different.

Another 10 or 15 minutes I'll know.

---

### Post by darkod on 2012-03-08
> **meanmrmustard said:**
> I started with the alternate install media. Got the same result from the desktop version too.
I'm starting to think it's the drive's firmware, but then, the one guy I talked to got the same results. I don't know if his hd was WD, Seagate, or something else. 3 TB is fairly new so there may be some issues with bootable installs. I  know the big drives are supposed to work with Windows 7, not Xp or anything else but I haven't read anyone who has done it with Windows.

I decided to try Linux Mint this time partitioning looked good but the sizes were incorrect maybe once it's done it will look different.

Another 10 or 15 minutes I'll know.

OK. But note that the original alternate install might have failed in the grub install step because of missing bios_grub partition. The partition layout might have been good (I'm just speculating here).

So, if you remember after so many attempts, where the failure was, it might be worth giving the alternate another shot.

What I would do to avoid any issues with bios_grub:
First boot live mode with the live cd, use parted to make a new gpt table and to create the bios_grub partition, set the flag on.
Then start the install with the alternate, and create the /, /home and swap during the alternate install using the manual method.

If that fails there is not much more you can do because you are doing things correctly.

---

### Post by meanmrmustard on 2012-03-08
> **darkod said:**
> OK. But note that the original alternate install might have failed in the grub install step because of missing bios_grub partition. The partition layout might have been good (I'm just speculating here).

So, if you remember after so many attempts, where the failure was, it might be worth giving the alternate another shot.
Eventually I learned about the bio_grub partition - Thanks again to oldfred - and wiped everything starting with a new gpt and the bios_grub partition with all newly made and formatted partitions - no difference with either the desktop or alternate install media. Just to be sure I'm doing it again today with both media.
> What I would do to avoid any issues with bios_grub:
First boot live mode with the live cd, use parted to make a new gpt table and to create the bios_grub partition, set the flag on.
That's what I did the last couple times and again before trying Mint... which btw seemed to have installed but would not boot. The other thing about Mint is, while I still had the live disk in, I opened gparted and looked at the info for the #1 partition and it claimed msdos. This was after the install. So I'm wondering if the desktop installer somehow changed the partition table automatically.
Opened gparted from the live disc (Ubu 11.10) and saw that only the reserved kernel space was used on the partitions. Weird!
I'm trying a desktop install (Ubu 11.10) right now to see what happens, then I'll try the alternate disc again.> 

If that fails there is not much more you can do because you are doing things correctly.

If that fails, then it's time to look more closely at the hd's firmware - maybe there's an update. I'll try talking with Seagate customer support <shudder>  if I must.
The 4K thing is, more and more, looking to be the likely problem.

I'll post the final result here... eventually, along with any new info I might find.

---

### Post by oldfred on 2012-03-08
I still do not know 4K drives, but some more info on them.

See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Are you by any chance using a new high speed 6Gb/s SATA port. There were(are?) issues with them working correctly. Not sure if design or software as they were supposed to be backwards compatible.

---

### Post by meanmrmustard on 2012-03-08
> **oldfred said:**
> I still do not know 4K drives, but some more info on them.

See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Are you by any chance using a new high speed 6Gb/s SATA port. There were(are?) issues with them working correctly. Not sure if design or software as they were supposed to be backwards compatible.

Thanks for the links.
No it's USB 3, though inside the enclosure, I'm thinking it's probably SATA

---

### Post by oldfred on 2012-03-08
I believe there are similar issues with USB3. Try installing from a USB2 port.

---

### Post by meanmrmustard on 2012-03-10
> **oldfred said:**
> I believe there are similar issues with USB3. Try installing from a USB2 port.

Why not... I think I've tried everything else.
Thanks again.

---

### Post by meanmrmustard on 2012-03-11
> **oldfred said:**
> I still do not know 4K drives, but some more info on them.


I've just now been told that mbr will handle my 3 TB drive!!??

Have I missed something?

---

### Post by oldfred on 2012-03-11
Maybe with the 4K? But do you want a 30 year old partitioning system or the newer gpt system that has a backup and is designed for newer systems?

[http://www.wolframalpha.com/input/?i=3TB+in+TiB](http://www.wolframalpha.com/input/?i=3TB+in+TiB)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

