---
title: "preseed.cfg problems with ubuntu 8.04.1 LTS i386"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by thesheff17 on 2008-09-08
Is anyone else installing ubuntu 8.04.1 LTS through preseed.cfg file?  I'm not sure if this was the case for ubunu 8.04 but now it wants to install a mysql server.  I would prefer it doesn't do this.  Anyway to remove this package?

Also I keep getting weird triangles at the command prompt when the system finally boots for the first time.  I swear I have the right keyboard layouts but something else is causing this.  Anyone have this happened to them before?

Any help will be greatly appreciated.

***I noticed that I had this in the file***
tasksel tasksel/first multiselect standard, lamp-server
and removing the lamp-server fixed the problem with mysql-server being installed.
Now just for the weird keyboard problem and I will be set.

~Dan

---

### Post by thesheff17 on 2008-09-08
I fixed everything by adding the below parameters to the kernel when it boots.  I read somewhere that the OS will figure out what country you are from and it may have been picking the wrong one the whole time.  It is in bold below.  Also attached is my new working preseed file.


LABEL auto
        kernel ubuntu-installer/i386/linux
        append ramdisk_size=14984 locale=en_US **console-setup/layoutcode=us** netcfg/wireless_wep= netcfg/choose_interface=eth0 netcfg/get_hostname=hostname url=http://192.168.0.2/preseed.cfg vga=normal initrd=ubuntu-installer/i386/initrd.gz --

---

### Post by NSharp on 2009-02-06
Hi there,

Im wondering if you could possibly point me in the direction of a decent how to on PXE installation of 8.04.

Ive got to the point where my preseed file is being pulled off of the server, I have a duplicated a mirror but no matter what I do my client always comes back with bad mirror

Regards

Nick Sharp

---

### Post by thesheff17 on 2010-05-05
Well I'm attempting to do this again with the new LTS.  I have a couple of problems already which I'm working on.  Sorry I wasn't watching this thread until now:

[https://www.digisoftinc.org/wiki/index.php/Ubuntu_preseed.cfg_installs_off_PXE_Boot](https://www.digisoftinc.org/wiki/index.php/Ubuntu_preseed.cfg_installs_off_PXE_Boot)

---

