---
title: "istallation from other linux"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by wtq4er on 2012-05-25
i have working gentoo and i'm trying to install ubuntu without cd and usb flash. im using ths guide [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) and i get all the time stupid message from live system that medium with live cd data not found. i also tried to use option LIVEMEDIA=/dev/sdb1 but still the same stupid error. 
i made all partitions and wrote into grub.conf all needed:
> title           installer 
root            (hd0,5) 
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw 
initrd          /casper/initrd.lz
 live cd start booting and then sticks on looking for medium with live cd lol
i haven't yet tried to use the alternative cd. 
the fact is that my pc can't boot from usb and cd rom always read with errors. 
thanks for any help.

---

### Post by wtq4er on 2012-05-25
OK, note3 that recommends to 
> simply use the boot option live-media=/dev/sdb1 or LIVEMEDIA=/dev/sdb1, referring to the usb device holding the ISO.actually works, but you should copy to usb not **ISO as **it's written there but **the content of ISO.** Those are different things i suppose. If anyone has access to edit this ([https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)) document, please correct there what i said above. 
I'm writing from ubuntu live environment now. And we'll see if there would be errors during installation.

---

### Post by wtq4er on 2012-05-25
allright here's new ****. i get this:
> &#1042;&#1086;&#1079;&#1085;&#1080;&#1082;&#1083;&#1072; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1072; &#1087;&#1088;&#1080; &#1082;&#1086;&#1087;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1080; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1085;&#1072; &#1078;&#1105;&#1089;&#1090;&#1082;&#1080;&#1081; &#1076;&#1080;&#1089;&#1082;:

[Errno 5] Input/output error

&#1069;&#1090;&#1086; &#1095;&#1072;&#1089;&#1090;&#1086; &#1087;&#1088;&#1086;&#1080;&#1089;&#1093;&#1086;&#1076;&#1080;&#1090; &#1080;&#1079;-&#1079;&#1072; &#1085;&#1077;&#1080;&#1089;&#1087;&#1088;&#1072;&#1074;&#1085;&#1086;&#1089;&#1090;&#1080; CD/DVD &#1076;&#1080;&#1089;&#1082;&#1072;, &#1087;&#1088;&#1080;&#1074;&#1086;&#1076;&#1072;, &#1080;&#1083;&#1080; &#1078;&#1105;&#1089;&#1090;&#1082;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1072;. &#1042;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1087;&#1086;&#1084;&#1086;&#1078;&#1077;&#1090; &#1086;&#1095;&#1080;&#1089;&#1090;&#1082;&#1072; CD/DVD &#1076;&#1080;&#1089;&#1082;&#1072;, &#1083;&#1080;&#1073;&#1086; &#1079;&#1072;&#1087;&#1080;&#1089;&#1100; CD/DVD &#1085;&#1072; &#1073;&#1086;&#1083;&#1077;&#1077; &#1085;&#1080;&#1079;&#1082;&#1086;&#1081; &#1089;&#1082;&#1086;&#1088;&#1086;&#1089;&#1090;&#1080;, &#1083;&#1080;&#1073;&#1086; &#1086;&#1095;&#1080;&#1089;&#1090;&#1082;&#1072; &#1083;&#1080;&#1085;&#1079; CD/DVD &#1087;&#1088;&#1080;&#1074;&#1086;&#1076;&#1072; (&#1089;&#1086;&#1086;&#1090;&#1074;&#1077;&#1090;&#1089;&#1090;&#1074;&#1091;&#1102;&#1097;&#1080;&#1077; &#1082;&#1086;&#1084;&#1087;&#1083;&#1077;&#1082;&#1090;&#1099; &#1076;&#1083;&#1103; &#1086;&#1095;&#1080;&#1089;&#1090;&#1082;&#1080; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1099; &#1074; &#1087;&#1088;&#1086;&#1076;&#1072;&#1078;&#1077;), &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1078;&#1105;&#1089;&#1090;&#1082;&#1080;&#1081; &#1076;&#1080;&#1089;&#1082; &#1091;&#1078;&#1077; &#1086;&#1095;&#1077;&#1085;&#1100; &#1089;&#1090;&#1072;&#1088;&#1099;&#1081; &#1080; &#1085;&#1091;&#1078;&#1076;&#1072;&#1077;&#1090;&#1089;&#1103; &#1074; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077;, &#1083;&#1080;&#1073;&#1086; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1087;&#1077;&#1088;&#1077;&#1084;&#1077;&#1089;&#1090;&#1080;&#1090;&#1100; &#1086;&#1073;&#1086;&#1088;&#1091;&#1076;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1074; &#1073;&#1086;&#1083;&#1077;&#1077; &#1087;&#1088;&#1086;&#1074;&#1077;&#1090;&#1088;&#1080;&#1074;&#1072;&#1077;&#1084;&#1086;&#1077; &#1084;&#1077;&#1089;&#1090;&#1086;.It says that i have bad CD/DVD lol. I tried both - install using flash as source of livecd contents and hdd partition as source( Yep, that is possible too, just need to put option  LIVEMEDIA=/dev/sda6 in my case) - in both cases same ****. What the hech is this? corrupt iso image? or some errors when using rsync /iso-mount/ /destination-device/

---

