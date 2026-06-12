---
title: "copy of running xubuntu 8.04 hd install to cf via usb"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2011-02-04
Hello all,

I'm running a toughbook cf-m34 PIII 400mhz/40gb/512m. curently have xubuntu 8.04 on a conventional HD and want to mirror the build onto a 8gb CF. I know i have to crank the partition down to make it fit, but i'm stuck after that.
in ubuntu you can create bootable usb media, but i want to replace the HD with the CF & IDE-CF convertor, so it wouldnt be a USB device after the build and hence the sda and Hda links would fail

Any info would be great.

---

### Post by oldfred on 2011-02-04
What boot choices does you BIOS give your. Only BIOS controls booting as BIOS jumps to MBR of next device. If the device is not on list then you cannot boot.

Some workarounds are to boot a kernel with whatever boot device is allowed and in effect chroot into your install on the cf card. 

This is just booting grub but you could add a kernel:
Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

There also is plop which I think does something like above.
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by petebarchetta on 2011-02-05
It's the unhelpful panasonic bios that doesn't allow USB boot and floppy boot options are limited to panasonics own floppy drive and little else, machine also has no CDROM so booting a live cd is a nogo
But plop maybe an option to get round the USB boot although at that point it would have the cf card in the drive bay so I'm not so sure how that would work?
With the hd in I can see the device from the xubuntu desktop as a USB cf device through the caddy  and change things on gparted so I'm ok from there to build it as jfss filesystem to minimise writes as ext3/4 kills cards. 
What issues arise from dd copying an ext3 onto a jfss system?
Also what commands need to be run to clone system over?

---

### Post by oldfred on 2011-02-05
I do not use dd. Many swear by it, others swear at it, since it is easy to miss type something and destroy system.
Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


While for a USB flash drive, I would think some of the general  info would apply to your case.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

I have never cloned a system, since I converted to clean installs I install the system and update with  all my installed apps. I only backup /home, some settings from /etc  where I have manually edited the file, /data where most of my data is, a  current run of boot info script to document system, & a current  list of apps.

---

### Post by petebarchetta on 2011-02-07
hello,
cloning the system is academic, it was merely an afterthought.I can backup the home folder and save the synaptic markings.
Ideally I want to set the 8Gb CF up to behave like a normal HD, looking at the ubuntu app that allows you to create USB bootable media i think it wouldnt work as the card and its convertor will end up inside IDE channel rather than hanging off the USB bus. I cant see an easy way of doing it, any assistance would be great

---

### Post by oldfred on 2011-02-07
Do you mean something like this?

[http://www.amazon.com/Syba-SY-IDE2CF-NB25-Compact-Adapter-2-5-Inch/dp/B001B19HGA](http://www.amazon.com/Syba-SY-IDE2CF-NB25-Compact-Adapter-2-5-Inch/dp/B001B19HGA)

---

### Post by petebarchetta on 2011-02-08
Slightly different design, but yes like that.
I have stuck it in a USB caddy and xubuntu can see it, I've repartitioned it through gparted into 3 bits all as ext3 and it's now ready for dd, just have to crank down the hd partitions then it should work


Code:
dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror

This should work for each of the partitions
Sda being source partition and sdb being the destination partition, you can check this by running 
Sudo fdisk -l
Please correct me if I'm wrong

---

### Post by petebarchetta on 2011-02-11
Hello all,

ran a ubuntu lynx usb key up through a tecra m5, all bits and bobs found, i then tried to build the usb creator option, all went ok using a xubuntu 8.04 iso as the source, drive checked after build. when the install tells you to reboot and remove all the non booting media that you used to install it the only USB device left "the CF-IDE" unit then drops to busy box shell after starting up.
I'll try to grab the logs, but i dont think it will have stareted logging by then?

any ideas?
its seems there are others havbing similar issues:
[http://ubuntuforums.org/showthread.php?t=1266132&highlight=compact+flash]("http://ubuntuforums.org/showthread.php?t=1266132&highlight=compact+flash")

---

### Post by oldfred on 2011-02-11
There were some issues with some versions of syslinux, not sure if they apply to you or not.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

The USB creator is not a full install, but the installer/LiveCD. You can make it persistent to save some data.

---

### Post by petebarchetta on 2011-02-16
> **oldfred said:**
> There were some issues with some versions of syslinux, not sure if they apply to you or not.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

The USB creator is not a full install, but the installer/LiveCD. You can make it persistent to save some data.

i assume the only proper way to make a full install would be a DD over from another drive?

---

### Post by oldfred on 2011-02-16
I use grub2 to loop mount the ISO directly and install from that. I just installed Natty in about half an hour from one USB flash ISO to another as a full install.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This is a script to install many ISOs. Some that will not loopmount so it also installs a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

