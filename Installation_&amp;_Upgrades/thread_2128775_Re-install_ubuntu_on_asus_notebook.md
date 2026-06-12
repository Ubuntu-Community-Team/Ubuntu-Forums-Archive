---
title: "Re-install ubuntu on asus notebook"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by beacon on 2013-03-24
I bought an ASUS Eee Pc Seashell Series (with a French keyboard if that makes any difference). It is 'ubuntu certified' and had a version of Ubuntu on it. I changed from Ubuntu to Mint some time back on my desktop, as I couldn't get on with the Unity desktop. I disliked it on the notebook as well and spent days trying to install Mint in place of it. I didn't succeed so paid a computer shop to install Mint, even though they found they could not install the latest version--only Mint 7. 

That has proved unsatisfactory, so I want to replace it with, say, Easy Peasy. Again I have spent days and have been unable to install any OS including Ubuntu. I have read through all the postings I can find. Although they remark on how easy it is to return to factory settings, nothing works for me. The same is true for installing Easy Peasy. It looks so simple: just put it on a flash disk and all will be well. Again, that doesn't work for me. I have tried as well with other operating systems.

I will even return to Ubuntu if I can figure out how to do it. I wonder if anyone can help. 

I will probably be told that I haven't provided enough information, but there is no model number on the notebook, only the information given above.

---

### Post by ibjsb4 on 2013-03-24
Going on the information you supplied, it sounds like that is the only operating system installed.  Do you have any files you need to save on the current install?  If not, you could burn a CD and use the option to try ubuntu before installing and then install using the entire disk if it worked.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

No CD?  You can do a flash drive the same way.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If your lucky enough to get ubuntu install and working you could then install a different desktop.  You say Unity is not for you, then maybe gnome-classic would be more to your liking.  Its like the old gnome (10.04) desktop.

Im just throwing some ideas at you.  Let me know what you think.

---

### Post by p-dh on 2013-03-24
I have 5 Seashell netbooks that I use for a computer lab. During the workshops, my students have installed Ubuntu multiple times on the netbooks. The only failure that I have experienced was when I created a Polish installation copy using something other than the Ubuntu Customization kit - my fault entirely. The model I use is the 1015BX.
This is what I have found:
* I use 12.04.2, 32-bit. 
* I DO NOT use the proprietary graphics driver as they tended to make it more difficult to install. I installed them and then the machines wouldn't boot right. I finally got them to work, but found that the open drivers worked better anyway.
* I use Unity and LightDM to log on (although I had to switch to gdm to troubleshoot something).
* I always install with a wired connection - not wireless. I've been playing around with wireless network booting the last few days and have had difficulties.
I would encourage you to install the basic 12.04 Ubuntu with Unity. Before you start the install, go into the BIOS, hit F9-<Yes>-F10-<YES> and  turn off the machine when the boot screen comes up. Then, turn it on again (makes sure that the BIOS has properly accepted the new settings.) Delete all partitions on the hard drive (you can use dd to copy the partitions first, if you want). Then, install from scratch and update everything. From my experience, it should work. Once you have a workable system, then install KDE, GNOME, etc. and see if something else works better for you. 

Paul :cool:

---

### Post by beacon on 2013-03-24
Thanks very much for the two quick replies. They are much appreciated. 

First, I might add some information I found in the BIOS. The BIOS version is 1001 and the build date is 05/30/2012.

Second, taking the suggestions of ibjs4 I understand that the computer mechanic, if I can call him that, wiped the hard drive and then installed Mint 8 (not 7, as I said inititally). So yes, there is only one OS installed, and it hasn't been used so there is nothing I want to keep.

I have tried to find a way to wipe the hard drive and start from scratch, but no joy. I have also tried various ways to add another operating system. I have used live dvd's from Linux magazines, but am unable to get the one program I want out of the many on the disk to transfer to Unet booting or USB image writer. I have burned copies of Puppy, Mint, Easy Peasy and others, and transferred them to a flash disk. But when I try to boot, Mint on the hard drive is the only thing to appear. 

Before I try to burn Ubuntu 12.04, as suggested by Paul, may I set out my method in case I am missing something simple. When I go into the bios, under boot, there is only 'boot option 1: SATA. Undeer that is 'disabled, which I am unable to change. On occasion it will recognise the flash disk, and I change the boot option (when I am permitted, which is not always), but when I boot, Mint comes up from the hard drive. I haven't been able to boot anything from a memory stick. I do install with a wired connection by the way. I'm not certain what it means to log on with Unity and LightDM and wonder if you could clarify that for me. 

Thanks again.

---

### Post by p-dh on 2013-03-24
You will need to boot from a LiveCD and delete the present partitions, and then install the OS. To do this:
[LIST=1]
[*]Put a bootable USB with LiveCD in a USB port.
[*]Repeatedly press the <ESC> key during boot up. You should be presented with an option to choose what you want to boot from (no need to change it in BIOS).
[*]Choose the USB drive. If you are given two options for the USB drive, use the one that is NOT efi.
[*]Once the OS is loaded from the USB, start gparted and follow this [link]("http://www.dedoimedo.com/computers/gparted.html") for instructions on how to delete partitions. 
[*]Delete all of the partitions - starting first with the one on the bottom and working to the one on the top.
[*]Make sure to hit apply to write the changes.
[*]Install the new OS following the its installation instructions (for Ubuntu, you simply double click on the "Install..." icon).
[/LIST]
Hope this helps.

Paul :cool:

---

### Post by beacon on 2013-03-25
Thanks very much for your patient help. The step-by-step pattern is what I needed. However, I am having the same problem as always. I can't get past step 3. I am given a choice when I boot of SATA and Scandisk flashdrive. I tick the latter, but Mint appears within a couple of seconds. I just can't get a flash disk to work. Any other ideas would be appreciated.

---

### Post by p-dh on 2013-03-25
Your flash drive may not be setup correctly. I have found that the following steps are most likely to produce a bootable USB flash drive.
[LIST=1]
[*]Use gparted to delete all the partitions on the flash drive. 
[*]Create a 2 gigabyte partition (anything over 4 gigabytes can be problematic) and format it as fat32.
[*]Reinstall the LiveCD using **Startup Disk Creator**. DO NOT create a persistent space (i.e. choose "Discarded on shutdown...").
[*]Wait until the program exits (you may have to type in your password to unmount the USB flash drive).
[*]Insert into netbook USB port, boot, hit <ESC> at the boot screen and choose the USB flash drive as your boot device.
[/LIST]
Please note that I have had problems with certain flashdrives. If you have a different brand, try it.

Paul
:cool:

---

### Post by beacon on 2013-03-25
I'm sorry, but my ignorance seems to know no bounds. I have tried several brands of flash drives and have the same problem with all of them. I have tried to format on a friend's Windows 7 computer and on my own with Linux Mint. Windows say 'cannot compete the format', and when I use Linux and go to Gparted I get the following:

unallocated
/dev/sda2  extended
  /dev/sda7  ext 4
  /dev/sda5   fat32
  /dev/sda6   fat 32
/dev/sda1  ext 2  

When I try to delete any partition I get the following message:

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

OR the following:


A new partition table cannot be created when there are active partitions.  Active partitions are those that are in use, such as a mounted file system, or enabled swap space.
Use Partition menu options, such as unmount or swapoff, to deactivate all partitions on this device before creating a new partition table.


Whatever I try, such as unmount, simply fails.

I apologise if this is something quite simple or needs to be a new thread, but it seems to be a block to going further with the initial problem.

---

### Post by beacon on 2013-03-25
I think you can probably ignore most of the lengthy item above. I finally made a bit of progress, although it seems I took one step forward and two back.

I have tried four flash disks, with no luck whatsoever.

1. San Disk: 'liberated bug found: input/output error during write on/dev/sdb

2. Vimpat: after I tick 'create new partition table', and then 'apply', it goes back to the beginning, where I have to tick create again.

3. Transcend: unable to mount location

4. Emtec: unable to mount location.

i have spent the afternoon trying to find out from the posts how to overcome the last two messages and find a way to mount, but no joy.

Needless to say, I am frustrated and don't know whether it is me, the disks, or something else. If there is anything more that can be suggested I am more than ready to try.

---

### Post by p-dh on 2013-03-27
From your next-to-last post, it looks like you were trying to change partitions on your hard drive - not the USB. Good thing that it wouldn't allow it. Please plug in your USB drive and run fdisk from the command line - **sudo fdisk -l**. Also run **mount**. Please copy and post the output from both commands.
I had a problem with an older Asus computer yesterday. I ended up having to change both the boot priority (USB first) and hard drive priority (USB first) in BIOS. Then things worked okay.

Paul :cool:

---

### Post by beacon on 2013-03-27
Alas your warning came too late. I now see how stupid I was, but I have re-installed Linux Mint 14!! I have pasted below the results of the two commands you suggested.  I don't know how to copy in the proper format. It is o.k. when I paste, but when I 'submit', it comes out as below.   Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x0006ac38     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *        2048   961050623   480524288   83  Linux /dev/sda2       961052670   976771071     7859201    5  Extended /dev/sda5       961052672   976771071     7859200   82  Linux swap / Solaris   /dev/sda1 on / type ext4 (rw,errors=remount-ro) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfsd-fuse on /run/user/larry/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=larry)

---

### Post by beacon on 2013-03-28
The problem hasn't been solved, but I have managed to reach a conclusion. With a red face, since the computer shop had spent a lot of time putting on Mint instead of Ubunut, I asked them to reverse the procedure. That has been done, and I now have Ubuntu 12.04, albeit with the nefarious Unity desktop, and hope there are no more problems. They had a difficult time re-installing, so it wasn't only my problem, but they succeeded.

---

