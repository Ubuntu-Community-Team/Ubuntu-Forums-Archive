---
title: "Errors during autoremove"
date: 2020-07-06
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2020-07-06
For 2 years I've been using v18.04.  Trying to makeupgrades I was suggested by the system to:
```
sudo apt autoremove
```
> The following packages will be REMOVED:
  linux-headers-4.15.0-106 linux-headers-4.15.0-106-generic linux-image-4.15.0-106-generic
  linux-modules-4.15.0-106-generic linux-modules-extra-4.15.0-106-generic
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 333 MB disk space will be freed.
> Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-109-generic
Found initrd image: /boot/initrd.img-4.15.0-109-generic
Found linux image: /boot/vmlinuz-4.15.0-108-generic
Found initrd image: /boot/initrd.img-4.15.0-108-generic
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found Ubuntu 16.04.4 LTS (16.04) on /dev/sdc2
Found Ubuntu 18.04.4 LTS (18.04) on /dev/sdd1
Adding boot menu entry for EFI firmware configuration
done
Removing linux-headers-4.15.0-106-generic (4.15.0-106.107) ...
Removing linux-headers-4.15.0-106 (4.15.0-106.107) ...
Removing linux-modules-4.15.0-106-generic (4.15.0-106.107) ...
Setting up initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-4.15.0-109-generic (4.15.0-109.110) ...
Setting up linux-image-4.15.0-108-generic (4.15.0-108.109) ...
Setting up linux-image-4.15.0-91-generic (4.15.0-91.92) ...
Setting up linux-firmware (1.173.18) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-109-generic
[COLOR="#FF0000"]Fatal: open /boot/vmlinuz-4.15.0-76-generic: No such file or directory[/COLOR]
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
[COLOR="#FF0000"]dpkg: error processing package linux-firmware (--configure):[/COLOR]
 installed linux-firmware package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.
......  the list continues ....

```
uname -r
```
> 4.15.0-108-generic

```
dpkg --list 'linux-image*'
```
> rc  linux-image-4.15.0-10 4.15.0-101.102  amd64           Signed kernel image generic
rc  linux-image-4.15.0-10 4.15.0-106.107  amd64           Signed kernel image generic
iF  linux-image-4.15.0-10 4.15.0-108.109  amd64           Signed kernel image generic
iF  linux-image-4.15.0-10 4.15.0-109.110  amd64           Signed kernel image generic
rc  linux-image-4.15.0-20 4.15.0-20.21    amd64           Signed kernel image generic
rc  linux-image-4.15.0-22 4.15.0-22.24    amd64           Signed kernel image generic
rc  linux-image-4.15.0-23 4.15.0-23.25    amd64           Signed kernel image generic
...... several more .....
rc linux-image-4.15.0-99 4.15.0-99.100   amd64           Signed kernel image generic
iU  linux-image-generic   4.15.0.109.97   amd64           Generic Linux kernel image


Mybe more information is needed.  Despite the errors marked the process continues with some errors and finally ended with > E: Sub-process /usr/bin/dpkg returned an error code (1)
Thanks for any help.

---

### Post by Bashing-om on 2020-07-06
marciano#1 - Hello

The line(s) " iF linux-image-4.15.0-10 4.15.0-109.110 ; iU linux-image-generic 4.15.0.109.97" suggest to me that at some point you ran short of disk space in /boot.
Show us what we have now for disk space:
```

df -h
df -i

```

And what kernel you are booting presently:
```

uname -r

```

See then what it will take to straighten the kernels up.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-07
```
df -h
```
[https://pastebin.com/VKCAuZn7](https://pastebin.com/VKCAuZn7)
```
df -i
```
[https://pastebin.com/fNUT761F](https://pastebin.com/fNUT761F)

```
uname -r 
```
> 4.15.0-108-generic

I usually make updates from Desktop updates, not from shell.
Because of an error I went to command shell.
I don't know what to do with that data.
Thank you

---

### Post by ActionParsnip on 2020-07-07
what is the output of:
```

dpkg -l | grep linux-image | grep -v extra

```
Thanks

---

### Post by marciano#1 on 2020-07-07
```
dpkg -l | grep linux-image | grep -v extra
```
[https://pastebin.com/5LD7RbK7](https://pastebin.com/5LD7RbK7)

Thank you!

---

### Post by Bashing-om on 2020-07-07
marciano#1; Well -

So far so good; we do have operating head room.

Let's first off clean out the 'rc' ( removed but config files remain) cruft:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
Now let's have a fresh look at what we are working toward:
```

dpkg -l | grep linux-

```

See what else needs attention besides linux-image-generic.

[INDENT]next step in that process
[/INDENT]

---

### Post by marciano#1 on 2020-07-07
Here we go.
After:```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
dpkg -l | grep linux-
```

[https://pastebin.com/DZCPkyD3](https://pastebin.com/DZCPkyD3)

---

### Post by Bashing-om on 2020-07-07
marciano#1; Hey -

Looking promising,

Let's see if apt will work its magic to fix the 109 version kernel -
run:
```

sudo apt install --reinstall linux-generic

```
which should pull in the missing 109 dependencies.
If so then we shift our attention to the 108 version kernel fixes.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-08
Here it is the reinstall
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 17 not upgraded.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-generic:amd64


---

### Post by Bashing-om on 2020-07-08
marciano#1; Wow !

Totally unexpected " Internal Error, No file name for linux-generic:amd64"
Ouch !
as we also have
> 
and 17 not upgraded.

show us the results of terminal commands:
```

sudo apt update
sudo apt full-upgrade

```

Maybe get a better hint of a way forward.

[INDENT]make the process work and work the process
[/INDENT]

---

### Post by marciano#1 on 2020-07-09
Sorry for the delay, I wasn't in town.
> sudo apt update
[https://pastebin.com/S3VvvxTM](https://pastebin.com/S3VvvxTM)
```
sudo apt full-upgrade
```
[https://pastebin.com/jX8m96Ep](https://pastebin.com/jX8m96Ep)
Thank you!

---

### Post by Bashing-om on 2020-07-09
marciano#1; Hey

We work at your pace -

Not looking to shabby now.
We are only concerned with the 108 and 109 kernel versions ? You have no care for the original installed series kernels ?

Lets run:
```

sudo dpkg-reconfigure linux-image-generic

```

then once completed show us:
```

uname -r
lsb_release -a
dpkg -l | grep linux-

```
to decide on what to do next -

[INDENT][INDENT]in the process of restoration
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-09
Starting not good:
```
sudo dpkg-reconfigure linux-image-generic
```
> /usr/sbin/dpkg-reconfigure: linux-image-generic is broken or not fully installed

---

### Post by Bashing-om on 2020-07-09
marciano#1; Yukkie -

OK
```

sudo apt install linux-image-generic

```
give us a way forward ?

[INDENT][INDENT]Keep it as simple as possible
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-10
Here you have!
```
sudo apt install linux-image-generic
```
[https://pastebin.com/XGfstpmM](https://pastebin.com/XGfstpmM)

---

### Post by Bashing-om on 2020-07-10
marciano#1 Well - Not -

Lets see if it is "Fatal: open /boot/vmlinuz-4.15.0-76-generic:" holding us up.

I ask again - is there a reason you want to hold on to the original series kernels ? As you are presently booting the HWE ( HardWare Enablement stack) kernel; maybe best to just get rid of the old kernels. 
```

uname -r

``` that one ^ we do not want to mess about with.

-ain't nothing but a thing-

---

### Post by marciano#1 on 2020-07-10
> I ask again - is there a reason you want to hold on to the original series kernels ?
No, I don't need them.
```
uname -r
```
4.15.0-109-generic

---

### Post by Bashing-om on 2020-07-10
marciano#1; Hokay :)

Though I did get a wire crossed somewhere as you are presently booting the latest 18.04 kernel; do not know where My attention got focused on HWE.

Show us a new:
```

dpkg -l | grep linux-

```
and we purge these old kernels.

[INDENT][INDENT]look'n for that way forward
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-11
```
dpkg -l | grep linux-
```
[https://pastebin.com/e3cu0ueg](https://pastebin.com/e3cu0ueg)
Thank you!

---

### Post by ActionParsnip on 2020-07-11
If the other kernels have the equivalent /boot/vmlinuz-xxx file then you could try making the file with:
```

sudo touch /boot/vmlinuz-4.15.0-76-generic
sudo apt autoremove

``` 
Does that help?

---

### Post by marciano#1 on 2020-07-11
Mmmm, still
> E: Sub-process /usr/bin/dpkg returned an error code (1)
```
sudo apt autoremove
```
[https://pastebin.com/CjJDncTf](https://pastebin.com/CjJDncTf)

---

### Post by Bashing-om on 2020-07-11
marciano#1; So -

Back again to:
> 
linux-image-4.15.0-91-generic
vmlinuz-4.15.0-76-generic


The question is how dirty do we get in order to remove these ?

I would like to see a current dpkg of the installed kernels:
```

dpkg -l | grep linux-

``` 
and decide if we are to break the package management system in the process to resolve this.

[INDENT]we have a procedure .....
[/INDENT]

---

### Post by marciano#1 on 2020-07-11
Here you have!
```
dpkg -l | grep linux-
```
(pastebin.com is "under heavy load")
> ii  binutils-x86-64-linux-gnu                     2.30-21ubuntu1~18.04.3                           amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                    4.5ubuntu1.2                                     all          Linux image base package
iF  linux-firmware                                1.173.19                                         all          Firmware for Linux kernel drivers
iU  linux-generic                                 4.15.0.109.97                                    amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-108                      4.15.0-108.109                                   all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-108-generic              4.15.0-108.109                                   amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-109                      4.15.0-109.110                                   all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-109-generic              4.15.0-109.110                                   amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.15.0.109.97                                    amd64        Generic Linux kernel headers
iF  linux-image-4.15.0-108-generic                4.15.0-108.109                                   amd64        Signed kernel image generic
iF  linux-image-4.15.0-109-generic                4.15.0-109.110                                   amd64        Signed kernel image generic
iF  linux-image-4.15.0-91-generic                 4.15.0-91.92                                     amd64        Signed kernel image generic
iU  linux-image-generic                           4.15.0.109.97                                    amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.15.0-109.110                                   amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-108-generic              4.15.0-108.109                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-109-generic              4.15.0-109.110                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-91-generic               4.15.0-91.92                                     amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-108-generic        4.15.0-108.109                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-109-generic        4.15.0-109.110                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-91-generic         4.15.0-91.92                                     amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
iU  linux-signed-generic                          4.15.0.109.97                                    amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                             all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.03+dfsg1-2                                   all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                             amd64        Bootloader for Linux/i386 using MS-DOS floppies


---

### Post by Bashing-om on 2020-07-11
marciano#1 Welp -

Do not see here how "vmlinuz-4.15.0-76-generic" plays into this.
 We dig deeper.
As I do prefer the results posted here on the forum -  in this case "(pastebin.com is "under heavy load")" is a good thing for me.

show us:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```
we must make all three agree. And in that process, as we go behind the package manager's back, we break the system. We will later have the package manager heal its self. IF we get that dirty.

[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-11
```
ls -al /usr/src/
```
> total 28
drwxr-xr-x  7 root root 4096 jul  6 21:20 .
drwxr-xr-x 11 root root 4096 ago 13  2019 ..
drwxr-xr-x 25 root root 4096 jul  2 10:37 linux-headers-4.15.0-108
drwxr-xr-x  8 root root 4096 jul  2 10:37 linux-headers-4.15.0-108-generic
drwxr-xr-x 25 root root 4096 jul  6 19:53 linux-headers-4.15.0-109
drwxr-xr-x  8 root root 4096 jul  6 19:53 linux-headers-4.15.0-109-generic
drw-r-xr-x  8 root root 4096 mar  1 21:12 rtl8192eu-4.4

```
ls -al /lib/modules/
```
> total 20
drwxr-xr-x  5 root root 4096 jul  7 20:51 .
drwxr-xr-x 21 root root 4096 abr 30  2018 ..
drwxr-xr-x  5 root root 4096 jul 11 15:45 4.15.0-108-generic
drwxr-xr-x  5 root root 4096 jul 11 15:45 4.15.0-109-generic
drwxr-xr-x  5 root root 4096 jul 11 15:45 4.15.0-91-generic
```
ls -al /boot/
```
> total 462524
drwxr-xr-x  4 root root     4096 jul 11 15:46 .
drwxr-xr-x 24 root root     4096 jul  6 19:54 ..
-rw-r--r--  1 root root      512 feb 13 20:21 boot.0800
-rw-r--r--  1 root root      512 feb 13 20:21 boot.0820
-rw-r--r--  1 root root      512 feb 13 20:21 boot.0830
-rw-r--r--  1 root root      512 jun 21 09:42 boot.0840
-rw-r--r--  1 root root   113162 feb 13 20:21 coffee.bmp
-rw-r--r--  1 root root   217473 jun 19 08:07 config-4.15.0-108-generic
-rw-r--r--  1 root root   217473 jun 22 23:07 config-4.15.0-109-generic
-rw-r--r--  1 root root   217457 feb 28 07:45 config-4.15.0-91-generic
-rw-r--r--  1 root root    22466 feb 13 20:21 debian.bmp
-rw-r--r--  1 root root    22560 feb 13 20:21 debian-de.bmp
-rw-r--r--  1 root root    31628 feb 13 20:21 debianlilo.bmp
drwx------  3 root root     4096 dic 31  1969 efi
drwxr-xr-x  5 root root     4096 jul  6 21:20 grub
-rw-r--r--  1 root root 39435273 jun 14 11:41 initrd.img-4.15.0-101-generic.dpkg-bak
-rw-r--r--  1 root root 39458901 jul  2 10:38 initrd.img-4.15.0-106-generic.dpkg-bak
-rw-r--r--  1 root root 39458225 jul 11 15:46 initrd.img-4.15.0-108-generic
-rw-r--r--  1 root root 39457411 jul  6 19:54 initrd.img-4.15.0-108-generic.dpkg-bak
-rw-r--r--  1 root root 39464040 jul 11 15:46 initrd.img-4.15.0-109-generic
-rw-r--r--  1 root root 39464102 jul 11 15:46 initrd.img-4.15.0-109-generic.dpkg-bak
-rw-r--r--  1 root root 39387194 mar 26 09:06 initrd.img-4.15.0-88-generic.dpkg-bak
-rw-r--r--  1 root root 39437351 jul 11 15:46 initrd.img-4.15.0-91-generic
-rw-r--r--  1 root root 39390977 abr 20 06:02 initrd.img-4.15.0-91-generic.dpkg-bak
-rw-r--r--  1 root root 39388962 may  4 20:42 initrd.img-4.15.0-96-generic.dpkg-bak
-rw-r--r--  1 root root 39388656 may 27 06:10 initrd.img-4.15.0-99-generic.dpkg-bak
-rw-r--r--  1 root root    22578 feb 13 20:21 inside.bmp
-rw-------  1 root root   961024 feb 19 06:32 map
-rw-r--r--  1 root root   182704 ene 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 ene 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 ene 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root     6878 feb 13 20:21 onlyblue.bmp
-rw-------  1 root root  4073353 jun 19 08:07 System.map-4.15.0-108-generic
-rw-------  1 root root  4073543 jun 22 23:07 System.map-4.15.0-109-generic
-rw-------  1 root root  4069388 feb 28 07:45 System.map-4.15.0-91-generic
-rw-r--r--  1 root root    33192 feb 13 20:21 tuxlogo.bmp
-rw-------  1 root root  8380064 jun 19 08:08 vmlinuz-4.15.0-108-generic
-rw-------  1 root root  8380064 jun 22 23:15 vmlinuz-4.15.0-109-generic
-rw-r--r--  1 root root        0 jul 11 15:37 vmlinuz-4.15.0-76-generic
-rw-------  1 root root  8375960 feb 28 07:51 vmlinuz-4.15.0-91-generic


---

### Post by Bashing-om on 2020-07-11
marciano#1; Yukkie poo -

Getting out of my experience range:
> 
drw-r-xr-x 8 root root 4096 mar 1 21:12 rtl8192eu-4.4
debian.bmp
inside.bmp
map
onlyblue.bmp


Slackware - Debian -  Lilo ? What in the world are we dealing with ?
Looks like we will get dirty ! But, presently I do not know what to clean up
.
What else is also on this ubuntu system ?
show us:
```

ls -al /usr/src/rtl8192eu-4.4
cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

Gonna go mow grass for a spell and cogitate on this sloppyation,

[INDENT][INDENT]consider where we go from here
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-12
> But, presently I do not know what to clean up
.
Imagine where I am standing! :)
```
ls -al /usr/src/rtl8192eu-4.4
```
> total 120
drw-r-xr-x 8 root root  4096 mar  1 21:12 .
drwxr-xr-x 7 root root  4096 jul  6 21:20 ..
-rw-r--r-- 1 root root    64 ago 17  2016 clean
drw-r-xr-x 3 root root  4096 mar  1 21:12 core
-rw-r--r-- 1 root root   243 ago 17  2016 dkms.conf
drw-r-xr-x 8 root root  4096 mar  1 21:12 hal
-rw-r--r-- 1 root root    54 ago 17  2016 ifcfg-wlan0
drw-r-xr-x 4 root root 12288 mar  1 21:12 include
-rw-r--r-- 1 root root   110 ago 17  2016 Kconfig
-rw-r--r-- 1 root root 52874 ago 17  2016 Makefile
drw-r-xr-x 3 root root  4096 mar  1 21:12 os_dep
drw-r-xr-x 2 root root  4096 mar  1 21:12 patches
drw-r-xr-x 2 root root  4096 mar  1 21:12 platform
-rw-r--r-- 1 root root   423 ago 17  2016 runwpa
-rw-r--r-- 1 root root   294 ago 17  2016 wlan0dhcp
-rw-r--r-- 1 root root  1517 ago 17  2016 wpa_0_8.conf

```
cat -n /etc/apt/sources.list
```
[https://pastebin.com/e0h4WJGR](https://pastebin.com/e0h4WJGR)
```
cat /etc/apt/sources.list.d/*.list
```
[https://pastebin.com/HSh4UaW4](https://pastebin.com/HSh4UaW4)
Thank you!

---

### Post by Bashing-om on 2020-07-12
marciano#1; Ho-Kay :)

I see no reason not to proceed with destruction.
The rtl8192eu-4.4 is a wireless driver and I see nothing in sources to hinder the kernel.

Here goes:
```

sudo rm -rf /lib/modules/4.15.0-91-generic
sudo rm /boot/config-4.15.0-91-generic
sudo rm /boot/initrd.img-4.15.0-101-generic.dpkg-bak
sudo rm /boot/initrd.img-4.15.0-106-generic.dpkg-bak
sudo rm /boot/initrd.img-4.15.0-88-generic.dpkg-bak
sudo rm /boot/initrd.img-4.15.0-91-generic
sudo rm /boot/initrd.img-4.15.0-91-generic.dpkg-bak
sudo rm /boot/initrd.img-4.15.0-96-generic.dpkg-bak
sudo rm /boot/initrd.img-4.15.0-99-generic.dpkg-bak
sudo rm /boot/System.map-4.15.0-91-generic
sudo rm /boot/vmlinuz-4.15.0-76-generic
sudo rm /boot/vmlinuz-4.15.0-91-generic

```

Next repair the package system.
```

sudo apt -f install

```

Finally properly uninstall the kernels and headers whose files you already deleted.
```

sudo apt purge linux-{headers,image}-4.15.0-{76,88,91,96,99,101,106}.*

```

Reboot and now let's see what is:
```

sudo apt update
sudo apt upgrade
sudo dpkg -C

```

By the way - your post has made it into this week's UbuntuWeeklyNewsletter: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue639](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue639)

[INDENT][INDENT]let there be healing
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-12
Still errors here. I didn't continue with  *purge*. Should I?
```
sudo apt -f install
```
[https://pastebin.com/7GN3XWFz](https://pastebin.com/7GN3XWFz)

---

### Post by Bashing-om on 2020-07-12
marciano#1; Uh HUh 

Continue on with the purge - see what happens then run the apt-f install command once more.

[INDENT][INDENT]if at 1st we do not succeed ->
[INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-12
```
sudo apt purge linux-{headers,image}-4.15.0-{76,88,91,96,99,101.106}.*
```
[https://pastebin.com/ceeseFPW](https://pastebin.com/ceeseFPW)
```
sudo apt -f install
```
[https://pastebin.com/bfcVBaqD](https://pastebin.com/bfcVBaqD)
Reboot
```
sudo apt update
```
> Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic InRelease                     
Hit:3 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-updates InRelease             
Hit:4 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                         
Hit:5 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-backports InRelease           
Hit:6 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-security InRelease            
Hit:7 [http://ppa.launchpad.net/hluk/copyq/ubuntu](http://ppa.launchpad.net/hluk/copyq/ubuntu) bionic InRelease              
Hit:8 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                      
Hit:9 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) bionic InRelease               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```
apt list --upgradable
```
> copyq/bionic 3.12.0~bionic amd64 [upgradable from: 3.11.1~bionic]
N: There are 2 additional versions. Please use the '-a' switch to see them.
```
apt list --upgradable -a
```
> copyq/bionic 3.12.0~bionic amd64 [upgradable from: 3.11.1~bionic]
copyq/now 3.11.1~bionic amd64 [installed,upgradable to: 3.12.0~bionic]
copyq/bionic 3.2.0-1 amd64

```
sudo apt upgrade
```
[https://pastebin.com/cfuWEUhx](https://pastebin.com/cfuWEUhx)
```
apt list --upgradable -a
```
> Listing... Done
```
sudo dpkg -C
```
> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-generic  Generic Linux kernel image
 linux-signed-generic Complete Signed Generic Linux kernel and headers (dummy t

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      generic modular initramfs generator (automation)
 linux-firmware       Firmware for Linux kernel drivers
 linux-image-4.15.0-108-generic Signed kernel image generic
 linux-image-4.15.0-109-generic Signed kernel image generic
 linux-image-4.15.0-91-generic Signed kernel image generic


---

### Post by Bashing-om on 2020-07-12
marciano#1 - progress made - but 
Huh ??
> 
linux-image-4.15.0-91-generic Signed kernel image generic


Wonder how this got re-installed,
Try again:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```
get rid of that 91 kernel then we address linux-generic .

[INDENT]sometimes I wonder
[/INDENT]

---

### Post by marciano#1 on 2020-07-12
```
ls -al /usr/src/
```
> total 28
drwxr-xr-x  7 root root 4096 jul  6 21:20 .
drwxr-xr-x 11 root root 4096 ago 13  2019 ..
drwxr-xr-x 25 root root 4096 jul  2 10:37 linux-headers-4.15.0-108
drwxr-xr-x  8 root root 4096 jul  2 10:37 linux-headers-4.15.0-108-generic
drwxr-xr-x 25 root root 4096 jul  6 19:53 linux-headers-4.15.0-109
drwxr-xr-x  8 root root 4096 jul  6 19:53 linux-headers-4.15.0-109-generic
drw-r-xr-x  8 root root 4096 mar  1 21:12 rtl8192eu-4.4



```
ls -al /lib/modules/
```
> total 16
drwxr-xr-x  4 root root 4096 jul 12 16:44 .
drwxr-xr-x 21 root root 4096 abr 30  2018 ..
drwxr-xr-x  5 root root 4096 jul 12 18:44 4.15.0-108-generic
drwxr-xr-x  5 root root 4096 jul 12 18:44 4.15.0-109-generic

```
ls -al /boot/
```
> total 180704
drwxr-xr-x  4 root root     4096 jul 12 18:45 .
drwxr-xr-x 24 root root     4096 jul  6 19:54 ..
-rw-r--r--  1 root root      512 feb 13 20:21 boot.0800
-rw-r--r--  1 root root      512 feb 13 20:21 boot.0820
-rw-r--r--  1 root root      512 feb 13 20:21 boot.0830
-rw-r--r--  1 root root      512 jun 21 09:42 boot.0840
-rw-r--r--  1 root root   113162 feb 13 20:21 coffee.bmp
-rw-r--r--  1 root root   217473 jun 19 08:07 config-4.15.0-108-generic
-rw-r--r--  1 root root   217473 jun 22 23:07 config-4.15.0-109-generic
-rw-r--r--  1 root root    22466 feb 13 20:21 debian.bmp
-rw-r--r--  1 root root    22560 feb 13 20:21 debian-de.bmp
-rw-r--r--  1 root root    31628 feb 13 20:21 debianlilo.bmp
drwx------  3 root root     4096 dic 31  1969 efi
drwxr-xr-x  5 root root     4096 jul  6 21:20 grub
-rw-r--r--  1 root root 39456928 jul 12 18:45 initrd.img-4.15.0-108-generic
-rw-r--r--  1 root root 39457411 jul  6 19:54 initrd.img-4.15.0-108-generic.dpkg-bak
-rw-r--r--  1 root root 39464656 jul 12 18:45 initrd.img-4.15.0-109-generic
-rw-r--r--  1 root root 39464031 jul 12 18:45 initrd.img-4.15.0-109-generic.dpkg-bak
-rw-r--r--  1 root root    22578 feb 13 20:21 inside.bmp
-rw-------  1 root root   961024 feb 19 06:32 map
-rw-r--r--  1 root root   182704 ene 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 ene 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 ene 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root     6878 feb 13 20:21 onlyblue.bmp
-rw-------  1 root root  4073353 jun 19 08:07 System.map-4.15.0-108-generic
-rw-------  1 root root  4073543 jun 22 23:07 System.map-4.15.0-109-generic
-rw-r--r--  1 root root    33192 feb 13 20:21 tuxlogo.bmp
-rw-------  1 root root  8380064 jun 19 08:08 vmlinuz-4.15.0-108-generic
-rw-------  1 root root  8380064 jun 22 23:15 vmlinuz-4.15.0-109-generic


```
locate 4.15.0-91
```
> /boot/System.map-4.15.0-91-generic
/boot/config-4.15.0-91-generic
/boot/initrd.img-4.15.0-91-generic
/boot/initrd.img-4.15.0-91-generic.dpkg-bak
/boot/vmlinuz-4.15.0-91-generic
/lib/modprobe.d/blacklist_linux_4.15.0-91-generic.conf
/lib/modules/4.15.0-91-generic
/usr/lib/linux/triggers/4.15.0-91-generic
/usr/share/doc/linux-image-4.15.0-91-generic
/usr/share/doc/linux-image-unsigned-4.15.0-91-generic
/usr/share/doc/linux-modules-4.15.0-91-generic
/usr/share/doc/linux-modules-extra-4.15.0-91-generic
/usr/share/doc/linux-image-4.15.0-91-generic/changelog.Debian.gz
/usr/share/doc/linux-image-4.15.0-91-generic/copyright
/usr/share/doc/linux-modules-4.15.0-91-generic/changelog.Debian.gz
/usr/share/doc/linux-modules-4.15.0-91-generic/copyright
/usr/share/doc/linux-modules-extra-4.15.0-91-generic/changelog.Debian.gz
/usr/share/doc/linux-modules-extra-4.15.0-91-generic/copyright
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.list
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.md5sums
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.postinst
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.postrm
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.preinst
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.prerm
/var/lib/dpkg/info/linux-image-4.15.0-91-generic.triggers
/var/lib/dpkg/info/linux-modules-4.15.0-91-generic.list
/var/lib/dpkg/info/linux-modules-4.15.0-91-generic.md5sums
/var/lib/dpkg/info/linux-modules-4.15.0-91-generic.postinst
/var/lib/dpkg/info/linux-modules-4.15.0-91-generic.postrm
/var/lib/dpkg/info/linux-modules-extra-4.15.0-91-generic.list
/var/lib/dpkg/info/linux-modules-extra-4.15.0-91-generic.md5sums
/var/lib/dpkg/info/linux-modules-extra-4.15.0-91-generic.postinst
/var/lib/dpkg/info/linux-modules-extra-4.15.0-91-generic.postrm
/var/lib/dpkg/triggers/linux-update-4.15.0-91-generic
/var/lib/initramfs-tools/4.15.0-91-generic


---

### Post by Bashing-om on 2020-07-12
marciano#1; Humm ...

The find results from what is present in memory ? As we can see the -91 files no longer exist in the respective directories.
Maybe roll our sleeves up and find out what debian.bmp is all about ?

What results if you reboot the machine and then run all those above "looking" commands again ?

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-12
1) Reboot
2)```
 sudo apt purge linux-{headers,image}-4.15.0-{76,88,91,96,99,101.106}.*
```
[https://pastebin.com/z4uvDvH8](https://pastebin.com/z4uvDvH8)
3)```
sudo apt -f install
```
[https://pastebin.com/yvFpsVGR](https://pastebin.com/yvFpsVGR)
4)```
sudo apt autoremove
```
[https://pastebin.com/aDdie1wC](https://pastebin.com/aDdie1wC)
5) ```
sudo apt update
```
> Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                                                            
Hit:3 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                                                                               
Hit:4 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic InRelease                                                                           
Hit:5 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-updates InRelease                                      
Hit:6 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-backports InRelease     
Hit:7 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-security InRelease      
Hit:8 [http://ppa.launchpad.net/hluk/copyq/ubuntu](http://ppa.launchpad.net/hluk/copyq/ubuntu) bionic InRelease
Hit:9 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) bionic InRelease             
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
6)```
sudo apt upgrade
```
[https://pastebin.com/P2V0JVuZ](https://pastebin.com/P2V0JVuZ)
7)```
sudo dpkg -C
```
> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-generic  Generic Linux kernel image
 linux-signed-generic Complete Signed Generic Linux kernel and headers (dummy t

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      generic modular initramfs generator (automation)
 linux-firmware       Firmware for Linux kernel drivers
 linux-image-4.15.0-108-generic Signed kernel image generic
 linux-image-4.15.0-109-generic Signed kernel image generic
8)```
sudo dpkg --configure linux-image-4.15.0-109-generic
```
> Setting up linux-image-4.15.0-109-generic (4.15.0-109.110) ...
Processing triggers for linux-image-4.15.0-109-generic (4.15.0-109.110) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 4.15.0-109-generic

Kernel preparation unnecessary for this kernel.  Skipping...
applying patch Fix-build-for-4.4.patch...patching file hal/hal_btcoex.c
patching file hal/hal_com.c
patching file hal/hal_com_phycfg.c
patching file include/hal_com.h
patching file include/rtw_debug.h
patching file Makefile
patching file os_dep/linux/usb_intf.c


Building module:
cleaning build area...
'make' KVER=4.15.0-109-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtl8192eu-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-109-generic (x86_64)
Consult /var/lib/dkms/rtl8192eu/4.4/build/make.log for more information.
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-109-generic
/etc/kernel/postinst.d/zz-runlilo:
Fatal: open /boot/[COLOR="#FF0000"]vmlinuz-4.15.0-76-generic[/COLOR]: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-4.15.0-109-generic (--configure):
 installed linux-image-4.15.0-109-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-109-generic

9)```
sudo dpkg --configure linux-image-4.15.0-108-generic
```
> Setting up linux-image-4.15.0-108-generic (4.15.0-108.109) ...
Processing triggers for linux-image-4.15.0-108-generic (4.15.0-108.109) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 4.15.0-108-generic

Kernel preparation unnecessary for this kernel.  Skipping...
applying patch Fix-build-for-4.4.patch...patching file hal/hal_btcoex.c
patching file hal/hal_com.c
patching file hal/hal_com_phycfg.c
patching file include/hal_com.h
patching file include/rtw_debug.h
patching file Makefile
patching file os_dep/linux/usb_intf.c


Building module:
cleaning build area...
'make' KVER=4.15.0-108-generic...(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtl8192eu-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-108-generic (x86_64)
Consult /var/lib/dkms/rtl8192eu/4.4/build/make.log for more information.
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-108-generic
/etc/kernel/postinst.d/zz-runlilo:
Fatal: open /boot/[COLOR="#FF0000"]vmlinuz-4.15.0-76-generic[/COLOR]: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-4.15.0-108-generic (--configure):
 installed linux-image-4.15.0-108-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-108-generic
10) ```
sudo dpkg --configure linux-firmware
```
> Setting up linux-firmware (1.173.19) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-109-generic
Fatal: open /boot/v[COLOR="#FF0000"]mlinuz-4.15.0-76-generic[/COLOR]: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-firmware
11)```
sudo dpkg --configure initramfs-tools
```
> Setting up initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-109-generic
Fatal: open /boot/[COLOR="#FF0000"]vmlinuz-4.15.0-76-generic[/COLOR]: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

---

### Post by Bashing-om on 2020-07-12
marciano#1; Ouch - My Bad
"Starting with a certain release number (maybe 4.15.*) the "extra modules" package is no longer named linux-image-extra-xxx but linux-modules-extra-xxx," I plumb missed these.

Let's see if:
```

sudo apt purge linux-{headers,image,modules,modules-extra}-4.15.0-{76,88,91,96,99,101,106}.*

```
will purge the pesky  4.15.0-91-generic and 4.15.0-76-generic components as well as any other remnants on the system.

[INDENT][INDENT]sometimes I do not see the tree at all
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-13
Don't worry!  
Here we go.
```
sudo apt purge linux-{headers,image}-4.15.0-{76,88,91,96,99,101.106}.*
```
[https://pastebin.com/W18FJ9aV](https://pastebin.com/W18FJ9aV)
```
sudo apt update
```
> Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                                                            
Hit:3 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                                                                               
Hit:4 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic InRelease                                                                           
Hit:5 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-updates InRelease                                      
Hit:6 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-backports InRelease     
Hit:7 [http://repos.interior.edu.uy/ubuntu](http://repos.interior.edu.uy/ubuntu) bionic-security InRelease      
Hit:8 [http://ppa.launchpad.net/hluk/copyq/ubuntu](http://ppa.launchpad.net/hluk/copyq/ubuntu) bionic InRelease
Hit:9 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) bionic InRelease             
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
```
sudo apt upgrade
```
[https://pastebin.com/rDmGUR3M](https://pastebin.com/rDmGUR3M)
```
sudo dpkg -C
```
> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-generic  Generic Linux kernel image
 linux-signed-generic Complete Signed Generic Linux kernel and headers (dummy t

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      generic modular initramfs generator (automation)
 linux-firmware       Firmware for Linux kernel drivers
 linux-image-4.15.0-108-generic Signed kernel image generic
 linux-image-4.15.0-109-generic Signed kernel image generic
```
sudo dpkg --configure linux-image-4.15.0-109-generic
```
[https://pastebin.com/0JHT3EE8](https://pastebin.com/0JHT3EE8)

---

### Post by Bashing-om on 2020-07-13
marciano#1; nope -

Note the changed purge command:
```

sudo apt purge linux-{headers,image,modules,modules-extra}-4.15.0-{76,88,91,96,99,101,106}.*

```
(also has a typo correction for a period vice comma).

We are making progress. But, there are a couple of items to find resolution.
Reboot after the purge completes and post back:
```

dpkg -l | grep linux-

```

see now what we have to direct the package manager to conduct.

[INDENT][INDENT]we can do - Yes !
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-13
```
dpkg -l | grep linux -
```[https://pastebin.com/h8ahnyqz](https://pastebin.com/h8ahnyqz)

---

### Post by Bashing-om on 2020-07-13
marciano#1; Huh ?

Why of why - where does -91 keep getting installed from ?

Can we get some hints as to what is going on from:
```

sudo apt --purge linux-image-4.15.0-91-generic
sudo apt --purge linux-modules-4.15.0-91-generic
sudo apt --purge linux-modules-extra-4.15.0-91-generic

```

and still to deal with is linux-firmware, linux-generic, linux-signed-generic. and linux-image-generic 4.15.0.109.97. Which at some point we will have the package manager cope with them.

[INDENT][INDENT]A process in learning
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-13
Doesn't want to be purged!
```
sudo apt purge linux-image-4.15.0-91-generic
```
[https://pastebin.com/WRbWfMFH](https://pastebin.com/WRbWfMFH)
```
sudo apt purge linux-modules-4.15.0-91-generic
```
[https://pastebin.com/HMdQaC1D](https://pastebin.com/HMdQaC1D)
```
sudo apt purge linux-modules-extra-4.15.0-91-generic
```
[https://pastebin.com/](https://pastebin.com/)

---

### Post by Bashing-om on 2020-07-13
marciano#1; Yukkie poo -


Several things here I do not understand ( run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1) But let's see if
```

sudo apt install --reinstall linux-firmware
sudo apt install --reinstall linux-generic

```

rather than a reconfigure, to move us forward.

[INDENT][INDENT]find that block
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-14
```
sudo apt install --reinstall linux-firmware
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-firmware:amd64

```
sudo apt install --reinstall linux-generic
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-generic:amd64


---

### Post by Bashing-om on 2020-07-14
marciano#1; Huh ??

What a crock !
as we do have:
> 
sysop@x1804mini:~$ apt list linux-firmware
Listing... Done
linux-firmware/bionic-updates,bionic-updates,now 1.173.19 all [installed,automatic]
N: There are 2 additional versions. Please use the '-a' switch to see them.

sysop@x1804mini:~$ apt list linux-generic
Listing... Done
linux-generic/bionic-security,bionic-updates,now 4.15.0.111.99 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
sysop@x1804mini:~$

As you also do have them partially installed - 

Well well well ->
Try as:
```

sudo apt install linux-firmware
sudo apt install linux-generic

```

as round and round we continue to go

---

### Post by marciano#1 on 2020-07-14
.111 is here.
```
sudo apt install linux-firmware
```
[https://pastebin.com/bKZGKgBs](https://pastebin.com/bKZGKgBs)
```
sudo apt install linux-generic
```
[https://pastebin.com/KbrtUW8R](https://pastebin.com/KbrtUW8R)

---

### Post by Bashing-om on 2020-07-14
marciano#1; Ouch !

Why oh why !
Is it the -76 kernel situation that is holding us up ?
what shows:
```

sudo find / -name "*4.15.0-76-generic"

```

As it keeps on showing up in spite of efforts to purge it . We do want it gone gone.

[INDENT][INDENT]try try again.
[/INDENT][/INDENT]

---

### Post by marciano#1 on 2020-07-14
```
sudo find / -name "*4.15.0-76-generic"
```
First results, still finding...
> find: &#8216;/proc/1152/task/1152/net&#8217;: Invalid argument
find: &#8216;/proc/1152/net&#8217;: Invalid argument
find: &#8216;/run/user/1000/doc&#8217;: Permission denied
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied


....  no more results

---

### Post by Bashing-om on 2020-07-14
marciano#1; Yuk !

Why then does:
> 
Fatal: open /boot/vmlinuz-4.15.0-76-generic: No such file or directory

keep re-appearing and from where ?

We can give a specific look - but "find" does not lie!
```

ls -al /boot/
ls -al /lib/modules/
ls -al /usr/src/
ls -al /var/lib/initramfs-tools/

```

-trying to build the wireless driver the cause ?- just brainstorming.

-sometimes I just do not know-

---

### Post by marciano#1 on 2020-07-14
```
ls -al /boot/
```
[https://pastebin.com/LqSnwDiL](https://pastebin.com/LqSnwDiL)
```
ls -al /lib/modules/
```
> total 20
drwxr-xr-x  5 root root 4096 jul 14 19:04 .
drwxr-xr-x 21 root root 4096 abr 30  2018 ..
drwxr-xr-x  5 root root 4096 jul 14 19:04 4.15.0-108-generic
drwxr-xr-x  5 root root 4096 jul 14 19:04 4.15.0-109-generic
drwxr-xr-x  5 root root 4096 jul 14 19:05 4.15.0-111-generic
```
ls -al /usr/src/
```
> total 36
drwxr-xr-x  9 root root 4096 jul 14 19:04 .
drwxr-xr-x 11 root root 4096 ago 13  2019 ..
drwxr-xr-x 25 root root 4096 jul  2 10:37 linux-headers-4.15.0-108
drwxr-xr-x  8 root root 4096 jul  2 10:37 linux-headers-4.15.0-108-generic
drwxr-xr-x 25 root root 4096 jul  6 19:53 linux-headers-4.15.0-109
drwxr-xr-x  8 root root 4096 jul  6 19:53 linux-headers-4.15.0-109-generic
drwxr-xr-x 25 root root 4096 jul 14 19:04 linux-headers-4.15.0-111
drwxr-xr-x  8 root root 4096 jul 14 19:04 linux-headers-4.15.0-111-generic
drw-r-xr-x  8 root root 4096 mar  1 21:12 rtl8192eu-4.4

```
ls -al /var/lib/initramfs-tools/
```
> total 20
drwxr-xr-x  2 root root 4096 jul 14 19:05 .
drwxr-xr-x 68 root root 4096 jul  6 19:49 ..
-rw-r--r--  1 root root   78 jul 14 19:05 4.15.0-108-generic
-rw-r--r--  1 root root   78 jul 14 19:05 4.15.0-109-generic
-rw-r--r--  1 root root   78 jul 14 19:05 4.15.0-111-generic

No trace of ...76

---

### Post by Bashing-om on 2020-07-14
marciano#1; Yup -

All looks sane to me -
And confirms that "find" does not lie.

I am stuck on this merry-go-round - gonna have to cogitate some more for a way out.

[INDENT][INDENT]gots to be a way
[/INDENT][/INDENT]

---

### Post by tboerner on 2020-07-14
What I can see here is that this seems always to be the problem:

> Fatal: open /boot/vmlinuz-4.15.0-76-generic: No such file or directory  

And this is ALWAYS preceded by this:

> update-initramfs: Generating /boot/initrd.img-4.15.0-109-generic  

There must be a problem with that kernel or with initramfs I think. What about trying to remove this kernel (the ...-109)? Make sure it is not the actually running one (uname -a )!

---

### Post by marciano#1 on 2020-07-16
Hi!
109 is the present used kernel
```
uname -a
```
> 4.15.0-109-generic #110-Ubuntu SMP Tue Jun 23 02:39:32 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by marciano#1 on 2020-07-16
Hi!
109 is the present used kernel
```
uname -a
```
> 4.15.0-109-generic #110-Ubuntu SMP Tue Jun 23 02:39:32 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Bashing-om on 2020-07-16
marciano#1; Sorry -

As much as it pains me - I must admit that I do not know what else to check, nor a way forward.

[INDENT]a know it all I am not
[/INDENT]

---

### Post by marciano#1 on 2020-07-16
I rebooted and loaded kernel ...108
> 4.15.0-**108**-generic #109-Ubuntu SMP Fri Jun 19 11:33:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Should I remove kernel ...109?
How so?
Thank you!

---

### Post by Bashing-om on 2020-07-16
marciano#1; Well 

> 
Should I remove kernel ...109?

NO - that is the backup kernel for the -111 version.

Did kernel 111 install fully ?
```

dpkg -l | grep linux- 
ls -al /

```

Needed is to find why 4.15.0-76-generic is still on the system that might be holding up  linux-firmware et all.

[INDENT]But I just do not know
[/INDENT]

---

### Post by marciano#1 on 2020-07-17
```
dpkg -l | grep linux- 
```
> ii  binutils-x86-64-linux-gnu                     2.30-21ubuntu1~18.04.3                           amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                    4.5ubuntu1.2                                     all          Linux image base package
iF  linux-firmware                                1.173.19                                         all          Firmware for Linux kernel drivers
iU  linux-generic                                 4.15.0.111.99                                    amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-109                      4.15.0-109.110                                   all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-109-generic              4.15.0-109.110                                   amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-111                      4.15.0-111.112                                   all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-111-generic              4.15.0-111.112                                   amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.15.0.111.99                                    amd64        Generic Linux kernel headers
iF  linux-image-4.15.0-108-generic                4.15.0-108.109                                   amd64        Signed kernel image generic
iF  linux-image-4.15.0-109-generic                4.15.0-109.110                                   amd64        Signed kernel image generic
iF  linux-image-4.15.0-111-generic                4.15.0-111.112                                   amd64        Signed kernel image generic
ic  linux-image-4.15.0-91-generic                 4.15.0-91.92                                     amd64        Signed kernel image generic
iU  linux-image-generic                           4.15.0.111.99                                    amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.15.0-109.110                                   amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-108-generic              4.15.0-108.109                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-109-generic              4.15.0-109.110                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-111-generic              4.15.0-111.112                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ic  linux-modules-4.15.0-91-generic               4.15.0-91.92                                     amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-108-generic        4.15.0-108.109                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-109-generic        4.15.0-109.110                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-111-generic        4.15.0-111.112                                   amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ic  linux-modules-extra-4.15.0-91-generic         4.15.0-91.92                                     amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
iU  linux-signed-generic                          4.15.0.109.97                                    amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                             all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.03+dfsg1-2                                   all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                             amd64        Bootloader for Linux/i386 using MS-DOS floppies

```
ls -al /
```
> total 15728752
drwxr-xr-x  24 root root        4096 jul 14 19:04 .
drwxr-xr-x  24 root root        4096 jul 14 19:04 ..
drwxr-xr-x   2 root root        4096 jun  7 11:37 bin
drwxr-xr-x   4 root root        4096 jul 17 06:31 boot
drwxr-xr-x   2 root root        4096 abr 30  2018 cdrom
drwxr-xr-x  20 root root        4580 jul 17 00:02 dev
drwxr-xr-x 144 root root       12288 jul 17 06:31 etc
drwxr-xr-x   3 root root        4096 abr 30  2018 home
lrwxrwxrwx   1 root root          34 jul 14 19:04 initrd.img -> boot/initrd.img-4.15.0-111-generic
lrwxrwxrwx   1 root root          34 jul 14 19:04 initrd.img.old -> boot/initrd.img-4.15.0-109-generic
drwxr-xr-x  21 root root        4096 abr 30  2018 lib
drwxr-xr-x   2 root root        4096 jul  9 09:42 lib64
drwx------   2 root root       16384 abr 30  2018 lost+found
drwxr-xr-x  12 root root        4096 ene 16 21:37 media
drwxr-xr-x   5 root root        4096 jun 28  2019 mnt
drwxr-xr-x   4 root root        4096 may  1  2018 opt
dr-xr-xr-x 299 root root           0 jul 16 18:57 proc
drwx------   6 root root        4096 ene  9  2020 root
drwxr-xr-x  33 root root        1100 jul 17 12:04 run
drwxr-xr-x   2 root root       12288 jul  8 06:15 sbin
drwxr-xr-x  18 root root        4096 abr 25 11:31 snap
drwxr-xr-x   3 root root        4096 jul  3  2018 srv
-rw-------   1 root root 16106127360 may  1  2018 swapfile
dr-xr-xr-x  13 root root           0 jul 16 18:57 sys
drwxrwxrwt  19 root root        4096 jul 17 11:59 tmp
drwxr-xr-x  11 root root        4096 ago 13  2019 usr
drwxr-xr-x  14 root root        4096 abr 26  2018 var
lrwxrwxrwx   1 root root          31 jul 14 19:04 vmlinuz -> boot/vmlinuz-4.15.0-111-generic
lrwxrwxrwx   1 root root          31 jul 14 19:04 vmlinuz.old -> boot/vmlinuz-4.15.0-109-generic


---

### Post by Bashing-om on 2020-07-17
marciano#1; Yukkies again

You have time and again removed old kernel modules and they re-appear - no idea here WHY.
The latest kernel, -111, also failed to (U)npack thus did not fully install due to the linux-firmwares failures.

Presently no additional idea of a way forward :(

[INDENT]I hate when that happens
[/INDENT]

---

