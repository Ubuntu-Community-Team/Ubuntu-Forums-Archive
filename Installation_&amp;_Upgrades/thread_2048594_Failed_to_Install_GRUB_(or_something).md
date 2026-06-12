---
title: "Failed to Install GRUB (or something)"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by thenewasbo on 2012-08-26
I've been trying to install Ubuntu on to my PC. I have Windows 7 of one partition and 200GB of free space. I've tried the express install feature with Ubuntu 12 (the top option). It creates its own partitions and then gives me an error.
 
I forget exactly what the error is but it fails to install GRUB or something like that and I think that's the bootloader. It asks me to install it in a different place but each one just causes my computer to reboot right back into Win 7. This could be because I had installed the Consumer Preview version of Windows 8 and instead of uninstalling it properly (however that may be) I just deleted the partition that it was on, and that became free space for Ubuntu. 
 
Any suggestion?

---

### Post by darkod on 2012-08-27
Are you running raid maybe? Usually grub2 doesn't install correctly on raid if you are using the live cd. The Alternate CD should be used for raid.

Sometimes grub2 can fail to install but usually you can add it without reinstalling the whole of ubuntu.

If you are not running raid, boot into live mode with the ubuntu cd, open terminal and post the output of:
```
sudo fdisk -l
```

---

### Post by thenewasbo on 2012-08-27
You know what? I am running in Raid 0. Where do I get this Alternate CD? And I wonder what the difference is.

---

### Post by darkod on 2012-08-27
The full list of links is here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Watch carefully the file names, you will see alternate i386 for 32bit, and amd64 for 64bit (all 64bit CPUs).

But in this case you might be able to add just grub2, if you want to try. No reinstall is necessary.

If you want to try, boot into live mode and post the output of the fdisk command I posted earlier. It should show the array like /dev/mapper/blahblah. When there is a number at the end, it means partition number. When there is no number, it means the MBR of the array, similar like when we are talking about a single disk.

You need to note down the exact device name for the array, and install grub2 to its MBR. Before that, you need to mount the root partition, usually #5 on the array, so that grub2 knows where your / is. In the fdisk results confirm if your Linux partition is really #5, and then to install grub2 on the MBR, run something like:
```
sudo mount /dev/mapper/blahblah[COLOR=Red]5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/blahblah
```

Note that in the first command the partition number is used, and in the second there is no number because you want the destination to be the MBR of the array.

That should work, but if it doesn't, and you can't even boot windows, don't panic. You can always work from live mode, come back here and we'll sort it out.

---

### Post by thenewasbo on 2012-08-27
I received the same error while using the 64-bit alternate CD. I'm going to try what you said now.

---

### Post by albert s on 2012-08-27
Im having serious trouble getting grub to work, simply keeps coming back saying 'fatal error'
raid1
ubuntu 12.04

---

### Post by thenewasbo on 2012-08-27
I used the LiveCD (the 32-bit) and opened the terminal. 
I used the "sudo fdisk -l" command and it gave me this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
fdisk: unable to seek on /dev/sdb: Invalid argument
ubuntu@ubuntu:~$ 


The thing is, I have two 500 GB drives running in RAID 0. I'm not sure what to do at this point.

---

### Post by darkod on 2012-08-28
It doesn't seem it recognizes the partition tables. Windows might have messed something up, so it can work only with windows. :)

Not sure what is going on exactly. When you tried the alternate install, did it ask you if you want to activate the raid?

---

### Post by chrisbay90 on 2012-08-28
I too am having a similar problem. I have installed Ubuntu 12.05, it fails with a non-descript cannot install grub error. I have tried, from the live CD to install grub, it says it installs grub. But there is no grub at reboot. I have booted into a server disc and chosen rescue system. If I choose to install grub it then fails with a nonn descript cannot install error. If I go into a shell on my linux partition from the server rescue CD and install grub it apparently installs okay. But alas no grub for me on reboot.

fdisk -l in picture. /dev/sdb1 is the USB thumbdrive I am using.

---

### Post by darkod on 2012-08-28
> **chrisbay90 said:**
> I too am having a similar problem. I have installed Ubuntu 12.05, it fails with a non-descript cannot install grub error. I have tried, from the live CD to install grub, it says it installs grub. But there is no grub at reboot. I have booted into a server disc and chosen rescue system. If I choose to install grub it then fails with a nonn descript cannot install error. If I go into a shell on my linux partition from the server rescue CD and install grub it apparently installs okay. But alas no grub for me on reboot.

fdisk -l in picture. /dev/sdb1 is the USB thumbdrive I am using.

This is not very similar, you are not using raid, you have only one disk. In your case you should install grub2 to /dev/sda. Is that failing? Is that where you tried to install it?

---

### Post by chrisbay90 on 2012-08-28
> **darkod said:**
> This is not very similar, you are not using raid, you have only one disk. In your case you should install grub2 to /dev/sda. Is that failing? Is that where you tried to install it?

Ah yes, sorry. Didn't want to create a new thread if unnecessary. Can't seem to delete post

Yes, that is what happened:
Guided CD install -> grub install failed with error
Subsequent attempts -> Install finishes silently, but grub not actually there.
**From live cd "grub-install /dev/sda --boot-directoy=<{mounted/dev/sda1}/boot/grub>"  cli says install okay, but BIOS still does not boot to HD.**
Boot server disc, select recovery, select reinstall grub, select /dev/sda, fails with unspecific error.

---

### Post by darkod on 2012-08-28
> **chrisbay90 said:**
> Ah yes, sorry. Didn't want to create a new thread if unnecessary. Can't seem to delete post

Yes, that is what happened:
Guided CD install -> grub install failed with error
Subsequent attempts -> Install finishes silently, but grub not actually there.
**From live cd "grub-install /dev/sda --boot-directoy=<{mounted/dev/sda1}/boot[COLOR=Red]/grub[/COLOR]>"  cli says install okay, but BIOS still does not boot to HD.**
Boot server disc, select recovery, select reinstall grub, select /dev/sda, fails with unspecific error.

The boot directory is not /mountpoint/boot/grub, it's /mountpoint/boot

But even though there are some opposite tutorials, I still think it's better to use --root-directory=/mountpoint instead of the --boot-directory option.

In any case, by adding the /grub you pointed it to the wrong place.

There is another question too, whether it failed only installing to the MBR or it didn't install at all, the whole package.
If it failed only the MBR part, you can add that with the commands you are trying (with the correct syntax).
If it didn't even instal the package, you need a bit more to add it.

When you have sda1 mounted (before running the sudo grub-install), look whether /mountpoint/boot/grub/grub.cfg and /mountpoint/boot/grub/core.img exist. If they do it usually means the package is installed OK. Then run the sudo grub-install and it should work.

---

### Post by thenewasbo on 2012-08-28
> **darkod said:**
> It doesn't seem it recognizes the partition tables. Windows might have messed something up, so it can work only with windows. :)
 
Not sure what is going on exactly. When you tried the alternate install, did it ask you if you want to activate the raid?
 
I don't recall it asking if I wanted to activate RAID.

---

### Post by darkod on 2012-08-28
Try this. Boot into live mode, open terminal and run:
```
sudo dmraid -ay
sudo fdisk -l
```

The first command should activate fakeraid arrays. The second should list the disk devices.

Does that list any /dev/mapper/.... device?

---

### Post by thenewasbo on 2012-08-28
This is all I got.

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_dicfhfjfjg_Volume0" already active
RAID set "isw_dicfhfjfjg_Volume0p1" already active
RAID set "isw_dicfhfjfjg_Volume0p2" already active
RAID set "isw_dicfhfjfjg_Volume0p5" already active
RAID set "isw_dicfhfjfjg_Volume0p6" already active
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
fdisk: unable to seek on /dev/sdb: Invalid argument


Also, I'm running this Ubuntu 32-bit off of a flash drive since I can't get into the one on the HDD.

---

### Post by darkod on 2012-08-28
OK, lets try something.

Boot into the live mode again, and in terminal try mounting the root partition which should be the one ending in Volume0p5 and install grub to the array which is ending in Volume0 (without any p?).

```
sudo mount /dev/mapper/isw_dicfhfjfjg_Volume0p5 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_dicfhfjfjg_Volume0
```

That should install grub to the MBR of the array. Restart and give it a go.

---

### Post by thenewasbo on 2012-08-28
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dicfhfjfjg_Volume0p5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mapper/isw_dicfhfjfjg_Volume0
Installation finished. No error reported.

This is what it gave me. I'll try rebooting and I suppose I should expect an option to boot into Linux as well as Win7...? Let's find out!

---

### Post by thenewasbo on 2012-08-28
No dice. It loads me into a black screen with white text that says something about GRUB. There's a blinking curser to insert text. Some kind of command prompt?

Also possible: This is supposed to happen? lol

---

### Post by darkod on 2012-08-28
I was afraid of this, but we tried the short way first. Not only it didn't install on the MBR of the array, it seems the grub package was never installed fully inside ubuntu. There is a longer procedure of commands that allows you to enter inside your hdd installation and reinstall grub fully. Lets start.

Mount everything needed to prepare the chroot:
```
sudo mount /dev/mapper/isw_dicfhfjfjg_Volume0p5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Purge grub, install it again and recreate the grub files:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/mapper/isw_dicfhfjfjg_Volume0
```

Exit chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart.

---

### Post by thenewasbo on 2012-08-28
"chroot: failed to run command `/bin/bash': Exec format error"

This showed up after  "sudo chroot /mnt"

---

### Post by darkod on 2012-08-28
Sorry, that was about all the ideas I have. You can try running boot-repair from live mode, you can either boot it from its own cd or just install it in ubuntu live mode and run it.

It can also repair raid installations. I am still not sure something is not messed up in the installation, hence the partition table errors.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by thenewasbo on 2012-08-28
ehh... boot repair gives me this error when I hit recommended repair.
"64bits detected. Please use this software in a 64bits session. This will enable this feature."

I'm downloading the ISO. Now I have to figure out how to burn it on Ubuntu.

---

### Post by darkod on 2012-08-28
Aha, that chroot error might have been because of that. I was assuming you are using the same version type as the system you have installed.

I don't think you can chroot into 64bit system from 32bit live mode.

But anyway, the automatic boot-repair might be the easier way.

---

### Post by thenewasbo on 2012-08-28
I was wondering about that. I don't think there's a 64-bit live version.

---

### Post by darkod on 2012-08-28
> **thenewasbo said:**
> I was wondering about that. I don't think there's a 64-bit live version.

Of course there is. The image file that says desktop-amd64. It's for all 64bit CPUs, don't let the word amd confuse you.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by YannBuntu on 2012-08-29
If I were you, i would:

1) download [Ubuntu-Secure-Remix-64bit ISO]("https://sourceforge.net/projects/ubuntu-secured/files/"), which is an Ubuntu-64bit ISO with pre-installed Boot-Repair.
See also [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

2) Make a CD or liveUSB of it. Boot on it, choose "Try Ubuntu"

3) From the Dash, run Boot-Repair, update it, click the Recommended Repair button.

4) Indicate us the URL that will appear.

5) Reboot and tell us what you observe.

---

