---
title: "The volume 'Boot&quot; has only 0 bites disk space remaining error message."
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by drhans2 on 2014-10-17
I have Ubuntu 14.04 LTS installed on a HP Pavilion DV7 laptop. I keep getting a error message stating that my boot partition is full. This laptop has 2 Hard drives, sda is Ubuntu & sdb is Windows7. When trying to update Ubuntu or exiting Ubuntu the error message is "The volume boot has 0 bytes disk space remaining". The error message suggestion is to empty my trash and remove temporary packages of former installations using 'sudo apt-get clean'. I emptied my trash but am clueless about how to do the second instruction. I included a screenshot of the error message and of my sda partitions. I did search the forum for like problems and found one but that only reinforced my admitted limited experience using this OS.    [ATTACH=CONFIG]257299[/ATTACH]  much thanks in advance..

---

### Post by ajgreeny on 2014-10-17
Can you please show the output of ```
ls /boot/ | grep vmlinuz
``` which will show all the kernels you have installed on the machine.  Also try running ```
sudo apt-get autoremove
``` which often gets rid of all but the last two kernels.

Incidentally, why do you have a separate /boot partition?  Do you use LVM or encryption?  If not, you don't need a separate /boot, and it often causes the problem you have seen here.

---

### Post by drhans2 on 2014-10-17
Thanks for the reply.. If I did this correct... here's the output file of both commands..

denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ ls /boot/ | grep vmlinuz
vmlinuz-3.11.0-13-generic
vmlinuz-3.11.0-14-generic
vmlinuz-3.11.0-15-generic
vmlinuz-3.11.0-17-generic
vmlinuz-3.11.0-18-generic
vmlinuz-3.11.0-19-generic
vmlinuz-3.11.0-20-generic
vmlinuz-3.11.0-24-generic
vmlinuz-3.13.0-30-generic
vmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-34-generic
vmlinuz-3.13.0-35-generic
vmlinuz-3.5.0-17-generic
vmlinuz-3.5.0-18-generic
vmlinuz-3.5.0-21-generic
vmlinuz-3.5.0-27-generic
vmlinuz-3.8.0-26-generic

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`

```
denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get autoremove
[sudo] password for denny:
Sorry, try again.
[sudo] password for denny:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libboost-system1.53.0 libcolamd2.7.1 libdns99 libebackend-1.2-6
  libedata-book-1.2-17 libedata-cal-1.2-20 libfftw3-3 libfftw3-long3
  libgweather-3-3 libhud-client2 libllvm3.3 libpoppler43 libqt53d5
  libqt5location5 librhythmbox-core7 libwebp4 libx264-123
  linux-headers-3.11.0-13 linux-headers-3.11.0-13-generic
  linux-headers-3.13.0-30 linux-headers-3.13.0-30-generic
  linux-image-3.11.0-13-generic linux-image-3.13.0-30-generic
  linux-image-extra-3.11.0-13-generic linux-image-extra-3.13.0-30-generic
0 upgraded, 0 newly installed, 25 to remove and 116 not upgraded.
6 not fully installed or removed.
After this operation, 472 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 569129 files and directories currently installed.)
Removing libboost-system1.53.0:i386 (1.53.0-6+exp3ubuntu8) ...
Removing libcolamd2.7.1 (1:3.4.0-3ubuntu1) ...
Removing libdns99 (1:9.9.3.dfsg.P2-4ubuntu1.1) ...
Removing libedata-book-1.2-17 (3.8.5-1ubuntu3) ...
Removing libedata-cal-1.2-20 (3.8.5-1ubuntu3) ...
Removing libebackend-1.2-6 (3.8.5-1ubuntu3) ...
Removing libfftw3-3:i386 (3.3.3-7ubuntu3) ...
Removing libfftw3-long3:i386 (3.3.3-7ubuntu3) ...
Removing libgweather-3-3 (3.8.2-0ubuntu1) ...
Removing libhud-client2:i386 (14.04+14.04.20140604-0ubuntu1) ...
Removing libllvm3.3:i386 (1:3.3-16ubuntu1) ...
Removing libpoppler43:i386 (0.24.1-0ubuntu1) ...
Removing libqt5location5:i386 (5.2.1-1ubuntu2) ...
Removing libqt53d5:i386 (5.0~git20130731-0ubuntu5) ...
Removing librhythmbox-core7 (2.99.1-0ubuntu1) ...
Removing libwebp4:i386 (0.3.0-3) ...
Removing libx264-123:i386 (2:0.123.2189+git35cf912-1ubuntu1.1) ...
Removing linux-headers-3.11.0-13-generic (3.11.0-13.20) ...
Removing linux-headers-3.11.0-13 (3.11.0-13.20) ...
Removing linux-headers-3.13.0-30-generic (3.13.0-30.55) ...
Removing linux-headers-3.13.0-30 (3.13.0-30.55) ...
Removing linux-image-extra-3.11.0-13-generic (3.11.0-13.20) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done
Removing linux-image-3.11.0-13-generic (3.11.0-13.20) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done
Removing linux-image-extra-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done
Removing linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done
Setting up linux-image-generic (3.13.0.35.42) ...
Setting up linux-generic (3.13.0.35.42) ...
Setting up linux-generic-pae (3.13.0.35.42) ...
Setting up linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ 
```

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`

As to why I have a separate boot partition.. I don't know the reason..When I installed Ubuntu a few years ago I remember reading a forum post that I should create 5 separate partitions so the OS files could be installed in it's own partition swap & home doing the same.  Doing so would make update and changes easier or so I understood at the time.  I also did not want my Windows OS or files mixing with Ubuntu.  I removed my Windows HD from the laptop and installed a separate HD with 5 partitions and installed Ubuntu on it. When I added back the Windows HD I was then able to choose which OS I wanted at boot time. All worked great until this error message appeared.. (the laptop supports 2 Hard Drives). 

I rebooted the laptop after running the commands you mentioned and checked for updates and got the same message not enough space to install the updates. The update is 201.3 MB.. I checked G-Parted and now have 70.83 mb Unused space in sda1. If I installed incorrectly the 1st time how would I now correct?

---

### Post by nerdtron on 2014-10-17
I think you system is installed correctly. But next time it would be easier for you to manage if you just use two partitions when installing Ubunutu. The minimum requirement is one / partition where the OS (and everything Ubuntu) resides and another partition for swap.
Your way of installing Ubuntu safely by removing the hard drive with windows in it is a good thing since it will eliminate possibly erasing your windows partitions on when you install Ubuntu.

Anyway, your problem is common when /boot is on a separate partition and install kernel updates. Usually the /boot partition is small and updates on kernels do not remove the old ones so you end up using all the space on /boot.

How's the output of "df -Th" now? Did you free up space?

---

### Post by drhans2 on 2014-10-17
Thanks for the reinsurance on my install.. as for the output of "df-Th".... Can you be more instructive as to how to find out what you want?  Like I say earlier.. getting around inside the Linux OS is my downfall..

---

### Post by Impavidus on 2014-10-17
The partitioning of your system is not optimal, but changing it later is complicated and usually not worth the effort.

You just removed 2 old kernels and now have 70MB free space, so it gave a little room to breathe, but not much. You had 17 kernels, you uninstalled 2, so you still have 15 kernels, most of which belong to older releases of Ubuntu. We usually recommend to keep 2 kernels, so there is a lot left to be cleaned up.

You can uninstall all packages beginning with **linux-image** or **linux-headers** with one of these version numbers in their name:```
3.11.0-13
3.11.0-14
3.11.0-15
3.11.0-17
3.11.0-18
3.11.0-19
3.11.0-20
3.11.0-24
3.5.0-17
3.5.0-18
3.5.0-21
3.5.0-27
3.8.0-26
```Use whatever tool you like. Synaptic is the best, but even the software centre can get the job done.

This will get rid of all kernels (and headers) belonging to old versions of Ubuntu. It should give you enough space to install your updates. Then you can clean the old kernels of 14.04.

As for that command nerdtron suggests, just type```
df -Th
```in the terminal and hit enter. Mind the space between the f and the -.

---

### Post by drhans2 on 2014-10-17
Here's the output of the df -Th command..

denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda5      ext4      9.1G  6.8G  1.8G  80% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  4.0G  4.0K  4.0G   1% /dev
tmpfs          tmpfs     804M  1.2M  803M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     4.0G   76K  4.0G   1% /run/shm
none           tmpfs     100M   52K  100M   1% /run/user
/dev/sda6      ext4       74G  931M   69G   2% /home
/dev/sda1      ext4      453M  383M   44M  90% /boot
denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I found the app Synaptic and loaded it but using it questionable as I don't understand it's operation.. I looked in the left hand column for the /dev/sda1 boot partition but no joy. I did find some of the files in question under "Kernel and modules" they were marked status.. green along with other files that are not in question. I didn't feel comfortable choosing uninstall as many other listing were also marked green.. Is there a command line option for uninstalling the files in question.. Could I just delete the files in that boot partition? 
Thanks again for the help.

---

### Post by Impavidus on 2014-10-18
Don't simply delete files from your boot partition. It will give you a messy system.

Both your /boot and your root partition are quite, although not completely, full. The root partition is quite small too, but there's little to do about that. Uninstalling old kernel and header packages helps to create more free space in both, and you have many old kernels and possibly old headers. They get installed in the same way and as you didn't uninstall old kernels, I assume you didn't uninstall old headers either.

Synaptic is a package manager (or rather, one of the front-ends to it). It doesn't list partitions and it doesn't list files, but it lists packages in several categories. Most software in Linux is distributed in packages, containing files that have to be installed in various directories, along with install and uninstall scripts and lists of dependencies. The package manager keeps track of where all files belonging to a package have been installed. This is the reason why you shouldn't simply delete files from /boot, without involving the package manager.

In synaptic, click "status" on the lower left. Above that, click "installed". That will list all your installed packages. Then type either linux-image or linux-headers in the search box. The boxes in synaptic indicate current status, not wether it's safe to uninstall them. You should decide that yourself. You can right click and select purge. Synaptic may notify you that it has to uninstall additional packages. If these additional packages are also on the list I suggested to uninstall, proceed. Else, which would be unlikely, cancel. If you have more old header packages, you can uninstall them too.

We could provide you with a terminal command that will uninstall all old stuff, but I don't think that would help you understand what is going on. Anyway, we'd need some more information for that, like a list with the exact package names you have installed. You can get that list with```
dpkg --list "linux-image*" "linux-headers*"
```You may have to maximise your terminal before running this command, as the output can be rather wide.

---

### Post by drhans2 on 2014-10-18
Thanks so much for the play by play instructions using Synaptic.. I followed your lead and removed everything mentioned in post # 6 (minus the reference to 14.04). Here is the end result..
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`

Here's the results of using "search' in Synaptic.... (I think, however it might be the results of something else)

Found Windows Recovery Environment (loader) on /dev/sdb3
done
Removing linux-image-3.8.0-26-generic (3.8.0-26.38) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Windows Recovery Environment (loader) on /dev/sdb2
Found Windows Recovery Environment (loader) on /dev/sdb3
done

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here's the results of..... df -Th  (After removing older packages in Synaptic..)

denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda5      ext4      9.1G  5.3G  3.3G  62% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  4.0G   12K  4.0G   1% /dev
tmpfs          tmpfs     804M  1.2M  803M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     4.0G   80K  4.0G   1% /run/shm
none           tmpfs     100M   44K  100M   1% /run/user
/dev/sda1      ext4      453M   92M  335M  22% /boot
/dev/sda6      ext4       74G  929M   69G   2% /home
denny@denny-HP-Pavilion-dv7-Notebook-PC:~$


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Here's the results of.... dpkg --list "linux-image*" "linux-headers*" (After removing older packages in Synaptic..)



denny@denny-HP-Pavilion-dv7-Notebook-PC:~$ dpkg --list "linux-image*" "linux-headers*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version Architecture            Description
+++-====================================-=======================-=======================-==============================================================================
un  linux-headers <none>                  <none>                  (no description available)
un  linux-headers-3 <none>                  <none>                  (no description available)
un  linux-headers-3.0 <none>                  <none>                  (no description available)
un  linux-headers-3.11.0-13-generic <none>                  <none>                  (no description available)
ii  linux-headers-3.11.0-14              3.11.0-14.21 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-14-generic      3.11.0-14.21 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-15              3.11.0-15.25 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-15-generic      3.11.0-15.25 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-17              3.11.0-17.31 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-17-generic      3.11.0-17.31 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-18              3.11.0-18.32 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-18-generic      3.11.0-18.32 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-19              3.11.0-19.33 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-19-generic      3.11.0-19.33 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-20              3.11.0-20.35 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-20-generic      3.11.0-20.35 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-24              3.11.0-24.42 all                     Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-24-generic      3.11.0-24.42 i386                    Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
un  linux-headers-3.13.0-30-generic <none>                  <none>                  (no description available)
ii  linux-headers-3.13.0-32              3.13.0-32.57 all                     Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic      3.13.0-32.57 i386                    Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-34              3.13.0-34.60 all                     Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic      3.13.0-34.60 i386                    Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35              3.13.0-35.62 all                     Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic      3.13.0-35.62 i386                    Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-18               3.5.0-18.29 all                     Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-18-generic       3.5.0-18.29 i386                    Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-27               3.5.0-27.46 all                     Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-27-generic       3.5.0-27.46 i386                    Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
un  linux-headers-3.8.0-19-generic <none>                  <none>                  (no description available)
un  linux-headers-3.8.0-23-generic <none>                  <none>                  (no description available)
un  linux-headers-3.8.0-26-generic <none>                  <none>                  (no description available)
ii  linux-headers-generic                3.13.0.35.42 i386                    Generic Linux kernel headers
ii  linux-headers-generic-pae            3.13.0.35.42 i386                    Transitional package
un  linux-image <none>                  <none>                  (no description available)
un  linux-image-3.0 <none>                  <none>                  (no description available)
rc  linux-image-3.11.0-13-generic        3.11.0-13.20 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-14-generic        3.11.0-14.21 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-15-generic        3.11.0-15.25 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-17-generic        3.11.0-17.31 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-18-generic        3.11.0-18.32 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-19-generic        3.11.0-19.33 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-20-generic        3.11.0-20.35 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.11.0-24-generic        3.11.0-24.42 i386                    Linux kernel image for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-3.13.0-30-generic        3.13.0-30.55 i386                    Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic        3.13.0-32.57 i386                    Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic        3.13.0-34.60 i386                    Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic        3.13.0-35.62 i386                    Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.5.0-17-generic         3.5.0-17.28 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.5.0-18-generic         3.5.0-18.29 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.5.0-21-generic         3.5.0-21.32 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.5.0-27-generic         3.5.0-27.46 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-19-generic         3.8.0-19.30 i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-23-generic         3.8.0-23.34 i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-26-generic         3.8.0-26.38 i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-13-generic  3.11.0-13.20 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-14-generic  3.11.0-14.21 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-15-generic  3.11.0-15.25 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-17-generic  3.11.0-17.31 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-18-generic  3.11.0-18.32 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic  3.11.0-19.33 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic  3.11.0-20.35 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-24-generic  3.11.0-24.42 i386                    Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic  3.13.0-30.55 i386                    Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic  3.13.0-32.57 i386                    Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic  3.13.0-34.60 i386                    Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic  3.13.0-35.62 i386                    Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.5.0-17-generic   3.5.0-17.28 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.5.0-18-generic   3.5.0-18.29 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.5.0-21-generic   3.5.0-21.32 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.5.0-27-generic   3.5.0-27.46 i386                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-19-generic   3.8.0-19.30 i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-23-generic   3.8.0-23.34 i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-26-generic   3.8.0-26.38 i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                  3.13.0.35.42 i386                    Generic Linux kernel image
denny@denny-HP-Pavilion-dv7-Notebook-PC:~$
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I then rebooted and then ran the "Software Updater".. it said 201MB will be downloaded. I hit "Install now" but nothing is happening. I retried and got the same results. The version I have is 14.04 LTS. I also tried using the "Install Updates vie the Ubuntu "Details" screen, same results.. Seems I can't install any Ubuntu Updates now..

---

### Post by ajgreeny on 2014-10-18
This command which is found in the thread at [http://ubuntuforums.org/showthread.php?t=2245790&p=13129519#post13129519](http://ubuntuforums.org/showthread.php?t=2245790&p=13129519#post13129519) should be able to remove all old kernels except the two most recent ones.
```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```

I have never used it, and to be honest I don't have the knowledge of "sed" to understand fully what it all means, though I think stickymaster can be trusted with these things.
Worth trying I think, though it may be better to always be aware of how many kernels there are on your system, and remove all except the last two.

---

### Post by ian-weisser on 2014-10-18
> **drhans2 said:**
> Thanks so much for the play by play instructions using Synaptic.. 

/dev/sda1      ext4      453M   92M  335M  22% /boot

Congratulations.
That looks a lot healthier.

Keep the instructions handy. You may need to do it again in a few months.


> **drhans2 said:**
> I then rebooted and then ran the "Software Updater".. it said 201MB will  be downloaded. I hit "Install now" but nothing is happening.

Close Software Updater.
Close Synaptic.
Close all other package managers (like Software Center).
Don't just minimize them, really Quit out of them.
If something complains that quitting is a bad idea because it's sill working, LET IT FINISH working. You're not in a hurry.

Then open a terminal and try these two commands:
```
sudo apt-get update
sudo apt-get upgrade
```

If you get an error message, the post the complete output here. Er, do use code tags to keep the output readable.

---

### Post by drhans2 on 2014-10-20
Thanks again to all that helped.. 

Using a quote from Gomer Pyle U.S.M.C... Surprise, Surprise, Surprise... When I turn on the laptop today (Monday) it went thru the auto update and from what I can tell its now up to date.

 I didn't do anything except turn off the laptop on Saturday after it failed to do the update. I also didn't get to try the option mentioned in post #10. But now wonder if I should run it just to see if it will work as a "1st option fix" if and when the problem reappears? 

 Along that line... what is the preferred number of partitions and how should I name them if I was to install Ubuntu on a separate Hard Drive, and would that number be the same if installing Ubuntu on a computer with only 1 HD and with the Windows OS on C:\?

Can I, or should I repartition my Ubuntu 'sda' HD (Windows is on 'sdb') and reinstall Ubuntu to correct my first install which in all likelihood present my problem again?

Much thanks.. denny

---

### Post by nerdtron on 2014-10-20
> Along that line... what is the preferred number of partitions and how  should I name them if I was to install Ubuntu on a separate Hard Drive,  and would that number be the same if installing Ubuntu on a computer  with only 1 HD and with the Windows OS on C:\?

Can I, or should I repartition my Ubuntu 'sda' HD (Windows is on 'sdb')  and reinstall Ubuntu to correct my first install which in all likelihood  present my problem again?

Next time to prevent the fill up of your /boot, you can just install Linux in a single drive or partition. The minimum requirements for partition is a "/" partition to hold the whole OS and another partition for swap.

Then if you have a separated hard drive that you would like to use a D drive, then go ahead and use it as usual. Format the drive (either NTFS or ext4) and you can use in Ubuntu.

As for naming the drive, drives in Linux are really /dev/sdaX or /dev/sdbX which you can't pretty much do anything. If you want to change the names as they appear in the left pane on Nautilus, consider changing the "Label" of the drives. Follow here: [http://smallbusiness.chron.com/rename-hard-drive-gparted-ubuntu-50906.html](http://smallbusiness.chron.com/rename-hard-drive-gparted-ubuntu-50906.html)

---

### Post by Shoalster on 2014-10-20
If I may get in on this thread I would like to report that I had this same problem.  I ran the auto remove, then message said to restart but now computer will not boot. Just  white text on dark screen that includes call trace......and other .  Obviously can't send a screenshot but did capture an image with phone camera.  Am I screwed ?

---

### Post by drhans2 on 2014-10-21
I'm assuming that when you said you experienced your 'boot' problems you used the 'auto remove' terminal cmd reference mentioned in post  #10? 

Sorry to hear, but I'm at a loss as what to do.. except maybe do a fresh install?? 

However hearing that I will leave my laptop as is. The last thing I did was follow the instructions in post # 8 using the program Synaptic. 

I did experience a update hiccup but after restarting the laptop a day later all went well. 

Much thanks too all...

---

