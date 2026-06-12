---
title: "Dual boot Ubuntu and another distro - auto mounting?"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by bengateau on 2010-10-21
Hi all,

I would like to install two Linux distros on two separate partitions on my PC. One will be Ubuntu for everyday usage and the other will be another Linux distro (haven't yet decided which one) which will be used only occasionally for things such as banking etc. I would like that Ubuntu does NOT see the other distro, and my question is: if Ubuntu sees another partition when loading, does it mounts automatically? If it does, is there a way to stop it from doing it?

Thanks, Ben

---

### Post by sanemanmad on 2010-10-21
No, all you need to do is configure GRUB to load X over Y first.


Try following this link as a tutorial. 
[Configuring GRUB BootLoader]("http://www.techhandbook.com/linux/3090-How-configure-GRUB-Bootloader-Mint-LinuxUbuntu.html")

---

### Post by sanemanmad on 2010-10-21
Here is another link that may help...

[Configuring GRUB]("http://beginlinux.com/blog/2009/09/understanding-the-grub-bootloader-course/")

---

### Post by sikander3786 on 2010-10-21
Depends on which distro you are going to choose. If it has got an option, you can choose not to install the bootloader. In that case you'll just have the Ubutnu boot loader and can later on add the new distro to Grub menu simply by running

```
sudo update-grub
```

It will just see the bootloader of that distro. Infact, Ubutnu will see the new distro's partition but won't mount it automatically unless you configure it for auto-mount in fstab.

---

### Post by perspectoff on 2010-10-21
It is also possible to keep all distros and OS's completely independent of each other (including independent of Grub 2) using instructions here:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

or

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

As it stands, Grub 2 is installed in the Ubuntu partition (which is set to be referenced by the MasterBootRecord). If you ever lose or change that partition, or if Grub2 becomes quirky, your computer will not boot any OS until you fix/re-install it.

However, if you create an independent boot partition that exists merely to chainload other OS bootloaders, then your system can be independent of the Ubuntu OS (and Grub2). While I like Ubuntu, I have many clients that do not want to have their entire bootup process dependent on the Ubuntu distro (and Grub2) and don't want the MBR to point to Grub2.

The instructions above detail a way to do this.

---

### Post by kansasnoob on 2010-10-21
> **bengateau said:**
> Hi all,

I would like to install two Linux distros on two separate partitions on my PC. One will be Ubuntu for everyday usage and the other will be another Linux distro (haven't yet decided which one) which will be used only occasionally for things such as banking etc. I would like that Ubuntu does NOT see the other distro, and my question is: if Ubuntu sees another partition when loading, does it mounts automatically? If it does, is there a way to stop it from doing it?

Thanks, Ben

I'm not sure what you mean by, "if Ubuntu sees another partition when loading, does it mounts automatically?"

By definition of "mount", no, neither OS is "mounted" while running the other. It seems like most people assume you're talking about grub being able to boot one or the other, but that's a different thing altogether.

I multi-boot a lot for testing purposes:

[ATTACH]173054[/ATTACH]

And by default no OS "mounts" any part of another OS. The only way that would happen is if you shared "/home" which IMO is a bad idea anyway.

What is "mounted" at boot is largely determined by /etc/fstab. By default mine in Maverick looks like this:

```
lance@lance-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap is on /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0

```

However I do want all OS's to mount the same "home/Documents - Downloads - etc" so I actually symlink the additional partitions:

```
lance@lance-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap is on /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2

```

Have I totally confused you :confused:

---

### Post by kansasnoob on 2010-10-21
I thought I should add that, aside from the "mounting" thing, even certain Firefox add-ons (such as Firefox Sync) can result in corrupt "files" being shared between distros.

Personally I use Firefox w/Firefox Sync for all of my daily surfing. I use Opera for banking and such and no one's robbed me yet :)

---

### Post by bengateau on 2010-10-22
Hi all,

thank you very much for all your replies. Sorry if my post wasn't clear. This is what I want: when Ubuntu is loaded, that it doesn't have access to another distro (I'll probably go with Debian). Good to hear that by default it will not. But I'm curious now about having the separate /boot partition. I posted message about partitions on [JustLinux]("http://www.justlinux.com/forum/showthread.php?t=153323") forum and was advised against it (separate /boot partition). The instructions listed on [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation) are refering to Grub Legacy (I assume that's version 1) and the document it is linking to (Installing Multiple Linux Distributions on a Single Box) is almost 7 years old. Also, this quote is scaring me a bit (instructions on how to install second linux distro) "I recommend a Server edition, because some Desktop editions overwrite  the Master Boot Record automatically, which is not at all desirable at  this stage". I really want client installations, with all their ports closed. So my question is, are there instructions on how to do the same with Grub2? I understand Grub2 has changed significantly and I'm not sure if I can just follow the instructions for Grub to achieve the same.

Thanks, Ben.

---

