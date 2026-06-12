---
title: "trouble installing 8.04 to fakeraid-0 set"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Marco7 on 2008-05-19
I did this once with gusty 7.01 using the following guide, for the most part.

[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation")

Basically I install dmraid, used fdisk to partition and format my hard drives, and then ran the installer from the live CD to install most of the system files, but had to install some others, dmraid, Grub, and configure the grub manually afterward.  It worked!

Hardy Heron seems to work even better, and the installer seems to complete installation without any problems (i.e. does not report that the grub was unable to install), however, on reboot it hangs after a while, after the Ubuntu slider bar screen thing (genome?).

This I assume is because dmraid is not installed to the boot disk, and the grub menu list is probably all wrong.

Using the terminal in the live CD I have tried to run the following commands to follow the last few steps of the above guide and complete 8.04 installation but the first command 

(sudo mount -t ext3 /dev/mapper/<RAID_SET_NAME><PARTITION_NUM> /target) 

won't work, and I get a message saying that /target directory doesn't exist.

Can anyone help me from here?  I think I have most of a complete and successful install, but I am having trouble installing and configuring the boot loader, but I don't really know because I am **very new** at this.

Any body know where the Grub is in 8.04, or what to do with it???

---

### Post by dstew on 2008-05-19
Did you create the mount point directory? As it says in the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"):```
sudo mkdir /target
```Then the mount command should work.

I don't think the Hardy Live CD will install to a FakeRaid without installing dmraid first. Did you do that?

---

### Post by Marco7 on 2008-05-19
No, but I have thought about it, was worried I might put it in the wrong place. I'm pretty much poking around in the dark here.

Yes I installed dmraid to the live CD but haven't installed it to the boot directory chrooted, I think, cant get that far.

I would simply make this /target directory like in the fakeraidhowto but in that guide he then installs the base system, and it's pretty involved and I think most of that may have been done by running the installer already, so I'm wondering if I can't skip all that, and just install the boot loader.

So, you think if I do a

sudo mkdir /target

#and then

sudo mount -t ext3 /dev/mapper/<RAID_SET_NAME><PARTITION_NUM> /target
sudo mount --bind /dev /target/dev
sudo mount -t proc proc /target/proc    # was already done
sudo mount -t sysfs sysfs /target/sys

# copy some necessary files from the live CD over to the new installation of Ubuntu
sudo cp /etc/apt/sources.list /target/etc/apt
sudo cp /etc/resolv.conf /target/etc

# now point the terminal to start working with your new installation instead of the live CD
sudo chroot /target

# update the new installation and install dmraid and grub
apt-get update
apt-get install dmraid
apt-get install grub    # might already be installed

# copy some grub files to the proper directory
cp /usr/lib/grub/i386-pc/* /boot/grub    # replace "i386" with "x86_64" if you are using the AMD64 live CD

# now we're going to run grub with a command line option that I made up while trying to grub to install properly
grub    


I can save this installation???

---

### Post by dstew on 2008-05-19
> I think most of that may have been done by running the installer alreadyI don't know about that, I have been trying to get my hands on a computer with a FakeRaid controller to experiment with Hardy. The HowTo is based on older distributions, so I don't know how much if it applies to Hardy. I am not sure what happened to your disks during the Hardy install. If it works like the older distributions, the install CD does not respect the RAID and installs as if it were individual disks, including grub going into the MBR of one of the disks.

> I can save this installation???I am not sure. Go ahead with the steps you outlined. Can you tell if the RAID is still intact? Are you trying to create a dual-boot system with Windows on a RAID, or a Ubuntu-only system? If the latter, it is easy to start over again. If the former, you have to be careful lest you destroy your Windows system.

---

### Post by Marco7 on 2008-05-19
I don't know where the grub went but for the most part I think the install went well.  Gparted recognizes the raid set partition table, and I am careful not to corrupt it and only format specific partitions during the install.

I am a little concerned where the Grub went, because if I make a new one now, what will happen.

I am running windows on other partitions, and they have disappeared from the Grub boot menu.  I am a little concerned about how to get those back too.

---

### Post by dstew on 2008-05-19
Do you get a grub menu when you boot? If so, we can use grub itself to figure out if it is installed correctly. 

At the grub menu, press 'c' to get a command line. On the grub command line, type **root (hd** and then hit <tab> (instead of <enter>). The autocomplete feature should give you a result that tells you which disks are available, as grub sees them. If the output is consistent with your RAID setup, then grub is probably installed correctly, and just needs to be configured. If the output is consistent with individual disks, then grub is not installed correctly, and will need to be re-installed.

---

### Post by Marco7 on 2008-05-20
Thanks dstew,

[sudo mkdir /target] was the key.

Other than that I was able to install Hardy Heron, Ubuntu 8.04 x64 to a fake raid set, that is also a dual boot environment with Windows XP x64, using the following guide,["My Ubuntu (7.10) Installation"]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation").  This guide is nice because it uses the Ubuntu installer to copy and install most of the system files for the installation, and also makes use of gparted to format the partitions, keeping a previous instalation of windows in another partition safe.  !Careful not to delete the partition table in gparted (select "do not use" for all of the drives in the first list of partitions)!  I still found it useful to use fdisk to create the partition table as outlined in the [FakeRAIDHowto]("https://help.ubuntu.com/community/FakeRaidHowto").

__________________________________________________________

sudo mkdir /target

#and then

sudo mount -t ext3 /dev/mapper/<RAID_SET_NAME><PARTITION_NUM> /target
sudo mount --bind /dev /target/dev
sudo mount -t proc proc /target/proc # was already done
sudo mount -t sysfs sysfs /target/sys

# copy some necessary files from the live CD over to the new installation of Ubuntu
sudo cp /etc/apt/sources.list /target/etc/apt
sudo cp /etc/resolv.conf /target/etc

# now point the terminal to start working with your new installation instead of the live CD
sudo chroot /target

# update the new installation and install dmraid and grub
apt-get update
apt-get install dmraid
apt-get install grub # might already be installed

#And then the rest of the guide...

#The Grub already was installed for me, after running the Hardy installer, but probably not dmraid, and the menu.lst was also probably wrong.

_________________________________________________________


I still don't get how /target can just be thrown in there and make it all work, but it works now. :-)

---

### Post by dstew on 2008-05-20
What you are doing is mounting the RAID partition onto the Live CD file system (which is a special kind of file system in RAM). The mount point is the directory in the Live CD file system to which the RAID partition is attached (mounted) so you can access it from the Live CD. Then, when you copy files to /target, you are really copying them onto the RAID root directory. The name "target" is not important, you could have named the mount point directory "raid_root" or anything else if you wanted too. You just have to use that mount point name in the copy commands.

And, when you **chroot** ("**ch**ange **root**"), your Live CD file system makes /target the new root directory for the commands, so now you are really operating from inside the RAID partition when you do the apt-get commands to install and update. It will then install programs to the RAID partition instead of into the RAM file system that the Live CD uses.

---

