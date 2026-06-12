---
title: "install on RAID array will not boot. (x64)"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by Linux_noob616 on 2010-09-15
I am using the 10.04.1 x64 Kubuntu live CD to install Kubuntu on my FakeRAID 0 array, I tell it not to install grub as i know it is still currently broken.

the install goes flawlessly. However on first boot using my live grub CD unless i tell my computer to point to the CD it will hang (which it is told to boot from CD first so i'm not sure why it does.)
When i tell it to boot to Linux, it will not boot saying the kernel is missing files (to much to sadly list, all i do not understand) then offers me a terminal to input "help" into for a list of Linux commands.

Windows 7  pro x64 works just fine

CD was downloaded VIA P2P if it matters

---

### Post by ronparent on 2010-09-15
The live grub cd is probably not the same version of grub 2 distributed with 10.04.1. Your best bet is to reinstall grub 2 using the live cd and using method 1 in the following: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

This will reinstall grub and write the correct boot loader to the MBR of your boot drive.

---

### Post by rtrask on 2010-09-15
I suspect that when it puts you into the terminal, you are in initramfs. Try typing "dmraid -ay" followed by exit. if it then boots, then the problem is that the raid array is not starting properly. You can probably fix that  by following the steps toward the end of this blog post.

[http://http://geertjohan.riemer.nl/2010/05/06/installing-kubuntu-with-dmraid/]("http://http//geertjohan.riemer.nl/2010/05/06/installing-kubuntu-with-dmraid/")

---

### Post by phillipdhall on 2010-09-15
I'm a Linux newb, so I can't say what the results of the above fixes will be. I have however found a workaround. Using the UBCD (Ultimate Boot CD - full of free tools) I can run Super GRUB2, which will boot my installation.

---

### Post by ronparent on 2010-09-15
Keep your eye on the target. If you objective is to turn on your computer and get a grub menu that will load any OS on it, then you have to reinstall grub 2.

If you download and run the boot info script and post the results, I could examine it and tell you how to fix it. Go here for the script: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

---

### Post by Linux_noob616 on 2010-09-16
> **ronparent said:**
> The live grub cd is probably not the same version of grub 2 distributed with 10.04.1. Your best bet is to reinstall grub 2 using the live cd and using method 1 in the following: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

This will reinstall grub and write the correct boot loader to the MBR of your boot drive.

Got it to install and boot finally. still no grub, So i will be applying your method above when i reboot.

Am i still pointing to /dev/sda even though i have a RAID?

EDIT:
I get the following when i try to use the "fdisk -l" command
```
ubuntu@ubuntu:~$ sudo fdisk -l

Unable to seek on /dev/sda

```

I also get this if i try to activate my RAID with dmraid
```
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_cbfdcbae" already active
RAID set "nvidia_cbfdcbae1" already active
RAID set "nvidia_cbfdcbae2" already active
RAID set "nvidia_cbfdcbae5" already active
RAID set "nvidia_cbfdcbae6" already active

```

I also can not mount any of the above partitions

mounting "sda" i get this
```
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: unknown filesystem type 'nvidia_raid_member

```

EDIT2: OKAY i got my kubuntu partition to mount using
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_cbfdcbae6 /mnt
```

Is this where i install the RAID? if i try just "/dev/mapper/nvidia_cbfdcbae" it says it is busy

I also am unable to access my kubuntu partition using Dolphin even though it is mounted

EDIT3: tried installing grub to "nvidia_cbfdcdae" and got this
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_cbfdcdae
You have a memory leak (not released memory pool):
 [0x13e81e0]
You have a memory leak (not released memory pool):
 [0x19311e0]
/usr/sbin/grub-probe: error: cannot stat `/dev/mapper/nvidia_cbfdcdae'.
You have a memory leak (not released memory pool):
 [0x117e740]
You have a memory leak (not released memory pool):
 [0x11051e0]
Invalid device `/dev/mapper/nvidia_cbfdcdae'.
Try `/usr/sbin/grub-setup --help' for more information.
```

EDIT4: well i got it to work (hopefully) it is still reporting memory leaks, But it said it installed no errors
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_cbfdcbae
You have a memory leak (not released memory pool):
 [0x1afc1e0]
You have a memory leak (not released memory pool):
 [0xb2e1e0]
You have a memory leak (not released memory pool):
 [0xe2c740]
You have a memory leak (not released memory pool):
 [0x1615740]
You have a memory leak (not released memory pool):
 [0x1798760]
Installation finished. No error reported.
```

EDIT5:
Okay, grub is now on my PC in dev/mapper/nvidia_cbfdcbae

But i can't do anything.. i'm at a screen that says "grub>" and if i try the "sudo update-grub" command, it doesn't work saying sudo isn't a command.

---

### Post by ronparent on 2010-09-16
If '/dev/mapper/nvidia_cbfdcbae6' is where your Kubuntu is installed you are on the right track. Then:

> ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_cbfdcbae6 /mnt

should mount your Kubuntu file system on /mnt.

Then:

> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_cbfdcdae

should have written the grub 2 boot loader to your raid. The memory leak business is meaningless. Get the boot info script from here: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

If you run it and post the results I'll get a better picture of what is going on.

---

