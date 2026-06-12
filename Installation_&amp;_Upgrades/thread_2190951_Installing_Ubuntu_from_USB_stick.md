---
title: "Installing Ubuntu from USB stick"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by x3r0ssx on 2013-11-30
Hi all,

I have Ubuntu on USB stick and in the live area at the moment, I had problems installing the GRUB to a location, it just won't acceptit anywhere.

I have paritioned the hard drive perfectly as you can see in the below pictures:

[[IMG]http://i1327.photobucket.com/albums/u662/c0ntempt/snapshot1_zps698687c8.png[/IMG]]("http://s1327.photobucket.com/user/c0ntempt/media/snapshot1_zps698687c8.png.html")

[[IMG]http://i1327.photobucket.com/albums/u662/c0ntempt/Screenshotfrom2013-11-30105336_zpsf87c8936.png[/IMG]]("http://s1327.photobucket.com/user/c0ntempt/media/Screenshotfrom2013-11-30105336_zpsf87c8936.png.html")

Does anyone have any idea how to manually install GRUB to / on the hard drive? I am stumped, it just will not do it at all! The installation goes well up to this point.

I will post another screen shot of what it says.

Thanks.

---

### Post by x3r0ssx on 2013-11-30
Hi all,

Here is the problem:

[[IMG]http://i1327.photobucket.com/albums/u662/c0ntempt/Screenshotfrom2013-11-30112728_zps9a049a51.png[/IMG]](http://s1327.photobucket.com/user/c0ntempt/media/Screenshotfrom2013-11-30112728_zps9a049a51.png.html)

---

### Post by heir4c on 2013-11-30
Why you use a boot partition? That is not needed.
You have only to create a / partition and a swap partition (and like you wish a /home partition)
For Grub: You have to choose /dev/sdX (without a number) to install Grub. X = the letter from the HD where you install Ubuntu. Is it sda than you use /dev/sda.

I see on the screenshot that the partitions have a note like: /dev/mapper/.....
What is that? I think you choose for the LVM option or something, or RAID or... (I don't have any knowledge about that, because I don't use them, but that is not what you normal get with the gParted (PartitionManager) with a normal install.

Or is this on a externe HD?

Your / partition is also very big. That is not needed. With 20 - 30 GB you have enough, certainly with a separated /home partition. You can make /home partition as big as you want.

---

### Post by oldfred on 2013-11-30
I do not know RAID nor LVM. Both use the mapper device.

I might try Boot-Repair as it works with RAID or LVM, but you have to tell it which you have as it sees the /mapper but does not know which it is.

Please use the paperclip icon in the Go Advanced edit and attach screen shots. Not everyone has high speed Internet and many screen shots may lock up their system for a while trying to download everything at once.

You always install grub to the MBR of a BIOS/MBR configurated system or sda not a partition like sda1. The same with LVM or RAID. You install to the root or a label without the partition numbers.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

