---
title: "GRUB &gt;= 2.00 has been unpacked but not yet configured."
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by mc@2 on 2015-01-04
I've upgraded my htpc box several times but only recently i found out im still on the generic 12.04 kernel
```
root@htpc:/# uname -a
Linux htpc 3.2.0-63-generic-pae #95-Ubuntu SMP Thu May 15 23:26:11 UTC 2014 i686 i686 i686 GNU/Linux

```
Yet the new 14.04 kernel is there
```
root@htpc:/# ls /boot
abi-3.13.0-43-generic     config-3.2.0-63-generic-pae   initrd.img-3.13.0-43-generic-pae  memtest86+.elf                System.map-3.2.0-63-generic-pae
abi-3.2.0-63-generic-pae  grub                          initrd.img-3.2.0-63-generic-pae   memtest86+_multiboot.bin      vmlinuz-3.13.0-43-generic
config-3.13.0-43-generic  initrd.img-3.13.0-43-generic  memtest86+.bin                    System.map-3.13.0-43-generic  vmlinuz-3.2.0-63-generic-pae

```
So i tried to update grub
```
root@htpc:/# update-grub
GRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.

```
I then tried the usual: apt-get -f install, reinstallation and removal of grub-pc, but still the error. grub-install works fine
```
root@htpc:/home/bart# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.

```
Any ideas where to go from here?
```
root@htpc:/# apt-cache policy grub-pc
grub-pc:
  Installed: 2.02~beta2-9ubuntu1
  Candidate: 2.02~beta2-9ubuntu1
  Version table:
 *** 2.02~beta2-9ubuntu1 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.02~beta2-9 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```

---

### Post by Bashing-om on 2015-01-04
mc@2; Oh so interesting .

So, more than 1 /boot directory at play here - recently got bit by this - ?
```

cat /etc/fstab
mount
cat /etc/mtab
sudo blkid

```

and what is the system set up to boot ?
```

ls -al /vmlinuz*
ls -al /boot
ls -al /usr/src
ls -la /lib/modules

```
And the contents of all the directories agree ?
before we go trying to decypher /boot/grub/grub.cfg 

[INDENT][INDENT]all in the process
[INDENT][INDENT][INDENT]let's look and see
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc@2 on 2015-01-04
Thanks for the swift reply! Interesting you say... :)

It seems everything is there and working ok, except for grub (well ok, and my nvidia ion drivers). Google hasn't brought up anything, only some people with similar issues. Although debian bug #717177 suggested an issue with files in /etc/grub.d/

Ok, here we go
```
root@htpc:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=348572a4-0c07-4e36-8d1a-efde295fbcbe /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d017d4f4-ad6d-4a11-a074-cbe79a9d420e /home           ext4    defaults        0       2
# /usr was on /dev/sda5 during installation
UUID=bfc99b50-a615-4ca5-803f-e5fc9712b23e /usr            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6669b8e9-b00d-4172-a7e5-3b4bd8d045d8 none            swap    sw              0       0

``````

root@htpc:/# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda5 on /usr type ext4 (rw)
/dev/sda7 on /home type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xbmc)

``````

root@htpc:/# cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
/dev/sda5 /usr ext4 rw 0 0
/dev/sda7 /home ext4 rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1001/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=xbmc 0 0

``````

root@htpc:/# blkid
/dev/sda1: UUID="348572a4-0c07-4e36-8d1a-efde295fbcbe" TYPE="ext4" 
/dev/sda5: UUID="bfc99b50-a615-4ca5-803f-e5fc9712b23e" TYPE="ext4" 
/dev/sda6: UUID="6669b8e9-b00d-4172-a7e5-3b4bd8d045d8" TYPE="swap" 
/dev/sda7: UUID="d017d4f4-ad6d-4a11-a074-cbe79a9d420e" TYPE="ext4" 
/dev/sr0: LABEL="DVD" TYPE="udf"

``````

root@htpc:/# ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Jan  3 20:20 /vmlinuz -> boot/vmlinuz-3.13.0-43-generic

``````

root@htpc:/# ls -al /boot
total 53028
drwxr-xr-x  3 root root     4096 Jan  4 20:08 .
drwxr-xr-x 22 root root     4096 Jan  3 20:25 ..
-rw-r--r--  1 root root  1168937 Dec  8 21:38 abi-3.13.0-43-generic
-rw-r--r--  1 root root   805098 May 16  2014 abi-3.2.0-63-generic-pae
-rw-r--r--  1 root root   169815 Dec  8 21:38 config-3.13.0-43-generic
-rw-r--r--  1 root root   147587 May 16  2014 config-3.2.0-63-generic-pae
drwxr-xr-x  5 root root    12288 Jan  4 20:40 grub
-rw-r--r--  1 root root 18768196 Jan  4 19:41 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root  2688520 Jan  4 20:08 initrd.img-3.13.0-43-generic-pae
-rw-r--r--  1 root root 14073240 Jan  4 19:36 initrd.img-3.2.0-63-generic-pae
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2699011 Dec  8 21:38 System.map-3.13.0-43-generic
-rw-------  1 root root  2322710 May 16  2014 System.map-3.2.0-63-generic-pae
-rw-------  1 root root  5833296 Dec  8 21:38 vmlinuz-3.13.0-43-generic
-rw-------  1 root root  5034176 May 16  2014 vmlinuz-3.2.0-63-generic-pae

``````

root@htpc:/# ls -al /usr/src
total 76
drwxr-xr-x 19 root root 4096 Jan  4 19:35 .
drwxr-xr-x 11 root root 4096 Jan  4 19:34 ..
drwxr-xr-x  2 root root 4096 Jan  4 19:35 bbswitch-0.7
drw-r-xr-x  2 root root 4096 Jul 27  2013 dvbhdhomerun-0.0.16~precise
drwxr-xr-x 24 root root 4096 May 29  2014 linux-headers-3.13.0-27
drwxr-xr-x  7 root root 4096 May 29  2014 linux-headers-3.13.0-27-generic
drwxr-xr-x 24 root root 4096 Jul 10 01:25 linux-headers-3.13.0-30
drwxr-xr-x  7 root root 4096 Jul 10 01:26 linux-headers-3.13.0-30-generic
drwxr-xr-x 24 root root 4096 Aug 14 23:13 linux-headers-3.13.0-34
drwxr-xr-x  7 root root 4096 Aug 14 23:13 linux-headers-3.13.0-34-generic
drwxr-xr-x 24 root root 4096 Sep 21 23:41 linux-headers-3.13.0-35
drwxr-xr-x  7 root root 4096 Sep 21 23:41 linux-headers-3.13.0-35-generic
drwxr-xr-x 24 root root 4096 Sep 29 22:46 linux-headers-3.13.0-36
drwxr-xr-x  7 root root 4096 Sep 29 22:46 linux-headers-3.13.0-36-generic
drwxr-xr-x 24 root root 4096 Jan  3 20:20 linux-headers-3.13.0-43
drwxr-xr-x  7 root root 4096 Jan  3 20:20 linux-headers-3.13.0-43-generic
drwxr-xr-x  4 root root 4096 Jan  3 23:47 linux-source-3.13.0
lrwxrwxrwx  1 root root   47 Dec  8 21:35 linux-source-3.13.0.tar.bz2 -> linux-source-3.13.0/linux-source-3.13.0.tar.bz2
drwxr-xr-x  3 root root 4096 Jan  4 19:35 nvidia-340-340.65
drwxr-xr-x  3 root root 4096 Jan  4 19:35 nvidia-340-uvm-340.65

``````

root@htpc:/# ls -al /lib/modules
total 36
drwxr-xr-x  9 root root 4096 Jan  3 20:19 .
drwxr-xr-x 24 root root 4096 Jan  4 19:35 ..
drwxr-xr-x  2 root root 4096 Jul 10 01:38 3.13.0-27-generic
drwxr-xr-x  2 root root 4096 Aug 14 23:35 3.13.0-30-generic
drwxr-xr-x  2 root root 4096 Sep 22 00:01 3.13.0-34-generic
drwxr-xr-x  2 root root 4096 Sep 29 22:54 3.13.0-35-generic
drwxr-xr-x  2 root root 4096 Jan  3 20:25 3.13.0-36-generic
drwxr-xr-x  6 root root 4096 Jan  4 19:41 3.13.0-43-generic
drwxr-xr-x  5 root root 4096 Jan  3 23:40 3.2.0-63-generic-pae

``````

root@htpc:/# ls -al
total 100
drwxr-xr-x  22 root root  4096 Jan  3 20:25 .
drwxr-xr-x  22 root root  4096 Jan  3 20:25 ..
drwxr-xr-x   2 root root  4096 Jan  3 20:11 bin
drwxr-xr-x   3 root root  4096 Jan  4 20:08 boot
drwxr-xr-x   2 root root  4096 Dec  9  2012 cdrom
drwxr-xr-x  14 root root  4240 Jan  4 20:48 dev
drwxr-xr-x 148 root root 12288 Jan  4 20:49 etc
drwxr-xr-x   5 root root  4096 Apr 19  2012 home
lrwxrwxrwx   1 root root    33 Jan  3 20:20 initrd.img -> boot/initrd.img-3.13.0-43-generic
drwxr-xr-x  24 root root  4096 Jan  4 19:35 lib
drwx------   2 root root 16384 Dec  9  2012 lost+found
drwxr-xr-x   3 root root  4096 Jan  3 19:53 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   2 root root  4096 Aug 18  2012 opt
dr-xr-xr-x 140 root root     0 Jan  4 20:48 proc
drwx------   6 root root  4096 Jan  3 22:15 root
drwxr-xr-x  25 root root   920 Jan  4 20:50 run
drwxr-xr-x   2 root root 12288 Jan  4 19:35 sbin
drwxr-xr-x   2 root root  4096 Aug 18  2012 srv
drwxr-xr-x  13 root root     0 Jan  4 20:48 sys
drwxrwxrwt   5 root root  4096 Jan  4 21:17 tmp
drwxr-xr-x  11 root root  4096 Jan  4 19:34 usr
drwxr-xr-x  14 root root  4096 May 29  2014 var
lrwxrwxrwx   1 root root    30 Jan  3 20:20 vmlinuz -> boot/vmlinuz-3.13.0-43-generic 
```

---

### Post by Bashing-om on 2015-01-04
mc@2; Humm ..

Someone been 'rm'n where they should have been dpkg'n ? as what is in /usr/src and /lib/modules does not agree with /boot.

Let's make sure we have operating head room:
```

df -h
df -i

```
and take a gentle poke at the situation with the package manager :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```
then consider means to take matters into our own hands .

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT][INDENT]nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc@2 on 2015-01-04
Hmm, i can't remember deleting any libs or modules by hand. I normally rely on apt-get.

Anyway, apt-get update/upgrade/-f install i've tried before and don't do anything. Also dpkg -C doesn't fix anything. Furthermore sufficient space left i think:
```
root@htpc:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.2G  1.3G  7.5G  15% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            873M  8.0K  873M   1% /dev
tmpfs           176M  1.2M  175M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            880M   68K  880M   1% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda5        14G  4.0G  9.2G  31% /usr
/dev/sda7       734G  656G   42G  95% /home

```
```
root@htpc:/# df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        610800  25657   585143    5% /
none             220177      2   220175    1% /sys/fs/cgroup
udev             216555    504   216051    1% /dev
tmpfs            220177    537   219640    1% /run
none             220177      3   220174    1% /run/lock
none             220177      2   220175    1% /run/shm
none             220177     10   220167    1% /run/user
/dev/sda5        915712 304319   611393   34% /usr
/dev/sda7      48832512  35705 48796807    1% /home

```

---

### Post by Bashing-om on 2015-01-04
mc@2; Welp;

You are short on space in /home - but, that is not a contributor to the present problem.

EDIT: Afterthought:
What release does the system think is installed ? As "assuming" can get us into deep trouble !
```

lsb_release-a
cat /etc/issue

```
IF it is indeed 14.04 - trusty, we can proceed.

Let's get manual with this and try and fix the kernel relationships.

Have not figured out what we are going to do yet with the missing vmlinuz.old and initrd.img.old links in '/'. But we will get to that in due time.

For now:
```

sudo rm -rf /usr/src/linux-headers-3.13.0-{27,30,34,35,36}-generic
sudo rm -rf /usr/src/linux-headers-3.13.0-{27,30,34,35,36}
sudo rm -rf /lib/modules/3.13.0-{27,30,34,35,36}*

```

Next; Try and repair the broken package system.
```

sudo apt-get -f install

```

Finally properly uninstall the kernels and headers whose files we have already deleted.
```

sudo apt-get purge linux-{headers,image}-3.13.0-{27,30,34,35,36}.*

```

There is this to consider deeply " linux-source-3.13.0.tar.bz2 -> linux-source-3.13.0/linux-source-3.13.0.tar.bz2 " Have you attempted to install the latest kernel from source ?

In any event, If the above goes well, we try and install a backup kernel, and see what we can do about (RE-)installing the 3.13.0-43-generic kernel properly .

[INDENT][INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT][/INDENT]

---

### Post by mc@2 on 2015-01-05
ok, i'm back again. First things first:
```
root@htpc:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty
root@htpc:/# cat /etc/issue
Ubuntu 14.04.1 LTS \n \l

```

I've deleted all headers and modules and ran apt-get, but doesn't seem to do anything
```
root@htpc:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Apt-purge also ran fine and deleted al the kernel packages. I tried another apt-get -f install, but nothing happened. Also update-grub gives the same error.

---

### Post by mc@2 on 2015-01-05
I started digging around a bit in /usr/sbin/grub-mkconfig and found:
```
if fgrep -qs '${GRUB_PREFIX}/video.lst' "${grub_mkconfig_dir}/00_header"; then
  echo "GRUB >= 2.00 has been unpacked but not yet configured." >&2
  echo "grub-mkconfig will not work until the upgrade is complete." >&2
  echo "It should run later as part of configuring the new GRUB packages." >&2
  exit 0
fi
```
but GRUB_PREFIX is nowhere defined??? Is this file delivered like that in the distribution? If so, it looks like a pretty silly bug. Anyway, I've added
```
GRUB_PREFIX="/boot/grub/i386-pc"
export GRUB_PREFIX

```
Then update-grub threw other nasty stuff at me
```
root@htpc:/# update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.

```
The warning was simply fixed by putting a comment before GRUB_HIDDEN_TIMEOUT in /etc/default/grub. But what the f... is the grub-probe error? I'll dig on.

---

### Post by Bashing-om on 2015-01-05
mc@2; OK,

let's take another step forward, install a backup kernel:
```

sudo apt-get update
sudo apt-get install linux-image-3.13.0-40-generic linux-headers-3.13.0-40-generic linux-headers-3.13.0-40

```
reboot and see if you can choose the new kernel to boot from grub's boot menu .

IF so, then we (RE-)install the -43 kernel.
Then finally, if the 3.13 kernels boot up fine , remove that obsolete 3.2 kernel .

[INDENT][INDENT]that's what I think
[/INDENT][/INDENT]

---

### Post by mc@2 on 2015-01-05
I can only add a new kernel to my startup, if i can run update-grub. As long as update-grub isn't working, i won't get new entries in my grub startup. The apt-get script for the kernels will call update-grub but that wasn't working.

Anyway, i've fixed it. I suspected and error in /etc/grub.d/00_header so i moved this to 00_header.old and copied 00_header.dpkg-dist to 00_header. For some odd reason grub was still scrubbing 00_header.old giving the funny error. Deleting this .old file fixed it.

So in a nutshell:
- /usr/sbin/grub-mkconfig has a bug as it doesn't have the GRUB_PREFIX variable defined
- /etc/grub.d/00_header was most likely bugged (by me?) and replacing it with the default file fixed that too

the final results:
```
root@htpc:/# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-63-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

Although the kernel versions were a bit of a mess, it had nothing to do with the update-grub error. I will try to fix these kernels though.

---

### Post by Bashing-om on 2015-01-05
mc@2; Well; Just great, Who else would have thunk it .

Glad ya got it fingered out .. 

If it is a bug, ya might consider opening up a bug report and have the developers take a look at it .

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by mc@2 on 2015-01-06
A final note, seems somewhere in my dist-upgrade history things have gone wrong. Purging grub-common (and manually removing /boot/grub) following by an install of grub-pc did the trick.

---

