---
title: "Installation from USB Stick"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by juice99 on 2007-04-09
when i try to install latest (beta 7.04 ) ubuntu from my USB stick ( following this guide - [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ) , somehow i'm not able to mount USB as CDROM.
linking and doing /dev/cdroms/cdrom0 and such, doesnt help, because somehow mount doesnt want to mount it at all!
it says no such device...
i tried many stuff, usually mount -t vfat /dev/sda1 /cdrom and nothing helps. i'm sure that sda1 is my usb and it DO exists, i checked dmesg, syslog and such and when i take off my USB system recognize it, and when i put it in, it also recognizes it correctly. sda and sda1 is being made,  and everything seems fine, but why mount -t vfat /dev/sda1 /mount_point says no such device? i tried -t auto or -t fat , but nothing...
it's busyboxy mount of course, so maybe it's it fault ?

I have Gigabyte 965-S3 motherboard, but this USB was working when i installed dapper from USB. i didnt even have to mount anything, it was automatically recognized as source of installation

---

### Post by juice99 on 2007-04-09
nobody no ideas?

---

### Post by juice99 on 2007-04-09
*bump*

---

### Post by juice99 on 2007-04-10
*bump2* sorry for spam, but nobody seems to even try to help me...

---

### Post by mountaindude1 on 2007-09-05
Did you ever find a solution to this? I am experiencing the same issue.

Have tried booting on several different PCs as well as on one decTop (small AMD based server). No luck.
Tried both Xubuntu 6.06.1 Alternate and Xubuntu 7.04 Alternate - same result.

Anyone?

/MD

---

### Post by scapalexis888 on 2007-09-17
Yea...I am having the same trouble too. I followed the guide in the first post and when it came to the stage where I have to mount the USB flash drive as a CDROM, i keep getting that the drive does not exist. I will be monitoring this thread when someone has a solution.

---

### Post by Stenico on 2007-12-03
**Bump**

I checked what device name my usb drive was mapped to:

(1) cat /proc/partitions
(2) ls -l /dev/disk/by-id/usb*

But can't mount it. Arrggh. I've read somewhere that the full install iso just works with none of this problems. Bit annoying as I wanted a minimal install, but I guess I can strip it down afterwards. Off to try it now...

---

### Post by scapalexis888 on 2007-12-04
I have successfully installed both gutsy and feisty on a laptop without cdrom drive using a flash drive and here is the summary:

1. Make flash drive bootable with syslinux
2. Download the vmlinuz and intrid.gz from the ubuntu archives (not the cd ones - this is why people can't mount the flash drive as CD)
3. get the isolinux.cfg from the cd and rename it syslinux.cfg
4. get a copy of an iso you want to install. dont extract or rename the iso.
5. drag those files into a flash drive
6. boot from it and the install shall go normally without needing to mount anything

any details can be found from the internet or this forum. search install edgy from iso (its the same guide done with edgy)

---

### Post by tormod on 2007-12-04
I just updated [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) with links to a isotostick.sh installation script. It works fine with the 7.10 Desktop CD. Hope it can help some people.

---

### Post by MergeMedia on 2007-12-04
worked for me!  thanks for the write up .. very useful now that it works :D

---

### Post by trimeta on 2008-01-08
I have the same problem as original poster with the Gutsy server install ISO; I suppose I could use the desktop disk, but I really wanted some of the server-specific features (LVM, automagic Apache and Samba, etc.). No luck getting non-desktop disks to work?

---

### Post by Chark on 2008-01-12
Yeah I just tried with the Gutsy i386 Server disk (used the isotostick.sh)

Failed,  get a device not found if I try to mount the flash drive... =\

---

### Post by Qwertinsky on 2008-01-18
Same problem here "No such device"](*,)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This method works fine with Dapper (6.06) can do with my eyes closed

Why not with anything else?

---

### Post by tormod on 2008-01-18
At what point do you get "No such device" ? When mounting the flash drive manually? Please use for instance "fdisk -l" to check what the correct device name should be.

---

### Post by Qwertinsky on 2008-01-18
> **tormod said:**
> At what point do you get "No such device" ? When mounting the flash drive manually? Please use for instance "fdisk -l" to check what the correct device name should be.

Is there another command that will do the same thing?

 fdisk : not found 

I searched through the directory's and could not find it myself.

All I have to work with here is the minimal shell (busybox?) that is available when you alt-f2 out of the installation to mount the flash.

But I have tried sda0 through sda10 jst for the hell of it and still get the error "No such device"

---

### Post by smartboyathome on 2008-01-18
> **Qwertinsky said:**
> Is there another command that will do the same thing?

 fdisk : not found 

I searched through the directory's and could not find it myself.

All I have to work with here is the minimal shell (busybox?) that is available when you alt-f2 out of the installation to mount the flash.

But I have tried sda0 through sda10 jst for the hell of it and still get the error "No such device"

It should be included on every version of Ubuntu. I think you may have a corrupt CD image. What size is the ISO you downloaded?

---

### Post by Qwertinsky on 2008-01-19
> **smartboyathome said:**
> It should be included on every version of Ubuntu. I think you may have a corrupt CD image. What size is the ISO you downloaded?

But I can not get to the files on the flash drive (where the iso files are) because I can not mount the flash drive.](*,)

---

### Post by tormod on 2008-01-19
Maybe the server CD kernel doesn't boot with USB support. I don't have a server CD here myself to check, but if you could take the initrd.gz from the CD (or the iso) and run this on it:
** gzip -dc initrd.gz  | cpio -it > initrd-files.txt**
and attach the new file initrd-files.txt here, I can take a look.

Inside the busybox shell you can try:
 **grep usb /proc/modules**
and
** ls /sys/bus/usb**

---

### Post by dan_hurst on 2008-01-22
Xubuntu 7.10 desktop CD worked ok for me but couldn't install to HDD as partitioning manager had probs.

Tried the alternative CD to see if it could do the partitioning any better and couldn't mount the USB as CDROM (same errors as above, no such device).

Tried Scapalexis888's suggestions but didn't work either.

Going back to the desktop CD to see if I have any more luck with that.

---

### Post by skeigor on 2008-01-23
So!?

Any news on this issue? It's kinda irritating that you can't install via usbsticks anymore.

Alternate and server edition seems broken.

I am installing on industrial pcs and appliance computers and usb sticks is like the only way. :-s

---

### Post by vertigo23 on 2008-01-24
*bump*

I'm getting exactly the same problem.  Got a bunch of headless servers with no CD-ROM that I'd really like to get installed.

---

### Post by tormod on 2008-01-25
If nobody answers my questions, I can't help much for the moment. This seems to have been reported in [https://bugs.edge.launchpad.net/ubuntu/+source/debian-installer/+bug/124049](https://bugs.edge.launchpad.net/ubuntu/+source/debian-installer/+bug/124049) - please verify and confirm. Other similar bugs are [https://bugs.edge.launchpad.net/ubuntu/+source/debian-installer/+bug/181908](https://bugs.edge.launchpad.net/ubuntu/+source/debian-installer/+bug/181908) and [https://bugs.edge.launchpad.net/ubuntu/+source/debian-installer/+bug/104113](https://bugs.edge.launchpad.net/ubuntu/+source/debian-installer/+bug/104113)

---

### Post by asmallerbrain on 2008-02-08
Bump... I'm having the same issue.  Perhaps we should be taking this up with the maker of  isotostick.sh ??

---

### Post by tormod on 2008-02-09
Does the workaround in bug #124049 help?

Just bumping on the forum won't help, if nobody wants to try to help find the cause of the problem :)

---

### Post by marcin on 2008-02-09
> **tormod said:**
> Maybe the server CD kernel doesn't boot with USB support. I don't have a server CD here myself to check, but if you could take the initrd.gz from the CD (or the iso) and run this on it:
** gzip -dc initrd.gz  | cpio -it > initrd-files.txt**
and attach the new file initrd-files.txt here, I can take a look.


the list from xubuntu-7.10-alternate-i386.iso is attached

---

### Post by marcin on 2008-02-09
only isofs filesystem module is in this initrd, no vfat/ext2/ext3.
I replaced vmlinuz/initrd.gz with ones from standard cd, and I could mount my disk.

---

### Post by tormod on 2008-02-10
Marcin, thanks for the information. That's very interesting. Can you please confirm that only the fs modules are missing? You can do this by adding vfat/vfat.ko to the original initrd.gz (see [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd) for how to do this).

The /lib/modules/2.6.22-14-generic/kernel/fs/vfat/vfat.ko from a normal Gutsy installation should do the job.

---

### Post by ternur on 2008-02-14
This is very intersting issue for me right now and it's a pity that the thread has been inactive for a few days. However, at least the Gutsy Server ISO lacks for vfat so I extracted the existing initrd from the ISO and recreated it after copying vfat.ko to its fs/vfat-subdirectory.

When trying to boot the computer from the stick, the system complains about not sufficient memory. Therefore, if somebody has altered the initrd succesfully with vfat support, please post here where to get it.

> **tormod said:**
> Marcin, thanks for the information. That's very interesting. Can you please confirm that only the fs modules are missing? You can do this by adding vfat/vfat.ko to the original initrd.gz (see [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd) for how to do this).

The /lib/modules/2.6.22-14-generic/kernel/fs/vfat/vfat.ko from a normal Gutsy installation should do the job.

---

### Post by caeserjk02 on 2008-02-19
When you get to the point in the install that the installation process checks for the cd you will switch to another session by alt-2

Once you have created /cdrom /dev/cdroms you will want to link /dev/cdroms/cdrom0 to your usb drive. 

ln -s /dev/sda1 /dev/cdroms/cdrom0

Then

mount -t vfat /dev/cdroms/cdrom0 /cdrom     -- This line is optional. If you tell the installer to check for the cd again, it will essentially do the same thing.

switch back to the installer using alt-1 and check media/continue.

---

### Post by ternur on 2008-02-21
The problem is that the iso cd's initrd file does not include vfat filesystem so you can't mount the cdrom as previously described. I was not able to rebuild the working initrd by copying vfat.ko from an existing system, so I am still waiting someone to post a solution :)

---

### Post by emesee on 2008-02-21
it seems like the process could theoretically be made to be more user friendly.

:-({|=

---

### Post by Bungo Pony on 2008-02-21
> **ternur said:**
> The problem is that the iso cd's initrd file does not include vfat filesystem so you can't mount the cdrom as previously described. I was not able to rebuild the working initrd by copying vfat.ko from an existing system, so I am still waiting someone to post a solution :)

Sounds like you're having the same problem as me. Apparently, the people at FitPC got it to work (that's how they install Ubuntu on their PCs), so I'll be heading over there to ask some questions.

---

### Post by marcin on 2008-02-21
As you know (because you read previous posts), this problem doesn't exists in initrd from regular ubuntu disk, so you can simply copy it from there. (this installer prefers to have .iso file on pendrive, not content of the disk)

@tormod: sorry, I didn't have time and motivation to investigate further missing modules

---

### Post by tke1384 on 2008-02-24
Could you go into a bit more detail on how to use the ISO file on a pen drive to boot I've been having loads of trouble.  The desktop install doesn't seem to like partitioning my SATA drive and I can't get the alternative iso to boot from my external without trouble mounting the cdrom.  I even created a second partition holding the iso hoping to mount it direct but same issue.  I tried copying the initrd file from desktop install but that wouldn't boot at all.  I'm really starting to wonder about Ubuntu.  I've used loads of other distro's and never had this much trouble

---

### Post by marcin on 2008-02-24
> **tke1384 said:**
> Could you go into a bit more detail on how to use the ISO file on a pen drive to boot I've been having loads of trouble.  The desktop install doesn't seem to like partitioning my SATA drive and I can't get the alternative iso to boot from my external without trouble mounting the cdrom.  I even created a second partition holding the iso hoping to mount it direct but same issue.  I tried copying the initrd file from desktop install but that wouldn't boot at all.  I'm really starting to wonder about Ubuntu.  I've used loads of other distro's and never had this much trouble

I used vmlinuz and initrd from desktop cd. So I had 4 files on pendrive: vmlinuz, initrd.gz, syslinux.cfg and xubuntu-7.10-alternate-i386.iso. Only one partition.

---

### Post by tke1384 on 2008-02-24
I was ablt to boot from a USB drive but still having problems formating my SATA HD but I thank you for all your help

---

### Post by amx109 on 2008-02-25
i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

[LIST]
[*]use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
[*]copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
[*]rename isolinux.cfg to syslinux.cfg
[*]goto [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") and download the initrd.gz and vmlinuz files.
[*]create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
[*]copy the ubuntu iso you wish to install onto the root of the usb stick
[/LIST]

whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps

---

### Post by tech404 on 2008-03-10
What install disk do you get isolinux from? I am using the minimum install disk and found no such directory. I will try with the one from the LiveCD. If this isn't the case please let me know.

---

### Post by glenboarder99 on 2008-03-10
NOTE that when you use a USB drive it is the same as using a live CD

---

### Post by wolfchri on 2008-04-13
> 

[LIST]

[*]goto [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") and download the initrd.gz and vmlinuz files.
[*]copy the ubuntu iso you wish to install onto the root of the usb stick
[/LIST]

whack it in, and install away. it will automatically find and mount the iso for install.



for the sake of completeness: If you want to install a amd64 iso, then you need to download the respective 64 bit installer files, otherwise no .iso will be found. The i386 installer is only looking for i386 .isos, although it would be possible to install the 64 bit system via i386 installer (in theory :-)  )

---

### Post by skeigor on 2008-04-21
> **amx109 said:**
> i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

[LIST]
[*]use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
[*]copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
[*]rename isolinux.cfg to syslinux.cfg
[*]goto [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") and download the initrd.gz and vmlinuz files.
[*]create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
[*]copy the ubuntu iso you wish to install onto the root of the usb stick
[/LIST]

whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps


It did! By far the best result so far. However it complains that the kernel is not matching. No idea what it means since it seems to work anyways. Thanks alot.

---

### Post by Jenxie on 2008-05-06
> **amx109 said:**
> i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

[LIST]
[*]use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
[*]copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
[*]rename isolinux.cfg to syslinux.cfg
[*]goto [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") and download the initrd.gz and vmlinuz files.
[*]create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
[*]copy the ubuntu iso you wish to install onto the root of the usb stick
[/LIST]

whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps

Thank you very much =)

This solved my problem installing the server version of ubuntu *phew*

---

### Post by netimen on 2008-05-07
> **amx109 said:**
> i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

[LIST]
[*]use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
[*]copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
[*]rename isolinux.cfg to syslinux.cfg
[*]goto [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") and download the initrd.gz and vmlinuz files.
[*]create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
[*]copy the ubuntu iso you wish to install onto the root of the usb stick
[/LIST]

whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps

thanks! I managed to install kubuntu 8.04 hardy LTS alternative CD 32-bit with this! I think it should be added to the [official guide]("https://help.ubuntu.com/community/Installation/FromUSBStick"), because it really works!

---

### Post by mikkelrev on 2008-05-19
> **amx109 said:**
> i ran into the same problem people are having here when trying to install the hardy alpha 5, but managed to get round it. thought i;d share my results

the problem lay in the fact that the kernel on the 'alternate' iso doesn't include support vfat/ext filesystems. toyed with using the isotostick script but came up with my own solution instead

[LIST]
[*]use syslinux to make the usb stick bootable (you will need to set the bootable flag too. i think syslinux gives you pointers on how to if it isn't set, that or use something like fdisk)
[*]copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick
[*]rename isolinux.cfg to syslinux.cfg
[*]goto [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") and download the initrd.gz and vmlinuz files.
[*]create a folder on the usb stick called 'install' and copy initrd.gz and vmlinuz into it (or alternatively edit the syslinux.cfg to point it to the correct location of initrd.gz+vmlinuz)
[*]copy the ubuntu iso you wish to install onto the root of the usb stick
[/LIST]

whack it in, and install away. it will automatically find and mount the iso for install. it seems that the 'hd-media' install kernel contains all the necessary kernel modules for accessing diff hardware/filesystem types etc

hope this helps

Thanks buddy, you saved my day!

---

### Post by cosynmr on 2008-05-24
Thanks a lot for that post amx109! very useful!

---

### Post by CameO73 on 2008-06-26
Thanks amx109. That post finally worked for me. Should really be a part of the official [Install from USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick) page!

---

### Post by tormod on 2008-07-01
> **CameO73 said:**
> Thanks amx109. That post finally worked for me. Should really be a part of the official [Install from USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick) page!

The good thing is that the official page is a wiki page so you can fix it yourself without waiting for someone to do it for you ;) Anyway, I added a link to amx109's post.

---

### Post by Shai Hulud on 2008-07-06
I followed your instructions, but all i get is an blinking _ at the top left corner of the screen. Any ideas?

---

### Post by tormod on 2008-07-06
> **Shai Hulud said:**
> I followed your instructions, but all i get is an blinking _ at the top left corner of the screen. Any ideas?

What's the last thing you see before that blinking _ ?

---

### Post by Shai Hulud on 2008-07-09
It was nothing actually. I was just selecting my usb from the boot screen and the _ appeared.

Anyway i managed to do it with some obscure and rather arcane instructions from a site that i lost to be honest.

I will search trough my history, and if i find it i'll post it here for future reference.

Thanks for replying  :)

---

