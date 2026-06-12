---
title: "External Hard Drive with Grub, Ubuntu and Live Ubuntu"
date: 2016-04-04
forum: Installation &amp; Upgrades
---

### Post by Walter_Scott on 2016-04-04
Hey folks,

I have an external hard drive, wanted to create something like a "ubuntu live usb"-partition. I found some solutions in the web, but i actually want to access "ubuntu live" via a grub entry, since i also want to install a working ubuntu version on that hard disk (and to be ambitious, i wanted to install also a win 7 recovery option, but this is not that important). 

I have a partition table with MBR and the following partitions:

sdb1 420 GB NTFS, primary
sdb2 5 GB Ext4, primary boot
sdb3 25 GB NTFS, primary
sdb4 50 GB Ext4, primary

I tried to do it with the "Startup Disk Creator", but he does not recognize the partitions (and i put the "boot"-flag to sdb2 with GParted). 

[B]So my first question is, is there a way to put a live ubuntu on sdb2, a recovery windows on sdb3 and a running ubuntu on sdb4?

[/B]I did not find any answers to that, so I thought about the option of placing an ubuntu iso file in a ubuntu version on sdb4, and creating a grub entry pointing to that iso. 
So I installed ubuntu 14.04. amd64 on sdb4 and installed also grub. 

I followed instructions of this link:

[http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

in particular i added the following lines 

```

menuentry “**Ubuntu 14.04 ISO**” {
set isofile=”**/home/name/Downloads/****ubuntu-14.04.1-desktop-amd64.iso**”
loopback loop **(hd1,4)**$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash
initrd (loop)/casper/initrd.lz
}

```

to the file /etc/grub.d/40_custom. I checked the locations of vmlnuz.efi and initrd.lz so these should be correct. 
But when i run update-grub there comes an error message, saying that the syntax of these lines is incorrect. 
I was thinking that maybe **(hd1,4)** is not correct, since its the entry of the grub on sdb, and this should be independent of the number if externals connected, so i took 
**(hd0,4)** instead, and update-grub did not give me any errors. Than i tried to boot into the live usb partition, 
and i got some errors:

/init:line 7: can't open /dev/sr0: No medium found

this line comes around 100 times. After 2 minutes he gives me some information about my hardware, and then he says 

(initramfs) Unable to find a medium containing a live file system. 



So 

[LIST]
[*]"Unable to find a medium containing a live file system", does this mean, the grub entry did not point correctly to the iso?
[*]Or does it mean, that my computer did not manage to scan the external hard drive in a certain amount of time? I found some similar cases in the web, and some people wrote, that with more power (usb3.0) the problem did not appear. But this computer does not have a usb 3.0 port, and i would like to solve that independently of that.
[LIST]
[*]Does the fact, that the iso file is placed in the end of my hard disk, influence my computer to find it? I didnt want to place the ubuntu system in the beginning, since i wanted to put there a ntfs partition for data, which is readable windows (i read that there are some problems, and windows does only recognize the first partition)
[*]I read something about a boot partition, is this maybe going to solve this problem?
[/LIST]
[/LIST]


I know I could solve this situation by two usb sticks and a live cd. But i am curious about this, and i only have one usb stick, and i think this should be possible.

---

### Post by grahammechanical on 2016-04-04
Have not tried to do what you are trying to do but about the syntax error, this is the kind of syntax used in /boot/grub/grub.cfg

> set root='hd1,msdos7'

So, you are correct about Grub seeing hd1 as the second hard disk but incorrect with (hd1,4). Perhaps. Maybe (hd1,msdos4) instead. Is there a 4th partition on hd0 (sda)? Is there a Linux kernel in /boot/ on that partition? Not having that would produce the "No medium found" message.

Regards.

---

### Post by yancek on 2016-04-04
Change your entry to that shown below and try it.

> menuentry “**Ubuntu 14.04 ISO**” {
set isofile=”**/home/name/Downloads/****ubuntu-14.04.1-desktop-amd64.iso**”
loopback loop **(hd1,4)**$isofile
linux (loop)/casper/vmlinuz.efi boot=casper findiso=$isofile quiet splash
initrd (loop)/casper/initrd.lz }

If that doesn't work try this.  Also, the (hd1,4) would be correct if the drive the iso is on is seen as sdb4.

> menuentry “**Ubuntu 14.04 ISO**” {
loopback loop **(hd1,4)**/**home/name/Downloads/****ubuntu-14.04.1-desktop-amd64.iso**
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=/home/name/Downloads/**ubuntu-14.04.1-desktop-amd64.iso** quiet splash --
initrd (loop)/casper/initrd.lz
}

Both/either should work.  If they don't, try moving the Ubuntu iso to the boot or / (root) directory and change the path as appropriate.

---

### Post by Walter_Scott on 2016-04-04
Thanks for answering:)

@[**[COLOR=#000000]yancek [/COLOR]**]("http://ubuntuforums.org/member.php?u=1928724")I did both, placing the iso file in root or boot and also chaning the menuentry, there is no effect. The output is the same.

@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") 	 I did change it back to **(hd1,4)** now he justs reboots into the grub menu. No i do not have a partition sda4 with linux. I have only the partitions on sda3.
Seems logical that hd0,4 points the sda4, i was just confused the first time, when he gave me a syntax error to hd1,4 (i thought he checked if there exists a forth hard disk, and therefore i assumend that grub sees hd0 as the disk, where it is living)
Anyway now he just does nothing, he reboots into the grub menu:/

---

### Post by oldfred on 2016-04-04
It depends on which drive's grub you use.
The boot drive from BIOS is always hd0, so if booting from sdb, it probably is hd0.

And you have to think of location on drive before normal mount in Ubuntu. Or as looking from a live installer.

So since not mounted the ISO cannot be in /home anything since /home is not mounted.

This is my entry in grub2's 40_custom, but I was booting from sdc or sdd, and /iso is a folder on sdb:
```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

I use configfile as I always forget to rerun grub-update on an ISO update in my ISO folder. But the livecdimage.cfg is then just a text file with all the standard boot stanza, but is in the /iso folder with all the ISO.

This is the configfile on my flash drive, this is booting from a grub on flash drive and /iso is the only folder in the 4th partition:
```
menuentry 'Live ISOs' {
configfile (hd0,4)/iso/livecdimageUSB.cfg
} 

```

This is first entry, I have many, and a different flash drive where /iso was in partition 5, booting with grub on flash drive so hd0.\:

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs on SSD' {
# configfile (hd0,5)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;
# debian-live-8.0.0-amd64-kde-desktop.iso

menuentry "Ubuntu 16.04 xenial Daily amd64" {
    set isofile="/xenial-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,2)$isofile 
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

```

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by Walter_Scott on 2016-04-05
@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") 
My home folder is not in an extra partition. In the grub menu, I started command line mode, and inserted all the commands in my menuentry manually, and it worked. But then i booted, and the same error as before came. And i checked before with ls which device i have to take, it was (hd0,4) but anyway, the result is the same. I get always 

/init:line 7: can't open /dev/sr0: No medium found

Also i dont see any essential differences between my menuentry and those of the links, besides replacing "quiet splash" by "noeject noprompt" which i will try now.

EDIT: I did try, and the result is the same.

---

### Post by oldfred on 2016-04-05
Not finding it is a path or device setting.
Must be some minor typo difference between grub menu and manually typing it if manual entry works.

Which grub are you using to boot with, from sda or sdb?
Did you manually install grub to sdb, or is it also a full install?

---

### Post by Walter_Scott on 2016-04-05
I installed the grub on **sdb**, after I installed ubuntu 14.04 on sdb4. The grub is on **sdb not on sdb4**.

As I installed grub on sdb, it showed also the boot entries of sda, I removed them with the tool grub-customizer ([https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)) then, i added the iso entry. Then I ran update-grub, saying that there are some syntax errors. I ran boot-repair and installed grub ONLY on sdb, 
I checked it afterwards, booting without the external plugged in directly in an os on my computer without grub, and with the external into the grub. (Finally i left the entries for my os on sda as they were, since this is only a question of aesthetics).
Then i readded the iso entry.

---

### Post by oldfred on 2016-04-05
Then the grub you have on sdb, is based on sda. And even the Boot-Repair install of grub is still based on your install on sda.

If you want a totally independant flash drive you have to install grub to it and manually edit the grub.cfg, not the 40_custom in your install.
Either actually should work, I have used both to boot ISO.

       Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

---

### Post by Walter_Scott on 2016-04-05
Thanks. I will try this and present the results.

---

