---
title: "Cant install, boot loader problem I guess"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by zyHEpEJ on 2014-03-23
After hours of running from one error into another and another I am really frustrated right now. All I wanted was to install Ubuntu Server on my HP ProLiant MicroServer N54L, Turion II Neo N54L. So it all began with trying Ubuntu Server edition AMD64 13.10. Didnt even could boot into the whole setup, because it always hang at selecting language, and it is mostly this error: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176)

So.... I tried out Ubuntu 14.10, where the keyboard thing was fixed it seemed. Next big issue was it just stopped with an unspecific error after installing the packages, I ust selected base serer, openssh server, samba server and Ubuntu desktop, which like "there was an error installing the packages: [http://i.imgur.com/gUSH8Qq.gif](http://i.imgur.com/gUSH8Qq.gif) Log says:

So... I tried the non server version, this time network boot/installation. I used the mini iso for this: [http://www.fr.php.net/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso](http://www.fr.php.net/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso)

This time, all seemed well, no errors, and I came to the point installing grub. Just selected default options, install to master boot record, bla bla, and then error, cant install grub, there was an error, bla bla bla. So I tried lilo, which seemed to run through without any problems, and I finished installation, rebooted, aaaand now this: [http://i.imgur.com/5owtKSR.jpg](http://i.imgur.com/5owtKSR.jpg)

I think it relays on that during the installation, the usb stick from where I am installing is /dev/sda, and the hdd sdb, but during normal boot (with usb stick removed), it changes from sdb to sda?

Another try, rebooted, partitioned, selected software same as before (where it worked), aaand ran into the "something went wrong" error again during software installation, log says:

Mar 23 16:01:35 in-target: Fehler traten auf beim Bearbeiten von:
Mar 23 16:01:35 in-target:  python3-plainbox
Mar 23 16:01:35 in-target:  python3-checkbox-ng
Mar 23 16:01:35 in-target:  checkbox-ng
Mar 23 16:01:35 in-target:  checkbox-ng-service
Mar 23 16:01:35 in-target:  checkbox-gui
Mar 23 16:01:35 in-target:  ubuntu-desktop

Sooooo... rebooted, repart, bla bla bla, again, didnt select ubuntu-desktop (just base, openssh, samba), installed, bla bla bla, and now I am at instaling boot manager again and grub2 fails, and I am still in the menu... What should I do now...

---

### Post by michael127 on 2014-03-23
There is some software that you can use to fix your Grub installation known as Boot-Repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) which has instructions of how to run the Boot-Repair. I hope this helps

---

