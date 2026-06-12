---
title: "Znowu Initramfs problem? cannot install Kernel 4.10.1 or upper"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by dj--alex on 2017-03-14
I have created for /me ubuntu 16.04.1 image and computer with this system
Installed - minimum components - wine, vlc , audacious, gimp, audacity
System updated to Kernel 4.9.4 from mainline.   

AMD FX 8100/ 8GB ram/ GTX780/ 128Gb ssd / 2Tb HDD
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10.1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10.1/)   kernel taken here


I DONT use on system Proprietary Nvidia or AMD drivers , only Mesa

I backup image system after installing with Systemback tool (great thanks to it's authors!! it save me much time!!!) 
I can do everything with this system to test how to install new kernel without any harm.
in any time i can rollback to normal state.

All works normal until i prepare from mainline  .deb files kernel
and run in command  dpkg -i *.deb 

```

user@ubuntu:~$ cd kernel4.10.2/
user@ubuntu:~/kernel4.10.2$ sh 0install.sh 
&#1042;&#1099;&#1073;&#1086;&#1088; &#1088;&#1072;&#1085;&#1077;&#1077; &#1085;&#1077; &#1074;&#1099;&#1073;&#1088;&#1072;&#1085;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; linux-headers-4.10.2-041002-generic.
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; &#8230; &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 173959 &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;.)
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1088;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1082;&#1077; linux-headers-4.10.2-041002-generic_4.10.2-041002.201703120131_amd64.deb &#8230;
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; linux-headers-4.10.2-041002-generic (4.10.2-041002.201703120131) &#8230;
&#1042;&#1099;&#1073;&#1086;&#1088; &#1088;&#1072;&#1085;&#1077;&#1077; &#1085;&#1077; &#1074;&#1099;&#1073;&#1088;&#1072;&#1085;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; linux-headers-4.10.2-041002.
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1088;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1082;&#1077; linux-headers-4.10.2-041002_4.10.2-041002.201703120131_all.deb &#8230;
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; linux-headers-4.10.2-041002 (4.10.2-041002.201703120131) &#8230;
&#1042;&#1099;&#1073;&#1086;&#1088; &#1088;&#1072;&#1085;&#1077;&#1077; &#1085;&#1077; &#1074;&#1099;&#1073;&#1088;&#1072;&#1085;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; linux-image-4.10.2-041002-generic.
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1088;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1082;&#1077; linux-image-4.10.2-041002-generic_4.10.2-041002.201703120131_amd64.deb &#8230;
Done.
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; linux-image-4.10.2-041002-generic (4.10.2-041002.201703120131) &#8230;
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; linux-headers-4.10.2-041002 (4.10.2-041002.201703120131) &#8230;
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; linux-image-4.10.2-041002-generic (4.10.2-041002.201703120131) &#8230;
Running depmod.
sh: 1: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; linux-image-4.10.2-041002-generic (--install):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 2
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; linux-headers-4.10.2-041002-generic (4.10.2-041002.201703120131) &#8230;
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.2-041002-generic /boot/vmlinuz-4.10.2-041002-generic
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 linux-image-4.10.2-041002-generic
user@ubuntu:~/kernel4.10.2$ 

```

I don't know how to fix it and normally install Kernel .
On MX-Linux 16 and Mint 18.1 4.10.2 installed OK without errors.

I tries install after failing install kernel  - install  initramfs update from Synaptic but update fails 
Other software normally installs and removes.

I need this kernel to continue work. Some devices works faster with it.

I Uploaded this bugged ISO   (in russian language ) 
If anyone wants i give link to it.

---

### Post by dj--alex on 2017-03-15
All versions of image  i created - have 4.9.4 kernel  and have this bug no allowed install any another kernel.
maybe kernel 4.9.4 not best select for system?

I try commands from another user before installation kernel etc.  
1.reinstall initramfs-tools
2.install kernel 4.10.1
3.get error

This is useless commands for me
```

You can try the following command to see if it's already installed:

  sudo dpkg -l |grep initramfs-tools
  If it isn't installed yet, you can try the following command:
  sudo apt-get install initramfs-tools
  If it says that it's already installed you could try the following:
  sudo apt-get install --reinstall initramfs-tools

```

Screenshot
[https://pp.userapi.com/c639721/v639721257/d8d2/Aj9XF8gf3SE.jpg](https://pp.userapi.com/c639721/v639721257/d8d2/Aj9XF8gf3SE.jpg)

Backup of system is here is anyone want to check it in virtualbox.
[https://yadi.sk/d/riBzXQIS3FtYdY]("https://vk.com/away.php?to=https%3A%2F%2Fyadi.sk%2Fd%2FriBzXQIS3FtYdY")
Terminal can be called Ctrl-Alt-t

---

