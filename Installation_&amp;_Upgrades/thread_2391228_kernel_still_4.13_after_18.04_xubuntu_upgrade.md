---
title: "kernel still 4.13 after 18.04 xubuntu upgrade"
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by iains on 2018-05-07
I have just upgraded Xubuntu 17.10 to 18.04 apparently successfully.
The only problem is that my kernel is still 14.13.0.16.

I tried to force the update to 15.18  using UKUU kernel update utility
this seemed  to work but when I rebooted GRUB it still referred to 17.10 and gave me 14.13


```
 
>inxi -SMCG
System:    Host: xxxxxx Kernel: 4.13.0-16-generic x86_64
           bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: P7P55D LE v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 2003 date: 12/16/2010
CPU:       Quad core Intel Core i5 750 (-MCP-) cache: 8192 KB
           clock speeds: max: 2668 MHz 1: 2674 MHz 2: 2674 MHz 3: 2674 MHz
           4: 2674 MHz
Graphics:  Card: NVIDIA G94 [GeForce 9600 GT]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           OpenGL: renderer: NV94 version: 3.3 Mesa 18.0.0-rc5

```

Further investigation showed in '/' I
```

lrwxrwxrwx   1 root root    35 May  7 13:59 vmlinuz -> boot/vmlinuz-4.15.18-041518-generic
lrwxrwxrwx   1 root root    30 May  7 12:59 vmlinuz.old -> boot/vmlinuz-4.15.0-20-generic

```
and in /boot
```

-rw-r--r--  1 root root  1500286 Oct 11  2017 abi-4.13.0-16-generic
-rw-r--r--  1 root root  1536934 Apr 24 05:56 abi-4.15.0-20-generic
-rw-r--r--  1 root root  1507974 Apr 19 08:51 abi-4.15.18-041518-generic
-rw-r--r--  1 root root   213028 Oct 11  2017 config-4.13.0-16-generic
-rw-r--r--  1 root root   216807 Apr 24 05:56 config-4.15.0-20-generic
-rw-r--r--  1 root root   215099 Apr 19 08:51 config-4.15.18-041518-generic
drwxr-xr-x  5 root root     4096 May  7 14:01 grub
-rw-r--r--  1 root root 50804649 May  7 13:03 initrd.img-4.13.0-16-generic
-rw-r--r--  1 root root 54171601 May  7 13:11 initrd.img-4.15.0-20-generic
-rw-r--r--  1 root root 53402777 May  7 14:00 initrd.img-4.15.18-041518-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root        0 Apr 24 05:56 retpoline-4.15.0-20-generic
-rw-r--r--  1 root root        0 Apr 19 08:51 retpoline-4.15.18-041518-generic
-rw-------  1 root root  3878463 Oct 11  2017 System.map-4.13.0-16-generic
-rw-------  1 root root  4038188 Apr 24 05:56 System.map-4.15.0-20-generic
-rw-------  1 root root  4014611 Apr 19 08:51 System.map-4.15.18-041518-generic
-rw-r--r--  1 root root  7812896 Dec 18 11:16 vmlinuz-4.13.0-16-generic
-rw-------  1 root root  8249080 Apr 24 05:42 vmlinuz-4.15.0-20-generic
-rw-------  1 root root  8206192 Apr 19 08:51 vmlinuz-4.15.18-041518-generic

```

so the new kernels were installed but not loaded


I suspect the problem may be that I have too many options(17) in my grub.cfg file 
I have a lot old file systems that at some time or another were had been bootable that I never cleared.

Is this likely to be the problem?

---

### Post by cruzer001 on 2018-05-07
Start with
```
sudo apt autoremove
```
What does that say?

---

### Post by dino99 on 2018-05-07
It's time to run 'autoremove' before you get an other big warning 'missing space' in /boot  ;)

Looks like you have several OS partitions installed, and the 'master' grub menu needs to be updated to know about the latest changes made ):P

---

### Post by iains on 2018-05-07
Hi cruzer99

```

sudo apt autoremove
[sudo] password --
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libappindicator1 libboost-python1.65.1 libextutils-depends-perl
  libextutils-pkgconfig-perl libindicator7 pkg-config
0 to upgrade, 0 to newly install, 6 to remove and 1 not to upgrade.
After this operation, 977 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 253771 files and directories currently installed.)
Removing libappindicator1 (12.10.1+18.04.20180322.1-0ubuntu1) ...
Removing libboost-python1.65.1 (1.65.1+dfsg-0ubuntu5) ...
Removing libextutils-depends-perl (0.405-1) ...
Removing libextutils-pkgconfig-perl (1.16-1) ...
Removing libindicator7 (16.10.0+18.04.20180321.1-0ubuntu1) ...
Removing pkg-config (0.29.1-0ubuntu2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2) ...


```

---

### Post by dino99 on 2018-05-07
Looks like the old kernels has not been purged: are they manual installs ? Open the file manager, and delete them from /boot, then update-grub.

---

### Post by iains on 2018-05-07
dino99 said 

"Looks like the old kernels has not been purged: are they manual installs ? 
Open the file manager, and delete them from /boot, then update-grub. "

There are abi.., config.., initrd, system.map..., retpoline.. for each version as well as vmlinuz
should I remove all the unwanted or just vmlinuz... ?

Sorry if it's a bit elementary but I haven't done this before (hence all the old boots!)

thanks 
iain

---

### Post by cruzer001 on 2018-05-07
May want to know what kernel your running before you delete anything.  A (for me) bit easier format to read:
```
uname -r && dpkg --get-selections linux*
```

---

### Post by iains on 2018-05-07
uname -r && dpkg --get-selections linux

gives

```

4.13.0-16-generic
linux-base					install
linux-firmware					install
linux-generic					install
linux-headers-4.15.0-20				install
linux-headers-4.15.0-20-generic			install
linux-headers-4.15.18-041518			install
linux-headers-4.15.18-041518-generic		install
linux-headers-generic				install
linux-image-4.13.0-16-generic			install
linux-image-4.13.0-19-generic			deinstall
linux-image-4.13.0-21-generic			deinstall
linux-image-4.13.0-25-generic			deinstall
linux-image-4.13.0-31-generic			deinstall
linux-image-4.13.0-32-generic			deinstall
linux-image-4.13.0-36-generic			deinstall
linux-image-4.13.0-37-generic			deinstall
linux-image-4.13.0-38-generic			deinstall
linux-image-4.13.0-39-generic			deinstall
linux-image-4.15.0-20-generic			install
linux-image-4.15.18-041518-generic		install
linux-image-extra-4.13.0-16-generic		install
linux-image-extra-4.13.0-19-generic		deinstall
linux-image-extra-4.13.0-21-generic		deinstall
linux-image-extra-4.13.0-25-generic		deinstall
linux-image-extra-4.13.0-31-generic		deinstall
linux-image-extra-4.13.0-32-generic		deinstall
linux-image-extra-4.13.0-36-generic		deinstall
linux-image-extra-4.13.0-37-generic		deinstall
linux-image-extra-4.13.0-38-generic		deinstall
linux-image-extra-4.13.0-39-generic		deinstall
linux-image-generic				install
linux-libc-dev:amd64				install
linux-modules-4.15.0-20-generic			install
linux-modules-extra-4.15.0-20-generic		install
linux-sound-base				install


```

thanks

---

### Post by cruzer001 on 2018-05-07
```
sudo update-grub
```
and reboot
That should put you on the 4.15 kernel.  Verify that with:
```
uname -r
```
If your now on the 4.15 kernel, try running the autoremove command again.

---

### Post by iains on 2018-05-07
Still very strange (and still 4.13)

as dino99 suggested (more or less) I renamed all the 4.13.0-16 files  to 'was_xxxxxxx'
(having backed up /boot first)

then ran update-grub which seemed ok.

on reboot  grub failed saying it couldn't find 4.13... files

I reinstated back-up to restore situation.

I have extracted the menuentry items from grub.cfg

( awk -F\' '/menuentry / {print $2}' /boot/grub/grub.cfg  )

and got this```

Ubuntu
Ubuntu, with Linux 4.15.18-041518-generic
Ubuntu, with Linux 4.15.18-041518-generic (recovery mode)
Ubuntu, with Linux 4.15.0-20-generic
Ubuntu, with Linux 4.15.0-20-generic (recovery mode)
Ubuntu, with Linux 4.13.0-16-generic
Ubuntu, with Linux 4.13.0-16-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (on /dev/sda1)
Ubuntu 11.04 (11.04) (on /dev/sda11)
Ubuntu 11.04, kernel 2.6.38-12-generic (on /dev/sda11)
Ubuntu 11.04, kernel 2.6.38-12-generic (recovery mode) (on /dev/sda11)
Ubuntu 11.04, kernel 2.6.38-11-generic (on /dev/sda11)
Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode) (on /dev/sda11)
Ubuntu 11.04, memtest86+ (on /dev/sda11)
Linux Mint Debian Edition (1) (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.2.0-4-amd64 (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.2.0-4-amd64 (recovery mode) (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.2.0-3-amd64 (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.2.0-3-amd64 (recovery mode) (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.2.0-2-amd64 (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.2.0-2-amd64 (recovery mode) (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.0.0-1-amd64 (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 3.0.0-1-amd64 (recovery mode) (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 2.6.39-2-amd64 (on /dev/sda6)
LinuxMint GNU/Linux, with Linux 2.6.39-2-amd64 (recovery mode) (on /dev/sda6)
Linux Mint 18.3 Sylvia (18.3) (on /dev/sda7)
Linux Mint 18.3 Xfce 64-bit (on /dev/sda7)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.10.0-38-generic (on /dev/sda7)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.10.0-38-generic (upstart) (on /dev/sda7)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.10.0-38-generic (recovery mode) (on /dev/sda7)
Linux Mint 18 Sarah (18) (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-34-generic (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-34-generic (upstart) (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-34-generic (recovery mode) (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-21-generic (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-21-generic (upstart) (on /dev/sdb6)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-21-generic (recovery mode) (on /dev/sdb6)
Linux Mint 18 Sarah (18) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-34-generic (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-34-generic (upstart) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-34-generic (recovery mode) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-21-generic (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-21-generic (upstart) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 4.4.0-21-generic (recovery mode) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 3.16.0-38-generic (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 3.16.0-38-generic (upstart) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 3.16.0-38-generic (recovery mode) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 3.13.0-24-generic (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 3.13.0-24-generic (upstart) (on /dev/sdh9)
Linux Mint 18 Xfce 64-bit, with Linux 3.13.0-24-generic (recovery mode) (on /dev/sdh9)
Windows 7 (on /dev/sdj1)
Linux Mint 18.3 Sylvia (18.3) (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.4.0-34-generic (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.4.0-34-generic (upstart) (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.4.0-34-generic (recovery mode) (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.4.0-21-generic (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.4.0-21-generic (upstart) (on /dev/sdj5)
Linux Mint 18.3 Xfce 64-bit, with Linux 4.4.0-21-generic (recovery mode) (on /dev/sdj5)


```

the ubuntu entries are on sdj11 (sumsung ssd)
at foot of Grub Menu (I'll try to post photo)

changed to Xubuntu 17.10 6 months(?) ago
(previous Linux Mint boot was on sdj5)

At least I've got a working system (if not a current kernel)
thanks for suggestions

---

### Post by deadflowr on 2018-05-07
Single boot or multi/dual-boot?

EDIT: yes, multi-boot.
I see that now(posts came in at same time)

You would need to run grub-install so that the version you want controls grub.

---

### Post by iains on 2018-05-07
Thanks deadflowr (and everyone. else).

ran sudo grub-install /dev/sdj and it now has 4.15.18 kernel.

Learned a lot today
thanks

---

