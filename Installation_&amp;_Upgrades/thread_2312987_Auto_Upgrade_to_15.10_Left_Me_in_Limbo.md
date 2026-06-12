---
title: "Auto Upgrade to 15.10 Left Me in Limbo"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by BudTuba on 2016-02-08
OK...this is not a hardware problem.  On my desktop that I like to use for CAD work, I started my U 14.04 the other day and was given a choice to upgrade to 15.10.  I thought...perhaps that would be a good idea.  So I opted for the upgrade and several hours later with tile downloads (2495 files of them) my computer restarted and it was NOT taken to the new installation, but what looked like the Terminal command line window.  It asked for my User Name and Password.  I finally figure out what it decided my User Name was and since my password has been the same for some time, I got past that.  But U 15.10 did not open to a Desktop.  I had used my Boot Repair CD to repair GRUB and it now shows the old U 14.04 on one hard drive and the new U 15.10 on a second hard drive.  My machine is a dual boot situation with Win XP on the second hard drive.  I was never asked during the installation to change the patitions or what hard drive I wanted to install on.  It did everything automatically.  But it does not go to the Desktop of the U 15.10 installation.  I need help with this.  I am not a strong Linux user.  If you want me to run a routine on Terminal, you will have to spell it out so I can cut and paste.  This would have to be done in the first drive U 14.04 Desktop that does start up...albeit not to the saved Desktop I had been previously using (image, programs, etc.)

---

### Post by kansasnoob on 2016-02-08
I'm a bit confused by the general layout of your system. I get that it's a dual-boot with Windows but did you also have two different Ubuntu installations? Since you can boot some Ubuntu (would also work using a live DVD/USB) please use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") to create a boot info summary and post that result here as it will help immensely in understanding what we're working with. DO NOT RUN THE RECOMMENDED REPAIR, just create a boot info summary and post the URL here.

---

### Post by grahammechanical on 2016-02-08
Your description of the problem has left me confused. You get a Grub boot menu that offers to load Ubuntu 14.04, Ubuntu 15.10 & Windows XP. Correct? What happens when you accept each of those options?

You can get to a working desktop by selecting Ubuntu 14.04 from the Grub menu. Correct? If so open a terminal and type

```
sudo update-grub
```

Watch the printout. It will list the OS detected on both drives. Post the output in this thread. But check first if the Grub boot menu has changed. And if the results have changed.

Another command that we can run to check what version of Ubuntu we are using is this

```
lsb_release -a
```

It will show something like this
> 
graham@sdb7-Dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial

Let us clear up the confusion about having 2 versions of Ubuntu when one of them was supposed to be upgraded to the other one. Then if you still cannot get to a working desktop with 15.10 we will see what can be done.

The loading of a Linux OS follows a certain pattern. First, Linux loads. Then Ubuntu has to log in to Linux using your name & password (which it knows). Then Ubuntu loads to a login screen. So, that request for a password at what is the Linux command line might just be a normal event that needs a little bit of time to work. I have found that if we use an open source video driver then messages like that are hidden by a purple splash screen but with a proprietary video driver we see some system messages.

Regards.

---

### Post by BudTuba on 2016-02-08
OK kansasoob, I will rerun Boot Repair and send the info in about 12 hours (tomorrow).  I did, however, already run it using the recommended repair twice and can send you the links to those info files sent to Ubuntu.  The system has several hard drives, but the issue is between two of them:  Drive A and Drive C.  Drive A has the U 14.04 on it.  Drive C has two partitions, one with U 15.01 and the other with Win XP   When Boot Repair was run, the question was posed,  Is Drive A a removable drive?.  The first time I ran Boot Repair I answered NO.  The second time I answered YES.  I was frankly confused by the question.  Drive A is a hard drive that COULD be turned off or not.

---

### Post by ian-weisser on 2016-02-08
> **BudTuba said:**
>   Drive A has the U 14.04 on it.  Drive C has two partitions, one with U 15.01 and the other with Win XP 

That makes your situation much clearer.
There is no supported upgrade path directly from 14.04 to 15.10, You should not have been offered such an upgrade.
There is a supported upgrade path from 15.04 to 15.10, and since 15.04 just EOL you were almost certainly offered such an upgrade very recently.

Pro tip: The release numbers represent year and month. 14.04 represents 2014.April. 15.10 (not 15.01) represents 2015.October.

Back to grahammechanical's question in post #3: Please verify that your 14.04 system works properly, that your XP system works properly, and that your 15.10 system is the one without graphical login.

You wrote that your 15.10 system takes you to a text login, not a grub prompt. If so, boot-repair won't help you...the system already is booting from the proper disk. Do you see the splash screen at all?

Did you notice any error messages during the release-upgrade?

---

### Post by kansasnoob on 2016-02-08
> **ian-weisser said:**
> That makes your situation much clearer.
There is no supported upgrade path directly from 14.04 to 15.10, You should not have been offered such an upgrade.
There is a supported upgrade path from 15.04 to 15.10, and since 15.04 just EOL you were almost certainly offered such an upgrade very recently.

Pro tip: The release numbers represent year and month. 14.04 represents 2014.April. 15.10 (not 15.01) represents 2015.October.

Back to grahammechanical's question in post #3: Please verify that your 14.04 system works properly, that your XP system works properly, and that your 15.10 system is the one without graphical login.

You wrote that your 15.10 system takes you to a text login, not a grub prompt. If so, boot-repair won't help you...the system already is booting from the proper disk. Do you see the splash screen at all?

Did you notice any error messages during the release-upgrade?

About this:

> There is no supported upgrade path directly from 14.04 to 15.10

Yes there is. Beginning about the time Utopic went EOL the devs made it so LTS releases will jump over EOL releases and upgrade directly to the next supported release if the user changed the setting in update manager from "notify only of LTS versions" to "notify of any new release". Please see:

[http://ubuntuforums.org/showthread.php?t=2312528](http://ubuntuforums.org/showthread.php?t=2312528)

If i had my druthers they'd just have made it much harder to upgrade an LTS version to anything that's not LTS.

---

### Post by deadflowr on 2016-02-08
> **ian-weisser said:**
> That makes your situation much clearer.
There is no supported upgrade path directly from 14.04 to 15.10, You should not have been offered such an upgrade.


They've been moving it to allow upgrades to non-lts releases other than the next release after the lts.
When 14.10 died, they allowed upgrades to 15.04, and now that 15.04 is dead they allow upgrades to 15.10.
I wouldn't recommend doing any of those, but to each his own:

Here's a screenie of my update-manager, I changed it to see some time ago and simply ignore the upgrade option.:

Edit:Ninja'd

---

### Post by BudTuba on 2016-02-09
Here are the two logs sent to ubuntu:

//paste.ubuntu.com/114986470  Drive A answered not removable  Grub placed U 15.10 as alternative at bottom

//paste.ubuntu.com/114988304  Drive A answered as removable.  Grub placed U 15.10 at the top

---

### Post by kansasnoob on 2016-02-09
I think you had an extra one at the beginning of each of those:

[http://paste.ubuntu.com/14986470/](http://paste.ubuntu.com/14986470/)

[http://paste.ubuntu.com/14988304/](http://paste.ubuntu.com/14988304/)

Give me a little while to parse that.

---

### Post by kansasnoob on 2016-02-09
I notice there's a fourth drive in one of those:

```
Model: Hitachi HTS545050B9A300 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  461GB  461GB  primary  ntfs         boot
```

So I suspect that drive is a USB external drive?

Otherwise there are three suspected internal drives:

```
=================== parted -l:

Model: ATA Maxtor 6Y080L0 (scsi)
Disk /dev/sda: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  82.0GB  82.0GB  primary  ext4         boot


Model: ATA WDC WD2500JB-22R (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
2      1049kB  250GB  250GB  primary  ntfs         boot


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  210GB  210GB   primary   ntfs
2      210GB   214GB  4295MB  primary   linux-swap(v1)
3      214GB   499GB  285GB   primary   ext4            boot
4      499GB   500GB  998MB   extended                  lba
5      499GB   500GB  998MB   logical   ext2            lvm

```

And there are two Ubuntu's:

```
sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
```

```
sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sdc3 
                       and looks at sector 541966161 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos3)/boot/grub.
    Operating System:  Ubuntu 15.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img
```

Are we on the same page so far? I assume you can still boot the Ubuntu 14.04 on /dev/sda1? You can see for sure just by running df in the terminal but I suspect that must be right.

---

### Post by kansasnoob on 2016-02-09
It rather looks to me like that upgrade did not complete properly because you're still on the 3.13 series kernel, but Wily (15.10) should be up to the 4.2 series kernel:

```
chroot /mnt/boot-sav/sdc3 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdc1
```

Something I'm not sure of is which systems grub you're booting with because I can't be sure which drive is set to boot first in BIOS. This really doesn't matter but we're going to need you to boot into the non-working Ubuntu by selecting the advanced boot option from grub and then select recovery mode so you can work from there. You'll need to type some commands but they're simple.

I just want to be absolutely clear that you understand what I'm talking about so far, then I'll provide more info about using recovery mode :)

---

### Post by kansasnoob on 2016-02-09
I may be AFK for a while soon so I wanted to type the procedure I spoke of above.

First select the advanced boot option for the borked Ubuntu install from the grub menu and next select the recovery mode option for the latest kernel. If that fails for some reason it may be worth also trying that with an older kernel.

Once you get to the recovery menu you'll see an option to enable networking. Use the arrow keys to select/highlight enable networking, then use the tab key to highlight OK at the bottom of that screen, and then hit the enter key. You'll be asked to confirm that you want to mount things read/write so confirm that you do. Then you'll be returned to the recovery menu again. Now use the arrow keys again to select drop to root shell and repeat the above steps, then you'll see that you have a shell as root indicated by the #. Since it's a root shell there is no need to use sudo. The commands I'd recommend are:

```
apt-get update
```

Make note of any obvious errors - a camera could come in handy.. Then next:

```
apt-get -f install
```

That's mostly informational and should show if any packages are installable, upgradeable, etc. Based on the kernel info I'd almost bet the release upgrade was incomplete so you'll likely need to run:

```
apt-get dist-upgrade
```

At the end of that you may be asked to run "apt-get autoremove".

Another command that often comes in handy is:

```
dpkg --configure -a
```

That is typically used when package configuration is incomplete.

**You may need to repeat any or all of the above (in no specific order) to clear any errors.** When you're done playing in recovery mode just type:

```
reboot
```

Then let the default grub entry boot. **This is especially important if the other Ubuntu controls boot in which case you'll need to run "sudo update-grub"** before trying to boot the borked upgraded install.

Good luck, I'll try to pop back by here as I have time.

---

