---
title: "Installing Ubuntu 9.04 on existing RAID5"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by ilikelinuxx on 2010-01-19
Hi All!

I looking for some help to get Ubuntu back in action on my rig! Currently, I have three 1T HDDs in a RAID5 configuration. My computer is running Windows 7 x64, fully updated blah blah... If it helps, my hardware is as follows:

Intel Q9550
EVGA 780i Chipset
2x EVGA NVIDIA 9800GTX+
4GB DDR2 1066 RAM
3x 1T HDDs
and plenty of power

Windows uses 200GB for a boot drive and the rest of the 2T is data (reformatting the drives is out of the question). Ideally, I would like to shirk the 200GB down and share it with Ubuntu.

I have searched the forums, documentation, etc and found nothing helpful. I have a laptop thats pure Ubuntu 9.04x64 that I would love to image onto the RAID, but I'm almost positive I cannot do that now. I even installed the Ubuntu Customization Kit (which is awesome!) and created my own live CD with RAID drivers (the package is 'dmraid') on it, in hopes that it would recognize the drives and allow me to install. When I boot into the custom live CD it wants to use all the space and displays nothing useful...:(

Thanks in advance!

---

### Post by dstew on 2010-01-20
The 200GB you refer to, is that a partition on the RAID5?

To install Ubuntu onto a partition on a FakeRAID (which is what you have) you can look at the [FakeRAID HowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). The [Alternate Install CD]("http://releases.ubuntu.com/9.04/") is what you want to use. It may or may not work.

A simpler option would be to install Ubuntu to an un-RAIDed partition. It should still be able to mount and use partitions on the RAID5 using dmraid. It is *installing* to the RAID that is tricky. Also, the grub booters, both grub2 and grub "legacy", cannot recognize RAIDs properly, so booting is a bit of an issue. One way to get around it is to use a small 100 Mb /boot partition that is not RAIDed to store the kernel images and the grub menu. Once the kernel boots, you can use dmraid to mount the RAID.

---

### Post by ilikelinuxx on 2010-02-02
Thanks for the tips dstew! To clarify, the 200 GB partition is indeed on the RAID5. I booted to the alternate CD and was a little confused when I encountered the following step in the [FakeRAIDHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). 

In the tutorial, "If the following doesn't appear this method will likely fail to load the Linux fakeRAID support and this method is not for you!

'One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?' Select yes."

I selected yes and much to my surprise, the install seemed to skip down to the menu with "Choose Finish Partitioning to write changes to disk." without the intermediate steps to specify the partitions, space, etc. I have no idea why it did this. I selected to "undo changes and quit" after and quit. I repeated this three times with the same result.

Please help! I miss my Linux =)

---

### Post by ilikelinuxx on 2010-02-11
My apologizes, this is not a 'fakeRAID' my hard drives are RAIDed through the BIOS, before the operating system boots. It sounds unreal that there is no way to install Linux, even another distro, to a RAID system. I just cannot believe it.

Please advise.

---

### Post by darkod on 2010-02-11
> **ilikelinuxx said:**
> My apologizes, this is not a 'fakeRAID' my hard drives are RAIDed through the BIOS, before the operating system boots. It sounds unreal that there is no way to install Linux, even another distro, to a RAID system. I just cannot believe it.

Please advise.

That is fakeraid. It is called that because even though it may seem it's proper hardware raid, it's not. It's a type of software raid too, so someone came up with fakeraid I guess.

I just tested software raid in VirtualBox this morning, but that is different to fakeraid. You can only use it if running only ubuntu, or when you don't want windows on the raid too. In that case the raid array is actually created by the OS hence it's called software raid. Worked great, and it was my first try to set up a raid (that's why I was using VirtualBox).

If you think it didn't detect your raid partitions properly I don't know what to say.

PS. You didn't get a menu to select manual partitioning?

---

