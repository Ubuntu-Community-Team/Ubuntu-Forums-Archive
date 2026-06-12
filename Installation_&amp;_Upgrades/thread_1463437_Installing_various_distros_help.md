---
title: "Installing various distros help"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by supershin on 2010-04-26
I want to keep windows 7 and install backtrack, openSuse, fedora and ubuntu 10.04(when it releases) on my laptop(Asus ul30vt, win7 64bit, 4GB ram, 500GB HD). 
I'm following various tutorials, bodhi.zazen guide, & links 
and I'm suffering from information overload now. 

Just to state what I'm thinking, so you can tell me what I'm missing and how to proceed. I'm going with /home in the each linux partition and having a single partition for shared data. 

1st: I need to understanding partitioning. I'm going to put them into a extended partition. So I make the partition and make 4 logical partitions. Then I install each distro in a partition, right? 
   Do I need to know how to use Gparted or can I install the distros in that order and just follow their installers instructions?

2nd: GRUB. I want to use grub2. I see some guides where grub can be in its own partition but is that a good idea. Can grub2 be in its own partition? Can grub2 be chainloaded? 

Most guides I see refer to grub, not grub2, so not sure of differences in the steps. 

I'll post the rest of my questions tmr. :confused:


bodhi.zazen guide:
[http://ubuntuforums.org/showthread.php?t=724817&page=1](http://ubuntuforums.org/showthread.php?t=724817&page=1)
other multi-boot thread:
[http://ubuntuforums.org/showthread.php?t=1446351](http://ubuntuforums.org/showthread.php?t=1446351)

---

### Post by QIII on 2010-04-26
As a suggestion...

You may try a lot of distros and realize that one or more just doesn't suit you.  Or you may want to try many more than you have listed.  I suspect you will find that you really only like one or two.

Before you commit to sorting out how you want to partition, it might be worth your while to take other distros for a spin by virtualizing them in VirtualBox or similar.

There are some penalties for virtualizing, such as the fact that the virtualization software will chose its own virtual hardware for things like video and the virtual drivers to go along with it.

You would also need the PEUL version of VirtualBox to get support for USB devices, etc.

But at least you would be able to try a host of different distros and see if you even like them (make your virtual disks fairly small to begin with.)  You may find that you think Ubuntu sucks, so you will have done a lot of work and planning for something you don't really want any more.

By first virtualizing, if you find that all you really want is Win 7 and OpenSUSE or Ubuntu or some other Linux distro, planning your partitioning will be much easier.

---

### Post by carl4926 on 2010-04-26
Personally, I would set out all my partitions first.
I would decide which distro is my main one and install that last. If you plan on using Ubuntu then can you use that as your main distro, it uses Grub 2, which is really easy and intuitive.

You sure need to know how to use the partitioner (I tend to to use Parted Magic)
You only need 1 swap partition
Each distro requires at least 1 partition to install to OR 2 partitions if you want a separate /home.

You ask if grub can have it's own partition. Not exactly. I think you are referring to a /boot partition. And honestly I never bother. I just put grub directly to the MBR.

---

### Post by QIII on 2010-04-27
Personally, I always install each OS to a separate physical disk and install Ubuntu last.  Makes planning partitions a snap.

But that's a bit limited by the number of SATA headers on the mobo...  ;)

---

### Post by limey_rick on 2010-04-27
I also like to have separate disk for separate OS. I have Ubuntu, Suse, Fedora, and XP on different disks and then on some of these I have different versions. 

Its important to decide which one you want to control booting, so for other LINUX distros, I don't install GRUB and always do windows first because it is fussy about which disk is goes on (you don't want to find this out after you've installed most of the others). 

If you do want to install several on one disk, as suggested, create the partitions first, install windows first and Ubuntu last.

---

### Post by supershin on 2010-04-27
> **QIII said:**
> As a suggestion...

You may try a lot of distros and realize that one or more just doesn't suit you.  Or you may want to try many more than you have listed.  I suspect you will find that you really only like one or two.

Before you commit to sorting out how you want to partition, it might be worth your while to take other distros for a spin by virtualizing them in VirtualBox or similar.

There are some penalties for virtualizing, such as the fact that the virtualization software will chose its own virtual hardware for things like video and the virtual drivers to go along with it.

You would also need the PEUL version of VirtualBox to get support for USB devices, etc.

But at least you would be able to try a host of different distros and see if you even like them (make your virtual disks fairly small to begin with.)  You may find that you think Ubuntu sucks, so you will have done a lot of work and planning for something you don't really want any more.

By first virtualizing, if you find that all you really want is Win 7 and OpenSUSE or Ubuntu or some other Linux distro, planning your partitioning will be much easier.


Instead of virtualizing it to test it out, it'd be much easier to just download the LiveCD versions and run it. But that's not what I want to do. 


Regarding grub and grub2, I read that grub2 if installed last(installing ubuntu 10.04 last)  will read all the other OSes and do something similar to chainloading them so that they will automagically appear on the menu.


```
> From Skynet2029

Interesting post. This method is far too complex methinks.
One could simply install Ubuntu 9.10 or 10.04 FIRST.
Install Fedora 12 and specifying to install the Fedora bootloader to the first sector of the
(Fedora) /boot partition.

Reboot. You will now be back at your standard Ubuntu grub screen, with NO option to boot
into Fedora install. This is fine and what we want.
Boot into Ubuntu.
Fire up a terminal and do:

Code:

$sudo grub-mkconfig /dev/sdX

where X is your primary drive.
This command will generate plenty of output on the terminal. No worries, as again..
this is what we want. Now do:
Code:

$sudo update-grub

You will notice grub finds your Fedora installation and adds it to your boot menu.
Sweet!
Very easy and fast.
I think this is actually proper way to do this, as it utilizes built-in Grub commands to force grub to
remap the partition records, and then regenerates a proper grub boot menu.

Hope this helps and no disrespect meant to OP, just thought this was a little easier.

Cheers!
__________________
The opinion of 10,000 men is of no value if none of them know anything about the subject. ~Marcus Aurelius
registered Linux User#: 416460 
```

[]("http://ubuntuforums.org/showthread.php?t=1370222")

So basically I just install backtrack, opensuse, fedora and ubuntu 10.04 and specify not to install grub with suse and fedora so when ubuntu installs with grub2 it automatically updates everything to give a boot menu with all distros?

---

### Post by QIII on 2010-04-27
Using the LiveCD will allow you to test, but it is slow and, unless you take some extra steps, what you have done will not persist between uses.

Yes, GRUB2 will detect other OSs and add them to the menu.

```
sudo update-grub2
```However, I have not had much luck with doing that to detect OpenSolaris, so I have had to make custom entries for it in the past.

While you could install GRUB on the other installations and get things to work, I find it easier to install it only in the "base" distro, which you appear to want to be Ubuntu.

---

### Post by supershin on 2010-04-27
It may not be out-of-box persistent but it is the easiest way to test a distro. 

Making a custom-entry seems much simpler than doing grub stuff at each install.

Also, I'd like to have a dedicated grub partition, using grub2, is it possible?
EDIT: Found a guide, How To Make a Dedicated GRUB 2 Partition.
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/]("http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/")

If I want grub2 is in its own partition then when ubuntu is installing should I point it to install grub 2 on that partition overwriting the grub 2 files I installed at the start when I made that partition? Or do I have an empty partition to install grub2 and install the distros and lastly have ubuntu install grub 2 there?

---

### Post by rnerwein on 2010-04-27
hi 
about solaris - id did a quick and dirty fake. i insert in my menu.lst ( i use the suse boot load because i can use vi to 
manipulate it).

title solaris 10
    rootnoverify (hd1,0)
    chainloader +1

this entry calls the solaris grub on the second disk in the first partition ( partition count in suse grub starts at 0 ).
 works fine.
ciao

---

### Post by QIII on 2010-04-27
Unfortunately, menu.lst goes away with GRUB2 used by Ubuntu Karmic and Lucid.

As for the grub partition, I'm afraid I haven't mucked around with something like that to be much help...

---

### Post by Penguin Guy on 2010-04-27
> **supershin said:**
> So basically I just install backtrack, opensuse, fedora and ubuntu 10.04 and specify not to install grub with suse and fedora so when ubuntu installs with grub2 it automatically updates everything to give a boot menu with all distros?
Exactly. But if you want a dedicated grub partition, you'll obviously need to install grub separately and select 'do not install grub' in each OS.

---

### Post by supershin on 2010-04-27
That exactly what I wanted to know penguin guy. I'm installing fedora now without a bootloader(since backtrack already installed grub, though not in a separate partition). So now I just need to make a partition for grub 2 and install ubuntu 10.04 with grub 2 in the partition I made for it. right?

---

### Post by supershin on 2010-04-30
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")

Would following this guide give me grub 2 on a dedicated partition?
I'm assuming they install grub2 with an OS first and are then moving into a separate partition. Is that correct?  A little more clearer context would be nice.

---

### Post by supershin on 2010-05-02
I installed fedora and edited the 40_custom to get it to show up in the menu then ran update-grub. However at boot menu I choose it and get error: invalid signature. The other OS's(backtrack,lucid,win7) boot fine. The feodra partition has boot enabled.

How do I get fedora working with my setup?

results of sudo fdisk -l

```

sda1  hidden fat32
sda2  ntfs (win7 c drive, boot checked)
sda3  w95 Ext'd (LBA)  [extended partition?]
sda5  ntfs (my d drive for win7)
sda6  linux  (un-used, gonna put solaris here)
sda7  linux swap/solaris 

(didn't complete solaris install so not sure why it here).

sda8   linux (boot checked, assuming fedora)
sda9   linux (lucid)
sda10  linux  (backtrack)

```

sda8 should be fedora cause i remember telling the install something bout booting from that partition. I was thinking to chainload it so that choosing fedora in the grub2 menu would cause the fedora grub to run and boot.

---

### Post by recluce on 2010-05-02
Having a dedicated partition for GRUB1 (Grub 0.97 to be exact, also called "Legacy Grub") is a very good gameplan if you intend to play around with a lot of distros and other operating systems.

This guide explains it all and more about GRUB1:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

Some notes:

If you use GRUB1 on a dedicated partition to boot Linux Kernels directly (I do that both for Jaunty and Lucid) you will have to manually update your menu.lst on every Kernel update.

However, you can install your distro's boot loader (GRUB, GRUB1, Lilo, NTLDR, whatever) to the same partition as the distro/OS itself (NO installation to the MBR) and just chainload into that secondary bootloader. The distro will keep track of its individual boot loader to make any updates to the kernel list, at the same time, it will not see or need to see any other OS on the system.

In the second case, you only need to edit your menu.lst for readability - if you replace, lets say Gentoo on sda9 with Sabayon, you would probably want to edit the title of the entry for sda9 to avoid confusion.

Also, you don't loose boot capabilities of your system if you erase/overwrite any individual OS partition.

If you decide to use GRUB1 in a dedicated partition, make sure that you take the GRUB files from Jaunty (NOT earlier!) if you want to be able to boot EXT4 partitions (other EXT4-supporting distros with GRUB1 should do as well). Note that the GRUB files on an installed Ubuntu Jaunty are not necessarily from Jaunty (GRUB files are not routinely replaced during distro upgrades), a Jaunty Live CD will be safe.

---

### Post by supershin on 2010-05-03
That's for grub1, very informative though. I'm using grub 2 and although os-prober picks up fedora it isn't shown on the menu and if i edit the 40custom file i get error: invalid signature. If you need more info just ask.

Help me boot my fedora please.

---

### Post by oldfred on 2010-05-03
I do not have Fedora but saved these comments, now older. supposedly grub 1.98 solved most of these issues:

See Kansasnoob comments 40 & 42 Install grub 1.98  & to fix major grub issues
here was a BIOS option setting in the boot loader device selection in the Fedora installer. Comment #44
[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

[http://ubuntuforums.org/showthread.php?t=1367305](http://ubuntuforums.org/showthread.php?t=1367305)
If the linux has no bootloader, the os-prober will look for the kernel file name that starts with vmlinu[zx] and the initrd file name that starts with initrd.
In my case, I have installed fedora without bootloader and the initrd file name starts with initramfs. I have made a simple change to the os-prober by make it looking for the file starts with initr instead of initrd.

---

### Post by supershin on 2010-05-05
[QUOTE=
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}
[/QUOTE]

Hey thanks oldFred, I came across this code in a post, ([http://ubuntuforums.org/showthread.php?t=1343779]("http://ubuntuforums.org/showthread.php?t=1343779")), you linked to but i didn't know you could copy and paste it when I saw the blkid command.

Anyway, I've reinstalled fedora yesterday and made sure not to install a bootloader, have boot unchecked. I ran sudo os-prober and sudo update-grub twice (heard it can miss things on first run ...weird) and rebooted. 

Fedora is now seen on the menu, it starts to load then I get 
"Warning unable to open an initial console
Hub 3-0:1.0 unable to enumerate usb device on port 1" and it hangs there.

---

### Post by oldfred on 2010-05-05
That may be initramfs did not load correctly or has a problem. Might check Fedora forums. What boot loader does Fedora use. 

I have always liked chainbooting but grub2 does not like to be in a partition. The advantage of chainbooting is that the system updates its own grub menu with new kernels and you only have to have a chain boot entry in the first system you boot.

---

### Post by supershin on 2010-05-06
Fedora uses grub 1. Why doesn't grub2 like to be in a partition? 

Originally I wanted to have grub2 in its own partition so then the other OS's could update their grub menu. That way I can add/remove distro easiyly. Currently I have ubuntu lucid grub2 in charge and i'm using it to boot win7, backtrack and fedora.

---

### Post by oldfred on 2010-05-07
If Fedora still uses grub legacy put it in the Fedora partition and chainboot to it from grub2. 

Grub2 says they have to use blocklists if in a partition. It works but if a file gets moved even by fsck then you would have to reinstall grub to boot again, so they do not think it is reliable. I used it for a while with Karmic beta and it worked.

menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1
}

You can install grub files to a grub partition and use that to boot also.
I am doing that on my USB 4GB flash drive key.

Herman also has instruction for a grub legacy partition:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

