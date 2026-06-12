---
title: "Install vanilla kernel to other Ubuntu server"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by dolphs on 2010-06-13
Hi - I am trying to compile a new vanilla kernel on to my Ubuntu server system which has been freshly installed with Ubuntu 10.04 server 32bits. As this will run on a VIA epia-px5000eg mainboard with USB stick I want compile this kernel on a different machine on which is also ubuntu 10.04 installed. Unfortunately currently I experience difficulties when I boot kernel 2.6.34; it says "Kernel panic - not syncing: VFS: unable to mount root fs on unknown block" while if I load to original kernel that comes with Ubuntu 10.04 all works perfectly well. BTW reason I want to build a custom vanilla kernel is to trim down kernel to the necessary services I need as I am running a server that requires just the essentials. And it needs to support the VIA Epia CPU processor family ( C3, C7 or generic setting which is another hurdle which I won't discuss here ). 

Hopefully one out there is able to guide me further as I type step by step what I executed. Thanks for your replies in advance:

Yet I hook up the VIA epia-px5000g with 2gb usb stick, a dvd drive and keyboard ( all usb ). Boot from CDrom and install a minimal system (<f4>) to usb stick. Partitioning part I set it to EXT4 and used full size thus no SWAP. Also mount option " noatime " has been set all to save writes to usb stick.
When the base system has been installed a user has been added, as well apt is being configured to install only security updates automatically. As services I want to run definitely openSSH-server so I can access remotely. Grub gets configured and system will be rebooted.

At this stage I configure the network interface to a static address so I do not need to check my router all the time which dhcp address Ubuntu is using if I want to access remotely.

Now the compile part starts, the ubuntu way. I log in to my other system and execute following commands accordingly:

sudu su, apt-get update, apt-get install kenel-package libncurses5-dev fakeroot

cd /usr/src
wget -P . [http://[kernel.org](http://[kernel.org) to bz2 image from latest 2.6.34 kernel]
tar xvjf bz2-image
ln -s linux-2.6.34 linux
cd /usr/src/linux

scp user@ubuntu-server-host:/boot/config-* ./.config

make menuconfig
[L]oad and Alternate Configuration File
.config

< adjust kernel setting to processor Family VIA-C3 and remove Amateur Radio Support fully - just to start "if all works as expected" >

make-kpkg clean
fakeroot make-kpkg --initrd -append-to-version=-viac3 kernel_image kernel_headers

While compiling log in to destination:

ssh user@ubuntu-server-host
sudo su
cd /usr/src ( which is totally empty at this stage )
wget -P . [http://[kernel.org](http://[kernel.org) to bz2 image from latest 2.6.34 kernel]
tar xvjf bz2-image
ln -s linux-2.6.34 linux
cd /usr/src/linux

Back to system which is compiling:
cd /usr/src
scp *.deb user@ubuntu-server-host:/tmp

mv /tmp/*.deb . ( linux-headers-2.6.34-*.deb and linux-image-2.6.34*.deb )
chown root:src *.deb

dpkg -i linux-image*

Running depmod.
Examining /etc/kernel/postinst.d.
Running postinst hook script update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.34-viac3
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done


dpkg -i linux-headers*
Selecting previously deselected package linux-headers-2.6.34-viac3.
(Reading database ... 23432 files and directories currently installed.)
Unpacking linux-headers-2.6.34-viac3 (from linux-headers-2.6.34-viac3_2.6.34-viac3-10.00.Custom_i386.deb) ...
Setting up linux-headers-2.6.34-viac3 (2.6.34-viac3-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.


This all looks fine now, however on booting the kernel this message appears:

longhaul: APIC detected. Longhaul is currently broken in this configuration
kernel panic - not syncing: VFS: unable to mount root fs on unknown block


-update-
based on happyhamster's post I managed to compile succesfully!
So additional steps taken.

on source machine, just after compilation
cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/ ( directory did not exist but created )

on destination machine, just after dpkg execute these steps:
update-initramfs -c -k 2.6.43-viac3
grub-mkconfig
update-grub

Yet I managed to boot in my vanilla kernel, thanks for your help!

---

### Post by happyhamster on 2010-06-13
Go here (post 1447 and several more onward):
[http://ubuntuforums.org/showthread.php?t=311158&page=145](http://ubuntuforums.org/showthread.php?t=311158&page=145)

For me, the link from master_kernel from post 1450 fixed the problem:
[http://linuxagora.com/vbforum/showthread.php?t=1126](http://linuxagora.com/vbforum/showthread.php?t=1126)

```

cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/

```
And then recompile. Good luck.

BTW. Warning: take care when copying&pasting the code from that page: the webpage software inserted a space in both lines (just before "initramfs"). Get rid of those space characters first. Good luck.

---

### Post by dolphs on 2010-06-14
Cheers for pointing out to these posts will check soon!

---

