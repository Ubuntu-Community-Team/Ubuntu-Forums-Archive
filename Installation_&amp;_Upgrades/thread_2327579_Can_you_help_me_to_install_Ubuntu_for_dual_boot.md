---
title: "Can you help me to install Ubuntu for dual boot?"
date: 2016-06-12
forum: Installation &amp; Upgrades
---

### Post by metalhusky on 2016-06-12
Hi, 
so a little background, i am new to Ubuntu, i tried it back then with WUBI and it was easy to install, and ubuntu was an ok system, but at the end i still ended up using Win7.
It's a good system. But now Microsoft is very pushy about Win10, installs telemetry with forced updates on Win 7 and 8 and you can't run DX12 without Win10 and with Win10 you basically are a "glass citizen", since they track everything and all that ********... so i decided, not with me. Through Smartphone Linux becomes more common, Vilkan runs on basically everything, AMDs support is getting better and better, also on Linux based OS' i heard, so, after reading and watching many videos, it looks like Ubuntu MATE and Gnome are  the two best distros. But i still, don't want to lose the option of Win7, eventhough i plan running also a VM with Win7 in Ubuntu MATE with GPU passtrough for compatibility.

Now the actual questions:
I made a USB stick with MATE, booted from it, as i saw on a explanation video, from the UEFI mode and created a SWAP partition, then clicked to install on the rest of free space, but then the installer asked, if i want to instal in UEFI, because there is a OS detected installed not in UEFI, and if i proceed installing, the other OS will not be able to boot anymore, so i said no, turned off the PC, and to install just Ubuntu i disconnected every HDD, including the one with Win7, but  the one with free space i left connected, the same message came up, but i completely disconnected Win7, why did it show up then?

I can make a video if you need.

Please respond, i've had enought of Windows' shenanigans with Win10...

---

### Post by Mark Phelps on 2016-06-12
Couple of side comments on your remarks ...

1) Forcing Win10 Upgrades: MS has become (IMHO) reprehensible in forcing upgrades on folks.  Download and install this tool in Win7 and that will be prevented:  [https://www.grc.com/never10.htm](https://www.grc.com/never10.htm)

2) AMD support: This seems to be disappearing!  I use Mint a lot, and in their latest release notes for version 18 Beta, they mention that AMD is NO LONGEr supporting their fglrx drivers for the newer kernel versions in Ubuntu 16.04 (upon which Mint 18 is based).  So, it looks like AMD is dropping support for Linux!

---

### Post by oldfred on 2016-06-12
Is your hardware UEFI, but you installed Windows 7 in BIOS/MBR mode?
Windows 7 default install mode has always been BIOS, but you can copy to flash drive and move some boot files to allow it to boot in UEFI mode. How it boots is how it installs (like Ubuntu).

Best to have Ubuntu in same boot mode as Windows, but if on a separate drive and hardware is newer UEFI, I might partition with gpt and include both an ESP - efi system partition for UEFI boot and a bios_grub partition for BIOS boot. But if you already have lots of data on drive, either backup or do not convert. Change from MBR to gpt will erase data, unless you use gdisk to convert.
Ubuntu can boot in either UEFI or BIOS from gpt partitioned drive. Windows only boots in UEFI mode from gpt and only in BIOS mode from MBR.

Shows 14.04 but 16.04 essentially the same:]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) 

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by metalhusky on 2016-06-12
1 I deinstalled all updates that have to do with telemetry or Win10 upgrade and set it so that i can choose what and when to update.
2 They are making new Drivers AMDGPU-PRO

---

### Post by grahammechanical on 2016-06-12
Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

We are going to get confused about which hard drive is which. So, the drive that you want to install Ubuntu on, what is also on it? How large is it? Is it GPT partitioned or MBR/msdos partitioned?

Which Ubuntu install option are you choosing? Use entire disk? Something else? The use entire disk option will erase everything on the disk but will create all the needed partitions. With a GPT partitioned disk Ubuntu will need a efi_boot partition if Ubuntu is installed in EFI mode. Or, a bios_boot partition if Ubuntu is installed in BIOS/Legacy/CSM mode. As well as a partition for Ubuntu ( / ) and a swap partition. That would be a minimum. And if we use the Something Else option we need to create those partitions in advance and then direct the installer to use them.

If you are using the install alongside option then there would be no need to create a swap partition as the installer would create the necessary partitions out of the unallocated space.

It seems that you are running the installer in EFI mode when may be you should be running the installer in BIOS mode.

Regards.

---

### Post by metalhusky on 2016-06-12
[[COLOR=#C61919]oldfred[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")
Well, holy moly, thats a lot of info.
So here we go, let's start very slowly, when i boot my PC the UEFI mode is available with F2, right, and when i installed Win7 i just put in my DVD and i don't know how it started the installation, in UEFI as well, would be my guess, right? So if i want to install Ubuntu i have to install it in UEFI as well, i went to UEFI and chose the USB stick that said UEFI on it, but before installing it said there is an another system that boots in a different mode than UEFI. So does it mean i can try to boot the USB stick in not UEFI but form UEFI and it will install?

---

### Post by metalhusky on 2016-06-12
[[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")[COLOR=#000000] [/COLOR]
Here is the Video that i watched.
[https://www.youtube.com/watch?v=y_44k6er-5A](https://www.youtube.com/watch?v=y_44k6er-5A)
I did everything as he explained.

I have cleared a didicated HDD for Ubuntu MATE.

So ok if i need to install in Legacy, how do i do that, he started installing from USB in UEFI mode, but if i choose the other option, will it work?

---

### Post by metalhusky on 2016-06-12
Here is what i get [https://www.youtube.com/watch?v=GzwWodz8qyE](https://www.youtube.com/watch?v=GzwWodz8qyE)

---

### Post by oldfred on 2016-06-12
If you installed Windows 7 with DVD, it was a BIOS boot and it formats drive as MBR.
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
You normally have to copy to flash drive and move files around.

You have to install with Something Else.
And if you want gpt, separate /home or anything else that is not typical, you should partition in advance.
But still have to use Something Else to choose partitions.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by lliseil on 2016-06-12
> **oldfred said:**
> Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. 

One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
Yeah swap is recommended unless one knows exactly what he's doing.
But oldfred one does not need swap size = RAM for suspend/hibernate. That's old gossip as [swap size = 2/5 RAM is practically enough]("https://wiki.archlinux.org/index.php/Suspend#About_swap_partition.2Ffile_size"). 
Works well on my desktop (1.9 GB swap file for 4 GB RAM), laptop (0.77 GB swap / 2 GB RAM) and NAS; suspending/hibernating the first two everyday.

---

### Post by oldfred on 2016-06-12
You need enough space for all of RAM in GiB. But most Ubuntu systems do not use all 4GB. So if you do not have 100's of tabs open in Firefox or just about every application, you probably can have a smaller swap. 
I just do not hibernate as it boots fast, especially now with my SSD.

---

### Post by lliseil on 2016-06-13
Not being in the heart of OP's question here but 

> You need enough space for all of RAM in GiB. 

This is an approximation. 
According to [kernel documentation]("https://www.kernel.org/doc/Documentation/power/interface.txt"):
> /sys/power/image_size controls the size of the image created by the suspend-to-disk mechanism. It can be written a string representing a non-negative integer that will be used as an upper limit of the image size, in bytes. The suspend-to-disk mechanism will do its best to ensure the image size will not exceed that number. However, if this turns out to be impossible, it will try to suspend anyway using the smallest image possible. In particular, if "0" is written to this file, the suspend image will be as small as possible. Reading from this file will display the current image size limit, which is set to 2/5 of available RAM by default.

Actually we may either decrease the value of /sys/power/image_size to make the suspend image as small as possible (for small swap partitions), or increase it to possibly speed up the hibernation process. In a word, swap size != RAM.

---

### Post by oldfred on 2016-06-13
@lliseil
You probably should update this with your good information.
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lliseil on 2016-06-14
Gasp. Would like to (see the history and talk behind this community page). Coming from the kernel documentation on which Arch wiki article bases its information and a few working setups with swap = 2/5 RAM, the SwapFaq seems to be from a fully different OS/culture. Do you believe there's *no reference* at all? Not sure I'll fit here.

---

### Post by oldfred on 2016-06-14
I just remember when the swap instructions were 2X times RAM back when RAM was less than 1GB. And for many years afterwards and even today still see users say to use 2X RAM. Some with 8GB use 16GB of swap and even saw one or two with 32GB of swap.

---

