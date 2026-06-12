---
title: "Installing Lucid iso from another partition by booting from grub2"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by deepclutch on 2010-05-07
Hello ,

I am having 9.10 Karmic  with **grub2** on /dev/sdb5 partition.I want to use this partition for Debian later on.

I've partitioned /dev/sdb6 to **ext4** and Plans to install Lucid on this Partition.I have downloaded Ubuntu LUCID amd64 iso on to /dev/sdb7 from where I hope to trigger installation using grub2.
But ,grub2 fails to find the image/partition.
here is the grub2 menu I've put on:
```
menuentry "Lucid ISO on /dev/sdb7" {
insmod ext2
set root=(hd0,6)
loopback loop /lucid/ubuntu-10.04-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid/ubuntu-10.04-desktop-amd64.iso noeject noprompt 
initrd (loop)/casper/initrd.lz
}
```^As (hd0,6) it boots /dev/sdb which is the First Harddisk 160GB one.But ,if I do a fdisk - l  "/dev/sdb" is the First Hdd ,While /dev/sda (80GB) is the 2nd One!
Is this related to the problem of not finding /dev/sdb ? I tried (hd1,6) but it shows the 80GB partition :(

Please Help:

[LIST]
[*][B]/dev/sdb5 -Current distro Ubuntu Karmic with Grub2
[/B]
[*]**/dev/sdb6 -where I intent to install Lucid**
[*]**/dev/sdb7- where Ubuntu Lucid ISO is stored**
[/LIST]
With Lucid iso on  / directory of /dev/sdb5(on karmic) ,I successfully booted into livecd environment and even tried Ubiquity to install.but ,it asks to unmount /dev/sdb5(which is the distro) which is an issue preventing installation.even if I formatted /deb/sdb7 and swap using gparted ,the installation fails because of asking to umount /dev/sdb5(/isomount) by installer.

---

### Post by deepclutch on 2010-05-07
My bad!Actually , /dev/sdb7 has to be denoted as (hd0,7) inside grub2!and it worked!.But ,sadly it asks to umount the partition /isomount(/dev/sdb7) during installation procedure :( ..

**I want to know if it is possible to have the iso copied to ram(ramdisk?) and initiate installation process?Any Idea?**

---

### Post by deepclutch on 2010-05-07
My PC has only 2 GB RAM.My thought was to copy the Ubuntu ISO into RAMDISK and initialize installer(ubiquity) from RAMDISK and after partition done ,enable SWAP partition on /dev/sdb .

Help is Appreciated.Any Leads?

Currently ,I am following  these Howtos:


[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

[http://ubuntuforums.org/showthread.php?t=182764](http://ubuntuforums.org/showthread.php?t=182764)

---

### Post by oldfred on 2010-05-07
I do not have an answer. 

The extended parition is mounted if any of the logical partitions inside are mounted. We ususally see this with gparted when editing logicals and the entire extended is mounted because gparted uses swap, so you have to swapoff. Is there anyway to use a primary? I do not know gpt partitioning,  but I understand all partitions are primary, but that requires other changes also.

---

### Post by deepclutch on 2010-05-08
of course, swap was turned off.I've all Linux Logical Partitions.
What I wanted to know is ,Inside the Livecd booted from ubuntu iso(via grub2),Anyway to install Ubuntu to the same harddisk where iso is also stored in one of the partition?I've read in some mailing lists that We can install from live  cd(booted from iso) using Ubiquity installer ,to partition of Any Other Hard Disk other than the Original Hard Disk where the ISO is stored.

I tried Ubiquity many times.but each time it asks for to umount /isodevice ,which is the partition where the Ubuntu ISO is stored!See the Screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156064&d=1273340410[/IMG]


[FONT=Tahoma][SIZE=3][COLOR=SeaGreen]_**So ,Only Solution,I think is to edit the Ubuntu-desktop-iso to reduce some MB's and make the Ubuntu Livecd copied to ram(RAMDISK) and boot from there.I really wanted to do this.**_[/COLOR][/SIZE][/FONT]

Of course ,there are alternate ways like using usb drive ,I will try that as a last resort.:-k

Regards,
DC

---

### Post by ic2 on 2010-05-09
"*[COLOR=blue]I really wanted to do this[/COLOR]*."
 
deepclutch, those were almost my exact words. I think we're trying to do the same thing. I can only dream of the speed and other benefits of such an install and it's blowing my mind ... WoW!!! Did you find a way to do it?
 

Install from INSTALLATION-CD on Hard-Disk
[http://ubuntuforums.org/showthread.php?s=f85bd633afeb19b233255d54a6](http://ubuntuforums.org/showthread.php?s=f85bd633afeb19b233255d54a6)

---

### Post by deepclutch on 2010-05-10
> **ic2 said:**
> "*[COLOR=blue]I really wanted to do this[/COLOR]*."
 
deepclutch, those were almost my exact words. I think we're trying to do the same thing. I can only dream of the speed and other benefits of such an install and it's blowing my mind ... WoW!!! Did you find a way to do it?
 

Install from INSTALLATION-CD on Hard-Disk
[http://ubuntuforums.org/showthread.php?s=f85bd633afeb19b233255d54a6](http://ubuntuforums.org/showthread.php?s=f85bd633afeb19b233255d54a6)

Hi ,
I am posting from My New install of Ubuntu Lucid using Ubuntu Alternate CD ISO booted from /dev/sdb7 partition.Alternate CD uses Debian Installer.:)

The Idea of copying to ram was not resolved.But ,Debian Installer in alternate cd by default copies to RAM(/dev/tmpfs).I will experiment with live cd iso copied to ramdisk at a later time.
--
With Debian Installer(Which is text/ncurses based) ,it asks to Mount Ubuntu CD when booted from hard disk iso.What I did was ,to symlink(symbolic Linking)  Lucid Alternate cd ISO to /dev/sr0(Which is the device file for dvd drive) .Then If I ask debian-installer to retry to mount cd ,it got mounted!
```
ln -sf /yourubuntuisodirectory/ubuntu.iso /dev/sr0
```After that the installation was smooth.ofcourse ,I had already formatted ext4 partition for Lucid install.but, partman partitioner is available in the installer.

^^^^of course!it is a crude method.moreover udev can overwrite the changes(umounting iso).But ,for the sake of iso install on *same* partition ,it worked.
Moreover ,inside debian-installer ,it can mount lucid desktop cd also(it searches).But ,I never tried.:rolleyes:

I am interested in to getting know how to copy iso to RAM DISK.I hope someone will answer this.

Regards,
DC

---

### Post by hatebreed on 2010-05-10
what were the commands to get grub 2 to boot to the iso in the first place, I tried this many times with no luck.

---

### Post by wilee-nilee on 2010-05-10
In interesting idea, but what are you going to do if you, need the ISO on a thumb or CD.

---

### Post by deepclutch on 2010-05-10
> **hatebreed said:**
> what were the commands to get grub 2 to boot to the iso in the first place, I tried this many times with no luck.
I used grub2 boot loader for Ubuntu karmic already on hard disk.

I used Ubuntu-Lucid **Alternate CD**.
Edit as 
```
sudo nano -w /etc/grub.d/40_custom
```Mine as example:    Lucid ISO is at /dev/sdb7)
```
menuentry "Lucid-Alternate ISO" {
insmod ext2
set root=(hd0,7)
loopback loop /lucid/ubuntu-10.04-alternate-amd64.iso
linux (loop)/install/vmlinuz  iso-scan/filename=/lucid/ubuntu-10.04-desktop-amd64.iso noeject noprompt  --
initrd (loop)/install/initrd.gz
}
```^^^ change the partition number accordingly, save the file .
Then update-grub
```
sudo update-grub
```^^^the entry will appear in grub2 menu on reboot.
Alternate CD directly boots from tmps invoking debian-installer(CLI).It searches for CD/DVD Drive instantaenously.You can open anoter virtual terminal by clicking ALT+F2 and ENTER.There You can symlink Ubuntu ISO tothe device file of your DVD Drive (most probably /dev/sr0/sr1 etc...) as shown in earlier post.

As  Regarding Ubuntu Desktop CD to boot from grub2 menu ,It is also possible this way.but ,the "Ubiquity" installer will abort the installation ,since it asks to unmount all partitions.
here it is:
```
menuentry "Ubuntu Desktop ISO" {
insmod ext2
set root=(hd0,7)
loopback loop /lucid/ubuntu-10.04-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid/ubuntu-10.04-desktop-amd64.iso noeject noprompt -- 
initrd (loop)/casper/initrd.lz
}

```Good Luck!

---

### Post by primski on 2010-05-11
nice job

you think it's possible to do it with LiveCD which doens't have text based installer and i can't make the symlink before mounting ?

or if grub could load the iso from network drive ? perhaps through samba on remote computer? can it do that?

---

### Post by deepclutch on 2010-05-11
@primski:ubuntu desktop cd(live cd) is obviously can be booted from iso.(I already tried that,If I understand your question correctly) .One Idea is ,boot a minimal cd with debian installer.it can search partitions for Linux ISO.in that way ,ISO can be mounted and install may be possible?

Yes,it is obviously possible to have the iso mounted to DVD Drive device file in Desktop CD Live Session.But ,the Idea had not struck Me while doing Ubuntu Live CD :mrgreen: (Silly Me!!!) .Ofcourse,Someone can try and report here.but ,one thing is ,udevd  may umount the device file randomly.means, do the symlinking only before launching installer(Ubiquity).

as regarding installation through local lan,I have not much Idea.may be multiple ways exists.I've done few RH/Fedora installs many years back.But ,I don't remember anything.Was it through SSH :rolleyes:
[https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations]("https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations")

--
Meanwhile,These all hassles will not occur ,if we copy the iso directly to RAM(RAMDISK).debian installer(alternate cd) mounts itself in /dev/tmpfs default. I've tried "toram" bootparameter and it seems to not work for Desktop CD.Do We Need to Mention "RAMDISK_SIZE=xyz kB" in grub2 line starting with "linux (loop)/casperinux ..."?What is the general format to copy iso to RAM?

---

### Post by primski on 2010-05-11
ok, thanks for ideas. i will give it a try later on when i come home from work.

i will also try putting iso on my SD card, which is USB device and it should work too in theory. Meanwhile, none of this hassle would be needed if i had an empty cd/usb stick or spare hdd in my laptop :) so worst case scenario, im buying an empty cd and burning it, but doing it through iso is so much easier (in the long-run when u know how to do it :) )

thanks again

---

### Post by deepclutch on 2010-05-11
@primski:Obviously,I've usb drives.But ,wanted to experiment :D.With USB Drive ,There is not much difficulty.

Thanks and Good Luck For your  install using USB(Pleanty of Guides are available in this forum itself?)

---

