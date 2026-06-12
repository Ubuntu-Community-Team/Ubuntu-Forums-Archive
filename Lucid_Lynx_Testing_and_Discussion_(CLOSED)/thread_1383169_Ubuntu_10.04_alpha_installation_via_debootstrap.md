---
title: "Ubuntu 10.04 alpha installation via debootstrap"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by absolutezero1287 on 2010-01-16
I was wondering if its possible. I'd like to do a very minimal ubuntu install of 10.04 alpha2 using debootstrap. I'd rather not use the Alternative Install CD.

My reasoning for using debootstrap is that I don't use many of the applications that come in a regular Ubuntu install and I like tweaking everything from the ground up.

---

### Post by absolutezero1287 on 2010-01-22
Bump. Seriously? Five days and not a single reply? 

Does anyone know how I can install the development branch of Ubuntu 10.04 via debootstrap?

---

### Post by Sef on 2010-01-22
Moved to Lucid Testing & Development.

---

### Post by xebian on 2010-01-22
> **absolutezero1287 said:**
> I was wondering if its possible. I'd like to do a very minimal ubuntu install of 10.04 alpha2 using debootstrap. I'd rather not use the Alternative Install CD.

My reasoning for using debootstrap is that I don't use many of the applications that come in a regular Ubuntu install and I like tweaking everything from the ground up.

How about
```

man debootstrap

```

---

### Post by VMC on 2010-01-22
> **absolutezero1287 said:**
> Bump. Seriously? Five days and not a single reply? 

Does anyone know how I can install the development branch of Ubuntu 10.04 via debootstrap?

I've never heard of "debootstrap" before. [Distrowatch]("http://distrowatch.com/weekly.php?issue=20081215#feature") had an article on a lean ubuntu install from the base system. If that's any help.

---

### Post by ranch hand on 2010-01-22
I do not think that an app made to convert other OS' into Debian is the best way to install 10.04.

Why not get the server edition and build up from there?

---

### Post by absolutezero1287 on 2010-01-22
> **xebian said:**
> How about
```

man debootstrap

```

I know how to use debootstrap. I've used it before. I was simply asking if it can be used to install Ubuntu 10.04. I've used it to install stable releases but never an alpha.

---

### Post by absolutezero1287 on 2010-01-22
> **ranch hand said:**
> I do not think that an app made to convert other OS' into Debian is the best way to install 10.04.

Why not get the server edition and build up from there?

Debootstrap does not "convert other OS'" into Debian. It basically sets up a very basic skeleton that you can use to make a highly customized Debian or Ubuntu build. 

The server edition has things that I, a desktop user, don't need. I have often found that removing unneeded packages makes Ubuntu very unstable. This is why I prefer building up as opposed to trimming an Ubuntu install.

---

### Post by VMC on 2010-01-23
If you've done it before then why not use it to build up Lucid?
Have you written a dowto on the subject or where do I find more into? Did you follow this [Ubuntu Guide on debootstrap]("https://wiki.ubuntu.com/DebootstrapChroot") ?

I'm very interested in how this works. I always hate to have to always update every single nVidia, ATI and whoever/whatever driver card among other useless stuff I will never use for my system.
Can debootstrap stop this? I know about pinning but that won't work.

I'm looking for something like Windows's nlite utility.

---

### Post by absolutezero1287 on 2010-01-23
> **VMC said:**
> If you've done it before then why not use it to build up Lucid?
Have you written a dowto on the subject or where do I find more into? Did you follow this [Ubuntu Guide on debootstrap]("https://wiki.ubuntu.com/DebootstrapChroot") ?

I'm very interested in how this works. I always hate to have to always update every single nVidia, ATI and whoever/whatever driver card among other useless stuff I will never use for my system.
Can debootstrap stop this? I know about pinning but that won't work.

I'm looking for something like Windows's nlite utility.


The wiki has a pretty detailed how-to on the subject but if you're looking for something easy like nlite then debootstrap is not for you. Its all commandline based. However, if you're willing to take the time to learn how to use it it would be well worth it.

---

### Post by k64 on 2010-01-23
Debootstrap is a package management utility for installing one Linux distribution from another. Even though it is designed to allow you to switch Linux distributions painlessly without wiping your hard drive AGAIN, it has its limitations. 

First of all, if you want to make the most of the Ext4 file system, good luck. You have to wipe your hard drive, because Ext4 is only the default on a small number of Linux distros. You can use tunefs, but it does not actually tune the FS fully. You have to format.

Secondly, if you're switching from an RPM-based distro, you are going to need to use Alien, which is a pain to install (you have to build it from source in RPM-based distros).

---

### Post by VMC on 2010-01-23
> **absolutezero1287 said:**
> The wiki has a pretty detailed how-to on the subject but if you're looking for something easy like nlite then debootstrap is not for you. Its all commandline based. However, if you're willing to take the time to learn how to use it it would be well worth it.

Thanks, but what I should have said, by "nLite",  was its outcome, not is gui interface. In fact that's a closed system, you have no way of knowing how its done.

 I prefer to have total control.  I use CLI commands on a lot of the work I do.

---

### Post by absolutezero1287 on 2010-01-23
> **k64 said:**
> Debootstrap is a package management utility for installing one Linux distribution from another. Even though it is designed to allow you to switch Linux distributions painlessly without wiping your hard drive AGAIN, it has its limitations. 

First of all, if you want to make the most of the Ext4 file system, good luck. You have to wipe your hard drive, because Ext4 is only the default on a small number of Linux distros. You can use tunefs, but it does not actually tune the FS fully. You have to format.

Secondly, if you're switching from an RPM-based distro, you are going to need to use Alien, which is a pain to install (you have to build it from source in RPM-based distros).

Actually, I'm on Ubuntu 9.04. I'm installing Lucid in a chroot. I followed a Debian [how-to article]("http://www.debian-administration.org/articles/426"). These are the steps I've taken so far:

1- Make a new ext4 partition
2- mount it under /mnt/Ubuntu_10.04
3- cd /mnt/Ubuntu_10.04 && debootstrap --arch=i386 lucid .
4- mount proc proc/  -t proc 
5- cp /etc/resolv.conf etc/resolv.conf
6- cp /etc/hosts etc/hosts
7- cp /etc/network/interfaces etc/network/interfaces
**keep in mind that my working directory is /mnt/Ubuntu_10.04**

All that's left to do is install the kernel and fix the sources.list file

---

### Post by absolutezero1287 on 2010-01-23
Here's the sources.list file. I ran an apt-get update and everything seems to be going smoothly.

Now installing the Linux kernel...

apt-get install linux-image-generic

```

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

#backports
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

#partner repos
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted

deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe

deb http://security.ubuntu.com/ubuntu lucid-security multiverse

deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by absolutezero1287 on 2010-01-23
The only issue I seem to be having is setting up the locales. I tried dpkg-reconfigure localeconf but I get an error message:
[CODE
]root@satori:/# dpkg-reconfigure localeconf
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Package `localeconf' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localeconf is not installed
[/CODE]

I then try to install it but the package doesn't seem to exist. Is there an alternative way to configure my locales?

```

root@satori:/# apt-cache search localeconf
root@satori:/# apt-get install localeconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package localeconf

```

I read [here]("http://ubuntuforums.org/showthread.php?t=1375356") that it has something to do with glibc and that the latest update fixes the issue. I ran an apt-get update and apt-get upgrade and it seems as though all my packages are up to date. I really don't know what the issue with the locales is.

---

### Post by absolutezero1287 on 2010-01-23
Alright, resolved the issue. I made a really stupid mistake because I didn't have the language packs installed.

After running the apt-get install language-pack-en-base and dpkg-reconfigure locales the locales seem to be working just fine. I also manually turned off apt's function to automatically install recommended packages.

touch /etc/apt/apt.conf.d/02no-recommends
and in that file I put the following line:
APT::Install-Recommends "false";

---

### Post by absolutezero1287 on 2010-01-23
Update:

Tried to boot into Lucid and got a kernel panic. I don't know what the issue could be. At first I thought that I may have done something wrong in grub's menu.lst or the fstab but after inspecting the two I still can't determine the source of the kernel panic. Below is the output of blkid, Lucid's fstab, and the menu.lst entry. Hope it helps.

```

Output of blkid

/dev/sda1: UUID="1249c9fe-420d-42fa-af59-08e203ff0cac" TYPE="ext3" 
/dev/sda2: UUID="bcb5d1d8-3589-42a1-bca2-16186d38b561" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda3: TYPE="swap" UUID="2a47f445-acca-4362-8a8b-969533f75d30" 
/dev/sda4: UUID="5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf" TYPE="ext4" 

sda1 = Jaunty /
sda2 = Jaunty /home
sda3 = swap
sda4 = Lucid /

Lucid fstab

# <filesystem> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID="5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf" / ext4 relatime,errors=remount-ro 0       1
#
# swap is on /dev/sda3
UUID="2a47f445-acca-4362-8a8b-969533f75d30" none            swap    sw              0       0
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#USER ADDED
# Jaunty root
UUID=1249c9fe-420d-42fa-af59-08e203ff0cac /mnt/Ubuntu_9.04/root ext3 relatime,errors=remount-ro 0  1
# Juanty home
UUID=bcb5d1d8-3589-42a1-bca2-16186d38b561 /mnt/Ubuntu_9.04/home ext3 relatime  0  2

Menu.lst entry for lucid
title           Ubuntu 10.04 (testing)
uuid            5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf
kernel          /boot/vmlinuz-2.6.32-11-generic root=5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf
initrd          /boot/initrd.img-2.6.32-11-generic

```

Here's the error I got. Odd thing is that these aren't written to Lucid's /var/log/dmesg. Its empty.
```

Begin: Mounting root file system... ...
/init: line 219: syntax error: 0x5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf
Kernel panic - not syncing: Attempted to kill init!
Pid: 1, comm: init Not tainted 2.6.32-11-generic #15-Ubuntu
Call trace:
?printk+0x1d/0x21
panic+0x48/0xf3

```

I didn't copy the entire error message but the rest was part of the call trace. The only things I can gather is that the kernel panic happened while the root file system was being mounted and that init did something strange.

EDIT: Remember that the system was built in a chroot. I created another partition, mounted it, chroot'd into it and used debootstrap. Could something have gone wrong when I installed the kernel in the chroot? As one user pointed out: "whatever figured out the root filesystem device to put in the initrd went wrong when trying to do it in the chroot"

If this is the case then it should simply be a matter of rebuilding the initrd. The problem with that is that the Lucid build is only accessible from the chroot. So rebuilding the initrd in a chroot would just recreate the same issue. Please help. I'm really stuck.

---

### Post by ranch hand on 2010-01-23
The number in your error looks, to me, like a uuid.  It does not match anything on the blkid output.

You may want to check that.

---

### Post by absolutezero1287 on 2010-01-23
> **ranch hand said:**
> The number in your error looks, to me, like a uuid.  It does not match anything on the blkid output.

You may want to check that.

I did. I checked the fstab and grub's menu.lst file. That's why I posted them to my prior message. Something is happening that's causing the UUID to appear incorrectly and I have no clue what it is.

UUID of /dev/sda4: 
5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf

Number in the error:
0x5fc167c6-3fb7-4ac8-91d4-0ceaf047dddf

See? Take out the 0x and its the same number.

---

### Post by VMC on 2010-01-23
I wonder if something is missed up with your initrd image.

Do you haven an older kernel and initrd pair to try?

---

### Post by absolutezero1287 on 2010-01-23
> **VMC said:**
> I wonder if something is missed up with your initrd image.

Do you haven an older kernel and initrd pair to try?

Nope. I just used the latest kernel image. I could rebuild the initrd but I wouldn't know where to start. I remember doing it on arch linux but never on Ubuntu. I guess since the initrd was built automatically it must have done something weird while in the chroot.

---

### Post by VMC on 2010-01-24
> **absolutezero1287 said:**
> Nope. I just used the latest kernel image. I could rebuild the initrd but I wouldn't know where to start. I remember doing it on arch linux but never on Ubuntu. I guess since the initrd was built automatically it must have done something weird while in the chroot.

From this [link]("http://gamblis.com/2009/10/01/how-to-fix-the-initial-ramdisk-initrd-in-ubuntu-and-debian/"):

"Unfortunately, you will often realize that you need to rebuild your initrd after it is too late, as you witness a **kernel panic** during the root file system mount stage of boot. When that occurs, boot into rescue mode and run mkinitrd after chrooting to the proper hard disk partition."

command:
```
sudo mkinitrd -o /boot/initrd.img-`uname –r` `uname –r`
```

---

### Post by absolutezero1287 on 2010-01-24
> **VMC said:**
> From this [link]("http://gamblis.com/2009/10/01/how-to-fix-the-initial-ramdisk-initrd-in-ubuntu-and-debian/"):

"Unfortunately, you will often realize that you need to rebuild your initrd after it is too late, as you witness a **kernel panic** during the root file system mount stage of boot. When that occurs, boot into rescue mode and run mkinitrd after chrooting to the proper hard disk partition."

command:
```
sudo mkinitrd -o /boot/initrd.img-`uname –r` `uname –r`
```

It seems that I don't have mkinitrd. However, I have a program called mkinitramfs-kpkg and mkinitramfs. Am I wrong to assume that they're the same thing?

---

### Post by ranch hand on 2010-01-24
I just took a look in synaptic for mkinitramfs-kpkg and mkinitramfs and do not come up with anything there is a bootcd-mkinitramfs.

I believe that mkinitrd is a set bash command that ought to work.  --rebuild-initrd is a built in switch.

---

### Post by VMC on 2010-01-24
> **absolutezero1287 said:**
> It seems that I don't have mkinitrd. However, I have a program called mkinitramfs-kpkg and mkinitramfs. Am I wrong to assume that they're the same thing?
I forgot your using KDE. I found this:

vmc@ubuntu:~$ aptitude search mkinitramfs
p   bootcd-mkinitramfs                                     - initramfs extension for bootcd                                  

So it appears you can or should use "bootcd-mkinitramfs".

---

### Post by absolutezero1287 on 2010-01-24
> **ranch hand said:**
> I just took a look in synaptic for mkinitramfs-kpkg and mkinitramfs and do not come up with anything there is a bootcd-mkinitramfs.

I believe that mkinitrd is a set bash command that ought to work.  --rebuild-initrd is a built in switch.

If it was a bash command then the autocompletion would have caught it. Here's all programs I have that start with "mki-"

```

root@satori:/# mk
mkdir             mkfontdir         mkfs.bfs          mkfs.ext3         mkfs.minix        mkinitramfs-kpkg  mknod
mke2fs            mkfontscale       mkfs.cramfs       mkfs.ext4         mkhomedir_helper  mklost+found      mkswap
mkfifo            mkfs              mkfs.ext2         mkfs.ext4dev      mkinitramfs       mk_modmap         mktemp

```

@VMC: Actually, Jaunty is just cli right now. I haven't added a DE. Either way, the DE has nothing to do with a program that's commandline based. Here's what I found upon searching for "initramfs."

```

root@satori:/# apt-cache search initramfs
bootchart - boot sequence auditing
busybox-initramfs - Standalone shell setup for initramfs
cryptsetup - configures encrypted block devices
initramfs-tools - tools for generating an initramfs
initramfs-tools-bin - binaries used by initramfs-tools
klibc-utils - small utilities built with klibc for early boot
libklibc - minimal libc subset for use with initramfs
bootcd-mkinitramfs - initramfs extension for bootcd
classmate-initramfs - classmate specific initramfs settings
debirf - build a kernel and initrd to run Debian from RAM
febootstrap - tool for bootstrapping a Fedora system (like Debian debootstrap)
fsprotect - Helper scripts to make filesystems immutable
live-initramfs - Debian Live initramfs hook
mksh - enhanced version of the Korn shell
uswsusp - tools to use userspace software suspend provided by Linux
yaird - Yet Another mkInitRD


```

---

### Post by ranch hand on 2010-01-24
Jaunty?

---

### Post by nanog on 2010-01-24
initramfs-tools  is what you need.

useful commands: 

mkinitramfs

update-initramfs

---

### Post by absolutezero1287 on 2010-01-24
> **ranch hand said:**
> Jaunty?
My mistake, I meant to say Lucid.

> **nanog said:**
> initramfs-tools  is what you need.

useful commands: 

mkinitramfs

update-initramfs

Well I have the initramfs-tools package installed so I guess I have everything I need. I just need some guidance on building a new initrd.

---

### Post by ranch hand on 2010-01-24
"update-initramfs" looks like a good thing to try to me.

---

### Post by absolutezero1287 on 2010-01-25
Update: Can't boot into Lucid via single user mode. I still get the same kernel panic. I tried changing from using the UUID in menu.lst to using the old method (root y,x). In the end I got the same exact kernel panic message.

---

### Post by VMC on 2010-01-25
> **absolutezero1287 said:**
> Update: Can't boot into Lucid via single user mode. I still get the same kernel panic. I tried changing from using the UUID in menu.lst to using the old method (root y,x). In the end I got the same exact kernel panic message.

Were you able to rebuild your *initramfs*? If so what were the commands you used.

---

### Post by absolutezero1287 on 2010-01-25
> **VMC said:**
> Were you able to rebuild your *initramfs*? If so what were the commands you used.

I couldn't boot into Lucid at all. If I rebuild the initramfs it would have to be via the chroot.

---

