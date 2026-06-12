---
title: "About LVM"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-10-07
Hi all,

I newly installed Ubuntu 12.04.1 from ubuntu-12.04.1-desktop-amd64.iso 

Installation went through without problem but without LVM.  Ubuntu is now up running.

I ran following command trying to mount LVM but failed;

# apt-get install lvm2
# vgchange -ay```

No volume groups found

```

Please help.

Which ISO should I use to install LVM?  ubuntu-12.04.1-alternate-amd64.iso ?

TIA

B.R.
satimis

---

### Post by darkod on 2012-10-07
You can't activate LVM when it doesn't exist.

Yes, you need to use the alternate cd to configure LVM during installation.

---

### Post by satimis on 2012-10-08
> **darkod said:**
> You can't activate LVM when it doesn't exist.

Yes, you need to use the alternate cd to configure LVM during installation.
Still fail.

Performed following steps

1)
Download "ubuntu-12.04.1-alternate-amd64.iso" and burned it on USB drive/stick

2)
Booted up the PC with the said drive/stick.  Deleted old partitions and created new partitions with LVM /root.  Installation went through without problem

3)
Started Ubuntun 12.04 desktop.  Ran "sudo apt-get update && sudo apt-get upgrade"

4)
On terminal

$ sudo fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfde6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      585727      291840   83  Linux
/dev/sda2          587774   154882047    77147137    5  Extended
/dev/sda3       154882048   156835839      976896   82  Linux swap / Solaris
/dev/sda5          587776   154882047    77147136   83  Linux

```

$ sudo apt-get install lvm2

$ sudo vgchange -a y```

  No volume groups found

```

Pls help.  TIA

B.R.
satimis

---

### Post by darkod on 2012-10-08
It seems you are missing one of the basic steps, you have no LVM partition on the disk. As you can see from the fdisk results, there are two Linux and one Linux swap partitions. There is no Linux LVM partition.

Did you read any LVM tutorials first and try to install it or you just came here to ask without bothering to read anything? You haven't done any basic steps.

When you are doing the partitioning and you create the partition you plan for LVM, when you select it in the Use As option you need to select Physical device for LVM. That will mark it as LVM.

After that you need to go into the option Configure LVM to configure the volume group and logical volumes.

And why are you creating many separate partitions, the point of LVM is all LVs to be inside it.

I don't think you understand how it works and you need to read more, it might not even be suitable for the way you want to use your computer.

---

### Post by satimis on 2012-10-08
I followed;
HowTo: Setup Ubuntu Desktop with LVM Partitions
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

to install Ubuntu.  But it didn't start two options of "Try Ubuntu" and "Install Ubuntu"

Then I continued the installation without manual and came to the result as posted previously.  Ubuntu was installed in about half space of the HD leaving the rest space for another Linux OS.

I made another round installing Ubuntu on the complete space of the HD.  Then I was allowed to create LVM.

$ sudo fdisk -l```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000948c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/mapper/lvm-root: 70.7 GB, 70678216704 bytes
255 heads, 63 sectors/track, 8592 cylinders, total 138043392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm-root doesn't contain a valid partition table

Disk /dev/mapper/lvm-swap_1: 8317 MB, 8317304832 bytes
255 heads, 63 sectors/track, 1011 cylinders, total 16244736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm-swap_1 doesn't contain a valid partition table

```

But still there is problem on "Disk /dev/mapper/lvm-root doesn't contain a valid partition table"


> LVM tutorials?

Whether you meant;
How To Create LVM Using vgcreate, lvcreate, and lvextend lvm2 Commands
[http://www.thegeekstuff.com/2010/08/how-to-create-lvm/#more-5125](http://www.thegeekstuff.com/2010/08/how-to-create-lvm/#more-5125)

Edit:
I think I have to use "ubuntu-12.04.1-desktop-amd64.iso" NOT "ubuntu-12.04.1-alternate-amd64.iso"  The former would start two options of "Try Ubuntu" and "Install Ubuntu"

---

### Post by darkod on 2012-10-08
fdisk can't always read the LVM properly so don't worry it says there is no valid partition table.

You can use both disks (images), the install procedure is slightly different depending which one you use.

I think the tutorial you linked is much more complicated, especially since the author creates partitions with fdisk which is not always a good idea.

The alternate cd supports LVM by default, you don't need the live dekstop and to install the lvm2 package, it already has it. I guess that is confusing you.

It's up to you what you want to use.

---

### Post by satimis on 2012-10-08
Another problem of unknown cause is;

Root password didn't work after installation.  I have to start "recovery" mode and dropped to root shell to run;

# mount -rw -o remount /
# passwd root

I use the same root password through out all OS under testing for years.

I'm prepared installing Fedora 17 on the same HD making it dual boot.  The bitter lesson which I learned before was after running update on Ubuntu Fedora gone.  I was NOT the first person encountering this problem.  You can find similar thread on Internet.

---

### Post by satimis on 2012-10-08
Another problem surfaces on installing Fedora 17 as dual boot.  There is no spare space.  

see photo attached.

Neither I can resize Ubuntu with the device provided by the installer.

I have to follow the steps on;
Dualboot on lvm with luks
[http://superuser.com/questions/392714/dualboot-on-lvm-with-luks](http://superuser.com/questions/392714/dualboot-on-lvm-with-luks)

Is there an easy way?  Otherwise I prefer going back to physical partitioning without LVM

TIA

B.R.
satimis

---

### Post by darkod on 2012-10-09
You see that Free space in the lvm which is 77GB? Why don't you use that for Fedora?

Once you have LVM and some unused space in it, you can install other distros that support LVM into it. Forget about the physical partitions, that's why you install LVM.

And the root username is not used directly any more in ubuntu, so of course what you tried to do failed. The first user created during the installation has root permissions when you use 'sudo' in front of CLI commands, and 'gksu' in front of GUI commands. It will ask you to enter your user password again, and that will confirm the permissions to execute the command as root.

---

### Post by satimis on 2012-10-09
> **darkod said:**
> You see that Free space in the lvm which is 77GB? Why don't you use that for Fedora?

Yes, I'm aware.  Unfortunately I can't touch it installing Fedora on the fly.  If without lvm I can install Fedora on the fly seamlessly.  The only way to install Fedora is performing the steps of "Dualboot on lvm with luks" in the thread mentioned on my previous posting.

> 
And the root username is not used directly any more in ubuntu, so of course what you tried to do failed. The first user created during the installation has root permissions when you use 'sudo' in front of CLI commands, and 'gksu' in front of GUI commands. It will ask you to enter your user password again, and that will confirm the permissions to execute the command as root.
sudo didn't work complaining "user" NOT on "sudoer".  I have to login root to edit that file.

B.R.
satimis

---

### Post by darkod on 2012-10-09
I don't know Fedora install process, but you should be able to install on existing LVM, that's what it's for. You will probably need to use the manual method, not the automated methods, but it should be possible.

LUKS is encryption which is a whole different topic and has nothing to do with LVM. Encryption shouldn't be a condition just so you can install on LVM. On the other hand, if Fedora by default wants to install encrypted, you have to disable that since the LVM you have is not encrypted.

With ubuntu you can install on existing LVM without problems.

The first user is ALWAYS in sudoer. The users created later are not unless you give them permissions. If the first user doesn't have sudo rights that means something went wrong or there is some corruption.

---

### Post by satimis on 2012-10-09
> **darkod said:**
> I don't know Fedora install process, but you should be able to install on existing LVM, that's what it's for.

No.  Fedora install process is simple and straightforwards.  I did it many times in recent few days installing dualboot Ubuntu and Fedora.

My goal is testing Cloud, OpenStack on Ubuntu and oVirt on Fedora.

> 
You will probably need to use the manual method, not the automated methods, but it should be possible.
Yes I used "Manual" method.  I was NOT allowed to edit it.

Ah, maybe I'll try to delete it later.  In the worst case I reinstall Ubuntu.  But in reinstallation I won't create lvm partitions,

I also tried "Shrink" and "Spare space" methods without a breakthrough.

> 
The first user is ALWAYS in sudoer. The users created later are not unless you give them permissions. If the first user doesn't have sudo rights that means something went wrong or there is some corruption.
I have only one "user" which is also the "first user".  Sudo failed to work.  It is a little bid strange to me.

---

### Post by satimis on 2012-10-09
Hi darkod,

I got Fedora 17 installed.  I can't edit nor delete the FREE space.  It belongs to the lvm group on Ubuntu.  I was allowed to create lvm partition on it to install Fedora

Pls see Screenshot-01 attached.

However another problem comes, Ubuntu gone on reboot.  On GRUB window at boot only Fedora is there.  However Ubuntu is still in the HD

Pls see Screenshot-02 attached.

(remark: I use the names lv00 and lv01 automatically assigned without changing them)

Pls advise how to get Ubuntu back to GRUB.  It is on Ubuntu lvm partition.

TIA

satimis

---

### Post by darkod on 2012-10-09
Well, that's what I was talking about all the time. Once you have LVM, you use it and create new Logical Volumes for the new distro you want to install.
You don't try to modify it in any other way, it won't allow you that (except completely deleting it).

You shouldn't have installed the fedora bootloader. I don't know how it works and is it grub1 or grub2.

You can get grub2 from ubuntu back to the MBR by booting into live mode, installing the lvm2 package, activating the LVM and doing the grub2 reinstall procedure. That would be something like:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/mapper/lvm-root /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

After booting ubuntu once, do:
sudo update-grub

to detect Fedora and add it to the boot menu.

You should already know how to reinstall the bootloader. It sounds to me like you are running through things instead of learning them. There is no point following blindly the commands we give you here.

---

### Post by satimis on 2012-10-09
> **darkod said:**
>  - snip -
You shouldn't have installed the fedora bootloader.

Durintg installation I was asked whether to install fedora bootloader.  My concept was without its installation I can't boot fedora.

> 
I don't know how it works and is it grub1 or grub2.

I think it would be grub2

On Fedora:
$ ls /boot/```

config-3.3.4-5.fc17.x86_64  grub                               memtest86+-4.20
efi                         grub2                              System.map-3.3.4-5.fc17.x86_64
elf-memtest86+-4.20         initramfs-3.3.4-5.fc17.x86_64.img  vmlinuz-3.3.4-5.fc17.x86_64
```

$ ls /boot/grub```

splash.xpm.gz

```

$ ls /boot/grub2/```

device.map  fonts  grub.cfg  grubenv  i386-pc  locale  themes

```

> 
You can get grub2 from ubuntu back to the MBR by booting into live mode,...
- snip -

I can't start Ubuntu.  But I can mount it on Fedora

Edit-1:
======
Whether run Ubuntu CD to do the job?


Edit-2:
======
Ubuntu came back while I fixed the sound problem on Fedora performing:-

$ sudo gedit /etc/default/grub

adding "radeon.audio=1" on the line "GRUB_CMDLINE_LINUX= ...."

$ sudo grub2-mkconfig -o /boot/grub2/grub.cfg

reboot Fedora

Ubuntu appears on GRUB window

Following error on text scrolling on booting Ubuntu;
udevd[318] inotify-old-watch (6, /dev/dm-310) failed: Invalid argument
udevd[328] inotify-old-watch ........

What are those errors?

satimis

---

