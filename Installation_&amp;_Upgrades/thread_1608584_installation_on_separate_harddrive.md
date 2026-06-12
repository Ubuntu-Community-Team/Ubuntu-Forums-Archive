---
title: "installation on separate harddrive"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by me_loco on 2010-10-29
Hi all,
Thinking of installing 10.10 on a separate hard drive but i would like to have a separate boot file for ubuntu how to do that?

Thanks,

---

### Post by mikewhatever on 2010-10-29
The installation to any partition, located on an internal or external hdd is pretty much the same. The only important aspect to consider is where to install the boot loader. Since you want Ubuntu on a separate hdd, you probably also want to install the bootloader to the mbr of that hdd. You can choose where to install the bootloader at the partitioning stage (has to be manual), bottom of the screen.

---

### Post by me_loco on 2010-10-29
> **mikewhatever said:**
> The installation to any partition, located on an internal or external hdd is pretty much the same. The only important aspect to consider is where to install the boot loader. Since you want Ubuntu on a separate hdd, you probably also want to install the bootloader to the mbr of that hdd. You can choose where to install the bootloader at the partitioning stage (has to be manual), bottom of the screen.

cool, so if i installed bootloader at the HDD where ubuntu would go, that wouldn't make changes to windows MBR? and i can switch OS with F8, yes?

:guitar:

---

### Post by kansasnoob on 2010-10-29
The very first thing is to find out how Ubuntu recognizes your drives and partitions. The command "sudo fdisk -l" should display all devices. Note: that's a lower case L!

You'll notice that drive designations are similar to /dev/sda, /dev/sdb, etc. The "a" and "b" indicate the order Ubuntu recognizes the devices in.

Partition designations are like /dev/sda1, /dev/sda2, /dev/sdb1, etc. So sda1 = drive #1, partition #1 and so on. Clear as mud?

Another very useful tool is Gparted which is installed in the Live CD by default. In fact my preferred method of installing with multiple operating systems, multiple drives, etc. is to pre-create my partitions as described in this tutorial:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

However I'd never resize a Windows 7 or Vista OS with anything but it's own partitioning tools!

This is a fairly common partition layout if Ubuntu is using an entire disc:

[ATTACH]173890[/ATTACH]

I'm not going to go into great detail about that but basically you can see I created a primary root partition which is designated by "/", an extended partition which can house a large number of logical partitions, a separate "/home" logical partition which makes it much easier to reinstall in the future, and an appropriate sized logical SWAP partition. **If you need more help determining proper partition sizes and/or layout options please say so**.

Also ubiquity (aka: the live installer) got a complete rework in Maverick so many of the screenshots in that tutorial are now outdated, but there are similarities.

By default Ubuntu will commonly install grub to the mbr of /dev/sda and **the option to install grub elsewhere is now only available if you choose "Manual partitioning (advanced)"**. Don't let that scare you.

After choosing "Manual partitioning (advanced)" you'll see a screen similar to this:

[ATTACH]173899[/ATTACH]

If you've created your partitions in advance you can simply scroll & click on the proper device designation (eg: /dev/sda3) and you'll see a screen somewhat similar to this:

[http://members.iinet.net/%7Eherman546/p28/025_ssd-done.png](http://members.iinet.net/%7Eherman546/p28/025_ssd-done.png)

Sorry I have to use an older image but there's a limit to how many screenshots I can post in a thread. Regardless the choices are the same:

Size: If you just created the proper size make no change.
Use as: Select your preferred file system, EXT4 is the default for Maverick.
Format: Normally yes, **[COLOR="Red"]the exception is if you're reusing an existing "/home" in which case you don't want to reformat[/COLOR]**.
Mount point: Well, "/" indicates root, "/home" indicates home.

If you pre-created a SWAP there is no need to make any changes at all to it.

Regarding grub you'll notice at the bottom it says "Device for bootloader installation". If you click to expand that you'll see all devices as indicted in the thumbnail below.

**It will allow you to install to the wrong device!** Thus the importance of creating devices and selecting only the proper devices during installation. I'd recommend installing grub to the mbr of the drive Ubuntu is installed on, however if you plan on using something like Easy-BCD grub should be installed to the pbr of the partition containing /boot, most commonly the root (aka: "/") partition.

During Maverick development some of the shortcomings in the new ubiquity were discussed and I'm working on trying to get things better in Natty:

[http://ubuntuforums.org/showthread.php?t=1595807](http://ubuntuforums.org/showthread.php?t=1595807)

So, how badly have I confused you?

---

### Post by me_loco on 2010-10-29
> **kansasnoob said:**
> The very first thing is to find out how Ubuntu recognizes your drives and partitions. The command "sudo fdisk -l" should display all devices. Note: that's a lower case L!

You'll notice that drive designations are similar to /dev/sda, /dev/sdb, etc. The "a" and "b" indicate the order Ubuntu recognizes the devices in.

Partition designations are like /dev/sda1, /dev/sda2, /dev/sdb1, etc. So sda1 = drive #1, partition #1 and so on. Clear as mud?

Another very useful tool is Gparted which is installed in the Live CD by default. In fact my preferred method of installing with multiple operating systems, multiple drives, etc. is to pre-create my partitions as described in this tutorial:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

However I'd never resize a Windows 7 or Vista OS with anything but it's own partitioning tools!

This is a fairly common partition layout if Ubuntu is using an entire disc:

[ATTACH]173890[/ATTACH]

I'm not going to go into great detail about that but basically you can see I created a primary root partition which is designated by "/", an extended partition which can house a large number of logical partitions, a separate "/home" logical partition which makes it much easier to reinstall in the future, and an appropriate sized logical SWAP partition. **If you need more help determining proper partition sizes and/or layout options please say so**.

Also ubiquity (aka: the live installer) got a complete rework in Maverick so many of the screenshots in that tutorial are now outdated, but there are similarities.

By default Ubuntu will commonly install grub to the mbr of /dev/sda and **the option to install grub elsewhere is now only available if you choose "Manual partitioning (advanced)"**. Don't let that scare you.

After choosing "Manual partitioning (advanced)" you'll see a screen similar to this:

[ATTACH]173899[/ATTACH]

If you've created your partitions in advance you can simply scroll & click on the proper device designation (eg: /dev/sda3) and you'll see a screen somewhat similar to this:

[http://members.iinet.net/%7Eherman546/p28/025_ssd-done.png](http://members.iinet.net/%7Eherman546/p28/025_ssd-done.png)

Sorry I have to use an older image but there's a limit to how many screenshots I can post in a thread. Regardless the choices are the same:

Size: If you just created the proper size make no change.
Use as: Select your preferred file system, EXT4 is the default for Maverick.
Format: Normally yes, **[COLOR="Red"]the exception is if you're reusing an existing "/home" in which case you don't want to reformat[/COLOR]**.
Mount point: Well, "/" indicates root, "/home" indicates home.

If you pre-created a SWAP there is no need to make any changes at all to it.

Regarding grub you'll notice at the bottom it says "Device for bootloader installation". If you click to expand that you'll see all devices as indicted in the thumbnail below.

**It will allow you to install to the wrong device!** Thus the importance of creating devices and selecting only the proper devices during installation. I'd recommend installing grub to the mbr of the drive Ubuntu is installed on, however if you plan on using something like Easy-BCD grub should be installed to the pbr of the partition containing /boot, most commonly the root (aka: "/") partition.

During Maverick development some of the shortcomings in the new ubiquity were discussed and I'm working on trying to get things better in Natty:

[http://ubuntuforums.org/showthread.php?t=1595807](http://ubuntuforums.org/showthread.php?t=1595807)

So, how badly have I confused you?

Thank you for the excellent details, i have created four partitions (3) primaries, /boot (500MB), /(20GB), swap(7GB) and one logical /home (250GB). I can't boot to ubuntu maybe because i put the bootloader in /boot? where should i place the bootloader?

Now do i have to reinstall from all over again or i can run setup and change configuration?

Thanks again for your time.

---

### Post by mikewhatever on 2010-10-29
> **me_loco said:**
> Thank you for the excellent details, i have created four partitions (3) primaries, /boot (500MB), /(20GB), swap(7GB) and one logical /home (250GB). I can't boot to ubuntu maybe because i put the bootloader in /boot? where should i place the bootloader?

Now do i have to reinstall from all over again or i can run setup and change configuration?

Thanks again for your time.

Installing the boot loader in /boot is ok, but you also need something in the mbr or some alternative way to point to that bootloader. Given you've picked /boot, how did you plan to load it?

---

### Post by me_loco on 2010-10-29
> **mikewhatever said:**
> Installing the boot loader in /boot is ok, but you also need something in the mbr or some alternative way to point to that bootloader. Given you've picked /boot, how did you plan to load it?

i can edit MBR to include GRUB but really i thought the whole idea of installing on separate drive is to avoid messing up the MBR? please advise.

---

### Post by kansasnoob on 2010-10-29
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can use a Live CD to do that and there are alternative instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kansasnoob on 2010-10-29
> **me_loco said:**
> Thank you for the excellent details, i have created four partitions (3) primaries, /boot (500MB), /(20GB), swap(7GB) and one logical /home (250GB). I can't boot to ubuntu maybe because i put the bootloader in /boot? where should i place the bootloader?

Now do i have to reinstall from all over again or i can run setup and change configuration?

Thanks again for your time.

Just wondering also, where did you get the idea to create a separate "/boot"?

And IMHO I would start over because you may later decide you need to add a Windows to that drive and Windows does not play well with logical partitions.

You really did nothing I suggested.

An mbr is the drive designation, a pbr is a partition designation.

---

### Post by me_loco on 2010-10-29
> **kansasnoob said:**
> Just wondering also, where did you get the idea to create a separate "/boot"?

And IMHO I would start over because you may later decide you need to add a Windows to that drive and Windows does not play well with logical partitions.

You really did nothing I suggested.

An mbr is the drive designation, a pbr is a partition designation.

It was too late, i had alrady had ubuntu installed before i checked your post. I will do it from over, i followed online tutorial on creating the partitions. I will never use this drive for windows because i already have one for windows.

were the sizes ok? your suggestion pls!
as far as the grub, what did you mean mbr of the drive ubuntu? /home? /? or /dev/sda?

Thank you.

---

### Post by mikewhatever on 2010-10-30
MBR is designated as /dev/sdX, where X ranges from a to z. Every hdd has it, and in your case, you probably want something other then /dev/sda, for example /dev/sdb or /dev/sdc, depending on how the external hdd is designated.

---

