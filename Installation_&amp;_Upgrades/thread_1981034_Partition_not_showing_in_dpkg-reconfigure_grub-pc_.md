---
title: "Partition not showing in dpkg-reconfigure grub-pc (grub2) menu"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by roomey on 2012-05-16
I am trying to install grub boot loader on a partition  /dev/sda3 (ext3 formatted), but it is not showing as an option when I  run dpkg-reconfigure grub-pc.
  My details are: I have a dual boot system set up with windows fully encrypted on sda1.  It is encrypted using truecrypt, so truecrypt is required on the mbr of  sda. I will briefly outline the steps I have taken (NB- This is dangerous,  backup your boot sector first, or even better your whole HDD):
  
[LIST]
[*]Encrypted windows on sda1 using truecrypt
[*]Ubuntu 12.04 installed on extended partition sda5 (within sda2) I  need a logical partition to install grub, it will not work on extended) -  so I shrunk sda5 by 20 MiB and then shrunk sda2 by the same
[*]This allowed me to create a new logical partition sda3. I formatted it as ext3 and gave it the boot flag
[*]I started up a live boot disk, mounted /dev/sda5 to /mnt, and installed grub using```
 grub-install --force --root-directory=/mnt /dev/sda3
```
[*]This allowed me to restart and boot into ubuntu normally, happy days.
[/LIST]
  At this point, after I boot into ubuntu normally, I usually run dpkg-reconfigure grub-pc.  If I don't do this, any update to grub, or a new kernel, will overwrite  the main mbr of sda. In ubuntu 10.04 this is fine, I go through the  menu, and it usually gives me the option to install grub onto whatever  partition I want, but now, when I run it, it only gives me two options:  /dev/sda or /dev/sda5 (/dev/sda3 is missing).
  Have I taken a step which stops /dev/sda3 showing up in this menu? Is  there a way to fix this, or could you tell me how I can manually change  the debconfig properties to get grub to install to /dev/sda3 by  default.
  Thank you!
      
NB.I posted this on askubuntu, but there is so little traffic, I was hoping somone might be able to shed some light, even if they could explain how to manually change debconf values for grub-pc

---

### Post by roomey on 2012-05-16
I used [http://feeding.cloud.geek.nz/2010/10/manipulating-debconf-settings-on.html](http://feeding.cloud.geek.nz/2010/10/manipulating-debconf-settings-on.html) to manually set the dpkg (debconfig) flag. I had to use this command (nb. this is dangerous, dont use this as a copy paste solution)

    echo "set grub-pc/install_devices /dev/disk/by-id/ata-TOSHIBA_MK1646GSX_481JF04DS-part3" | debconf-communicate 

There is more detail in the link above which should help with most debconf issues

---

### Post by oldfred on 2012-05-16
Your dpkg command should have reset your reinstall location.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

This does let you select partitions, although not normally recommended. Your case with Truecrypt is one of the exceptions.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not (normally) choose partitions

---

### Post by roomey on 2012-05-17
Hi Oldfred,

> **oldfred said:**
> 
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not (normally) choose partitions

This is the way I usually have done this task in the past, but this time the menu was missing one of my partitions. I'm not sure if the partition was missing a flag, or if it was because I created the partition after I installed kubuntu. I suspect the latter, but for the life of me I could not find where ubuntu had a list of the partitions (like a device.map) nor how to update that list. I agree with you that it would be better to be able to configure through the menu as opposed to manually accessing debconf.

---

### Post by oldfred on 2012-05-17
A couple of versions ago, grub2 obsoleted device.map, but the commented they would use it if found. If you have an old device.map that might cause issues?

Grub2 just scans for all drives & partitions. Not sure if it just looks at partition table or scans system.

But most Linux tools do not see partitions they cannot mount. So if it has issues then it may not be shown.

---

### Post by roomey on 2012-05-18
Hi Oldfred,
I appreciate the help.  It was a brand new 12.04 install, on a disk already containing win xp, so there was no device.map. I thought the "device.map" held info on the disks, and not the actual partitions anyway. I thought mounting/formatting may be a problem, so I tried the partition as both ext2 and ext3, and also mounted and unmounted (using /etc/fstab).
Unfortunately I am no coder so I cannot check the logic behind the dpkg-reconfigure installation location menu. To be honest I am not sure if this is even a grub issue, as grub installs fine on the sda3 partition (I tested by wiping the partition boot sector using dd, and just using muon to reinstall grub).
In this case it would be good to know where dpkg-reconfigure gets its menu items from.

---

### Post by oldfred on 2012-05-18
Post this as then we can see where everything is installed.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by roomey on 2012-05-25
Hi Oldfred, 
Sorry for the delay, it is a company laptop unfortunately so I havent had access to it for the last week. From memory everything is installed like so (NB, partition numbers are out of order, (due to me creating the third partition after everything was installed) The HDD is partitioned as below (in this order):

/dev/sda - mbr = Truecrypt boot loader
/dev/sda1        = encrypted partition (win vista)(boot flag)
/dev/sda3        = 20mb ext3 used for grub boot loader
(partition 2 is extended, and includes)
/dev/sda5        = / ext4 main ubuntu install
/dev/sda6       = 2GB encrypted swap

---

### Post by oldfred on 2012-05-25
Boot-Repair also will force an install of the grub2 boot loader to a PBR.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

Another choice is just use a USB flash drive to boot Ubuntu, if you have the choice in BIOS. If system it really locked down (like it should be, if security is a major concern) then you may not have that choice.

---

### Post by roomey on 2012-06-01
> **oldfred said:**
> Boot-Repair also will force an install of the grub2 boot loader to a PBR.

Hi Oldfred,
Thanks for your help with this. The system is working fine now, there is no outstanding problem, so I deffo dont want to re-install any boot loaders!

No, my real question is why dpkg-reconfigure grub-pc did not give /dev/sda3 (a valid ext3 partition) as an option. Perhaps it has some sort of sanity check which does not display geometrically out of order partitions. I dont know where to begin looking for the answer however, not sure if the problem is with grub or dpkg-reconfigure

---

### Post by oldfred on 2012-06-01
I know it used to show all partitions. But I just reran it and it now only shows all drives and only the install (root) partition.

There were many issues with users overwriting Windows NTFS partition boot sectors and corrupting Windows and/or overwriting other systems that I think they decided only to allow the root (and boot?) partitions as choices. You may be able to use the manual command and force it into another partition, but I have not tested that.

---

