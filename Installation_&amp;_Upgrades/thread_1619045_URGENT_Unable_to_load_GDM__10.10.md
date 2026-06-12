---
title: "URGENT: Unable to load GDM  10.10"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2010-11-11
Through Hardware drivers I deactivated the nvidia proprietary driver with the intention of reactivating it after a reboot. It was supposed to speed up the OS.

An error message arose at the end of the deactivation. I rebooted and now can not load GDM. I am currently using the live CD as I can not access the desktop. 

I am able to login to the system.
At the login console I have  tried sudo  -gdm -restart
  Error messsages:
     Failed to acquire org.gnome.display manager
     Could not acquire name: bailling out.

I had guessed it is something to do with xorg.conf. I can not find a copy at /etc/X11 However I read that xorg.conf has been phased out and I should not need it.

How can I switch the proprietary driver back on in the hard disk when I am running the live disk.

Is there a repair system program?

If that does not work what should I do next to get the GDM to load? 



(I hate the idea of having to reinstall and recall hundreds of programs and settings on a clean install.)

Robin

---

### Post by sikander3786 on 2010-11-11
Hi.

Boot into recovery mode. You'll need to press and hold Shift key at your Bios screen until you see the Grub menu. Recovery should be the 2nd on the list. You'll then get a choice to reconfigure your graphics. Reconfigure and reboot to see if it helped.

xorg.conf is not needed anymore by modern X. Reconfiguring graphics should do that.

I hope you don't need to reinstall :-)

---

### Post by Robbyx on 2010-11-11
I can not get grub options to load. Despite holding down the shift key, it is bypassed and loads from the HD without giving me the grub options.

It looks as if I will have to do a fresh install:

I have my /home is a separate partition

I am going to back up all of etc when  I can work out how to do it from within the live CD. I have a permission problem.

I will also backup /var/cache/apt/archives

Are the software sources in etc? 

Should I reformat the boot partition or just point the installer at that partition?


Hope you can comment.

Robin

---

### Post by houseworkshy on 2010-11-11
I think the command would be sudo start gdm rather than  sudo  -gdm -restart

---

### Post by sikander3786 on 2010-11-12
If it is a clean install of 10.10 with Grub2, the Shift key should work. Hope you've tried a couple of times with both Right and Left Shift. You needed to hold it down until you see the menu.

> 
Are the software sources in etc? 


Did you add some custom sources, if not then backing up sources.list will be of no use because a new one will be generated at the install.

/etc/apt/sources,list

Custom added PPAs should be in,

/etc/apt/sources.list.d

> Should I reformat the boot partition or just point the installer at that partition?

Yes it would be better to format both /boot and / Ubuntu root partition so it doesn't contain any data from the previous install. Clean install makes sense after formatting them

Don't format /home.

> I am going to back up all of etc when I can work out how to do it from within the live CD. I have a permission problem.

If your /home is not encrypted, you can just go to terminal and launch nautilus with root permissions and you'll be able to copy any needed stuff.

```
gksu nautilus
```

---

### Post by Robbyx on 2010-11-12
Thank you for your comments. I am not finding the solutions easily. If I do one thing it appears  blocked by another problem:

**Grub**

I have failed to get the grub options to load and can not find a control file that I can alter to require the grub options to appear on start up. I think that grub file is missing and that is why SHIFT is not having any effect. 

Grup does load as part of the hard disk startup of Ubuntu.

**Backing up /etc/**

Using gksu nautilus I am not seeing the correct version of  /etc/.

[INDENT]I think I am seeing /etc that has been loaded into memory via the live cd. 

I can not see the installed installation on the hard disk.
[/INDENT]


Using places, computer I can see the hard disk with the original installation but can not copy most of the files because of a lack of permission.

**Summary: With gksu nautilus I cannot find the files I wish to backup. Without it I can find them but can not copy them.**


**Live CD installation**


As I have not been able to back up the /etc/ directory I have tried to do an installation from the live CD without reformatting the original installation on SDA1. 

In the installer I set SDA1 as the boot. (SDA2 is home)

I am unable to proceed because the installer asked for the root to be set within the partition manager. How do I do that?  I assume it is SDA1 but I have not noticed how I can designate that drive both as boot and root.

Robin

---

### Post by sikander3786 on 2010-11-12
Find your intended partition by

```
sudo fdisk -l
```

Create a mount point, I'll be doing this in /media

```
sudo mkdir /media/ubuntu
```

Mount your desire partition

```
sudo mount /dev/sdXX /media/ubuntu
```

Replace sdXX with whatever your partition e.g, sda1 or sda2 or sdb1 for instance...

Start Nautilus by gksu nautlius, navigate to /media/ubuntu and you'll see your drive, copy over what ever you want to.

You might also find /etc/default/grub and /etc/apt/sources.list in there.

Hope it helps this time.

---

### Post by Robbyx on 2010-11-12
> In the installer I set SDA1 as the boot. (SDA2 is home)

I am unable to proceed because the installer asked for the root to be set within the partition manager. How do I do that? I assume it is SDA1 but I have not noticed how I can designate that drive both as boot and root.


Can you comment on the above about setting the root and boot to the same partition?

Thanks for the rest of your answer. I have been able to copy all of /etc/. 
/etc/default/grub is missing!

Robin

---

### Post by sikander3786 on 2010-11-12
Couldn't quite understand that statement.

If you want your Ubuntu root partition to hold your boot files as well instead of having a separate /boot, just create a / partition during installer and it will happily put your boot files in there.

For more info, please post the output of

```
sudo fdisk -l
```

---

### Post by Robbyx on 2010-11-12
Here is my disk setup. Is it saying that I have a separate boot partition? SDA1 seems to be described as both the boot disk and the root.Am I not understanding the output?

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3725    29921031   83  Linux
/dev/sda2            3726        7647    31503465   83  Linux
/dev/sda3            7648       60057   420983325    5  Extended
/dev/sda4           60058       60801     5976180   82  Linux swap / Solaris
/dev/sda5            7648       21000   107257941   83  Linux
/dev/sda6           21001       60057   313725321   83  Linux

Disk /dev/sdd: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3aa5e04


fstab shows:

proc                                       /proc          proc         defaults                               0  0  
UUID=3fb00645-ed14-46fa-a0b4-5c384add8c90  /              ext3         relatime,errors=remount-ro             0  1  
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b  /home          ext3         nodev,nosuid,relatime                  0  2  
UUID=e36cb6cf-f372-4418-bd8b-f36a27dc3e76  none           swap         sw                                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                  0  0  
UUID=724E07853D78E7A8                      /media/mydocs  ntfs         user,rw,auto,exec,nls=utf8,unmask=007  0  2  
UUID=f35c7bf9-9c2b-4ec9-9522-84d73f3c37db  /media/f       reiserfs     noatime,user,notail,rw                 0  0  
UUID=7b859c36-c68d-408f-9425-de9f525f3c71  /media/g       reiserfs     noatime,user,notail,rw                 0  0  
UUID=86290d05-e673-4310-9f3e-93af30cc13af  /media/video   reiserfs     noatime,user,notail,rw                 0  0  
UUID=4A16-E85E /media/sda1 vfat 
none                                       /proc/bus/usb  usbfs        devgid=126,devmode=664                 0  0  
/dev/sdc1                                  /media/sdc1    vfat         user,rw,noauto,exec,utf8                              0  0  
localhost:/wuala /home/luzius/wuala/direct nfsdefaults,users,noauto,rsize=8192,wsize=8192,timeo=60,acregmin=10,noac,intr,nolock,soft

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7840     2007024    e  W95 FAT16 (LBA)

Disk /dev/sde: 250.1 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   fd  Linux raid autodetect
ubuntu@ubuntu:~$ 


---

### Post by sikander3786 on 2010-11-12
Yes seems like sda1 is the separate /boot partition.

What do you want to accomplish now? Reinstall with separate /boot partition? Or just let / handle all that stuff?

---

### Post by Robbyx on 2010-11-12
> **sikander3786 said:**
> Yes seems like sda1 is the separate /boot partition.

What do you want to accomplish now? Reinstall with separate /boot partition? Or just let / handle all that stuff?

Unless you advise against it I was trying to install over the top of the existing installation so that I keep as much of my old settings as possible, but replace damaged or missing files. This would mean keeping the setup as it is. Is this possible or should I go for a reformat of the sda1?

When I tried to follow  the above over write installation I had the message that it needed a root location and I could not see how to make SDA1 both root and boot. If that is not possible then I will be forced to reformat and create  separate boot and root partitions.

---

### Post by sikander3786 on 2010-11-12
> Unless you advise against it I was trying to install over the top of the existing installation so that I keep as much of my old settings as possible, but replace damaged or missing files. This would mean keeping the setup as it is. Is this possible or should I go for a reformat of the sda1?

I am not sure if it is possible. Not sure either if it is impossible. If you've got the time, you can try yourself and let us know how it goes :-)

To make a partition your / root partition, select Manual partitioning from the installer, highlight your partition and click edit. Select '/' as the mount point and you'r done.

You can do that for /boot, /home etc as well.

If you intend to keep you previous /home drive, you need to specify the mount point same as above.

---

### Post by Robbyx on 2010-11-12
As my system seemed flaky I decided to format the / and put a clean system in it.

**1. Sources.list.d**

I copied over the old folder that I had backed up. When  I go into the update manager I get an error message:

> Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Unable to read /etc/apt/sources.list.d/ - opendir (13: Permission denied)'


I have looked at the permissions of the other directories in apt and they are the same as the directory I have copied over. Any ideas how to resolve it? I have looked again and there are some differences and have changed them, but I am concerned at compromising my file integrity and so I am going to do another clean install.

**2.Nvidia twin screen**

I am not retaining the dual screen settings between boot. Do I have to create an xorg.conf for the settings to be retained?

**3. ATA5 SRST failed (error no =-16)**

This fault was there before I did the clean install. Any idea what to do to make it go away? It shows up when the the system is rebooted.


Robin

---

