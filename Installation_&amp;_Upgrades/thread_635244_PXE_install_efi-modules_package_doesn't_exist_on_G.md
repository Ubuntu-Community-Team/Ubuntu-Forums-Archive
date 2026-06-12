---
title: "PXE install efi-modules: package doesn't exist on Gutsy 7.10"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by miksmi on 2007-12-08
When installing 7.10 Gutsy Gibbon with either Xubuntu Alternate Install or Ubuntu Server Edition, I get this error on the target machine:

Dec  8 19:19:15 anna[6377]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Dec  8 19:19:18 anna[6377]: wget: server returned error 404: HTTP/1.1 404 Not Found

The installer correctly detects the target hardware; I specify the Ubuntu mirror archive (a local HTTP server), the installer runs for about 30 seconds, then displays the error.

On the Apache server, I get HTTP error 404. The installer tries to wget 
e2fsprogs-udeb_1.40.2-1ubuntu1.1_i386.udeb 
but the file on the Apache server (copied from the iso) is:
e2fsprogs-udeb_1.40.2-1ubuntu1_i386.udeb 
(asks for version 1.1 but version 1 is on disk). I copied the files from the CD images:

xubuntu-7.10-alternate-i386.iso
ubuntu-7.10-alternate-i386.iso

Target hardware: Dell Dimension XPS D300, Pentium II 300MHz, 256MB RAM, 1 EIDE, 2 SCSI disks, Intel PRO/100B NIC IP: 192.168.0.204

192.168.0.204 (Dell) syslog:

Dec  8 19:19:15 anna[6377]: DEBUG: install nic-restricted-modules-2.6.22-14-generic-di, priority >= standard 
Dec  8 19:19:15 anna[6377]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Dec  8 19:19:15 anna[6377]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec  8 19:19:15 anna[6377]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec  8 19:19:15 anna[6377]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Dec  8 19:19:18 anna[6377]: wget: server returned error 404: HTTP/1.1 404 Not Found^
Dec  8 19:19:18 anna[6377]: WARNING **: package retrieval failed 
Dec  8 19:21:00 main-menu[2839]: WARNING **: Configuring 'download-installer' failed with error code 6 
Dec  8 19:21:00 main-menu[2839]: WARNING **: Menu item 'download-installer' failed. 
Dec  8 19:21:01 main-menu[2839]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Dec  8 19:21:01 debconf: Setting debconf/priority to medium
Dec  8 19:21:01 main-menu[2839]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec  8 19:21:01 main-menu[2839]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec  8 19:21:01 main-menu[2839]: DEBUG: resolver (os-prober): package doesn't exist (ignored) 
Dec  8 19:21:01 main-menu[2839]: DEBUG: resolver (tzsetup-udeb): package doesn't exist (ignored) 
Dec  8 19:21:01 main-menu[2839]: DEBUG: resolver (mounted-partitions): package doesn't exist (ignored) 
Dec  8 19:21:01 main-menu[2839]: DEBUG: resolver (created-fstab): package doesn't exist (ignored)

HTTP server's /var/log/apache2/access.log:

192.168.0.204 - - [08/Dec/2007:14:21:11 -0500] "GET /ubuntu/xalt/pool/main/d/devmapper/dmsetup-udeb_1.02.20-1ubuntu4_i386.udeb HTTP/1.1" 200 17634 "-" "Wget"
192.168.0.204 - - [08/Dec/2007:14:21:12 -0500] "GET /ubuntu/xalt/pool/main/d/devmapper/libdevmapper1.02.1-udeb_1.02.20-1ubuntu4_i386.udeb HTTP/1.1" 200 34110 "-" "Wget"
192.168.0.204 - - [08/Dec/2007:14:21:12 -0500] "GET /ubuntu/xalt/pool/main/e/e2fsprogs/e2fsprogs-udeb_1.40.2-1ubuntu1.1_i386.udeb HTTP/1.1" 404 346 "-" "Wget"

It seems there is corrupt list of files to wget but I'm unsure which configuration file contains this info. I grep'ed for the missing file and came up empty.

I searched for relavant threads before posting.

Any suggestions?

Thanks in advance.

---

### Post by erdinger on 2007-12-11
The same problem here...

Curious that this problem is since two days and I had no problem before that day. For testing I installed Ubuntu about 50 times before and I didn't shut down my installation server that night and I didn't changed anything...

I tried to make a ln -s and I tried to just change the name of the file but he always is angry about the md5 checksum :evil:

do you know how to create a new md5sum for that?

=============================================================
there is a e2fsprogs-udeb_1.40.2-1ubuntu1_i386.udeb 
but no e2fsprogs-udeb_1.40.2-1ubuntu1**[COLOR=SandyBrown].1[/COLOR]**_i386.udeb

---

### Post by miksmi on 2007-12-12
It appears the Xubuntu 7.10 Gutsy Gibbon .iso is missing three files. Solution:
```

cd <Xubuntu 7.10 directory>/pool/main/e/e2fsprogs
sudo wget http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs-udeb_1.40.2-1ubuntu1.1_i386.udeb
sudo wget http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1-udeb_1.40.2-1ubuntu1.1_i386.udeb
sudo wget http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1-udeb_1.40.2-1ubuntu1.1_i386.udeb

```
Hope this helps.

---

### Post by erdinger on 2007-12-12
Works for me... Thank you

funny that is worked the days before. but perhaps i did something wrong there.

---

### Post by erdinger on 2007-12-23
during installation of a laptop i additionally needed the following files:

```
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/acpi-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/block-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/cdrom-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/crypto-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/fat-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/fb-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/firewire-core-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/floppy-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/fs-core-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/ide-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/input-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/ipv6-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/irda-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/md-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/message-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/nfs-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/nic-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/nic-pcmcia-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/nic-shared-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/nic-usb-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/parport-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/pata-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/pcmcia-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/pcmcia-storage-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/plip-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/ppp-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/sata-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/scsi-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/serial-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/socket-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/storage-core-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/usb-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb
```
is that a fault of the server cd or is it mine?
under [http://archive.ubuntu.com/](http://archive.ubuntu.com/) there are all files, but i don't have enough disk space to make a whole copy of that... what can i do?

---

### Post by miksmi on 2007-12-24
> **erdinger said:**
> 
is that a fault of the server cd or is it mine?

I'm no expert but I think the server CD is missing files.
> **erdinger said:**
> 
under [http://archive.ubuntu.com/](http://archive.ubuntu.com/) there are all files, but i don't have enough disk space to make a whole copy of that... what can i do?
Maybe I'm not following you but you copied the CD to a repository directory, used wget commands (in your post)  to download missing files, and ran the installation. 

Why do you want to mirror archive.ubuntu.com?

You're PXE booting and installing from a repository (copy of CD image) provided by Apache , right?

---

### Post by vidarjb on 2008-01-10
There is one more file missing on the alternet install cd:

> wget [http://archive.ubuntu.com/ubuntu/pool/main/l/fs-secondary-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb](http://archive.ubuntu.com/ubuntu/pool/main/l/fs-secondary-modules-2.6.22-14-generic-di_2.6.22-14.47_i386.udeb)

---

### Post by dwad on 2008-01-13
Hi, I had a similar problem installing with PXE from a server CD image on lan.
Try the installation disconecting the internet acces.  
For some ¿unknown? reason PXE installation goes to ubuntu repositories on internet.

dwad

---

### Post by hans_olo on 2008-03-03
Hi,

I have been trying to do an unattended install for some days now, I have used KickStart and at last a preseed-file. Nothing works, always some packages are missing. I have my own, complete, full mirror of gutsy now ;-), but still the files are missing.
 I have tried the list of manually downloads some posts above, but these are not found anymore on the mirror. I have other versions of the missing packages, than the installer tries to get. 
So where is the real problem? I took the netboot images of gutsy...maybe the list of files is too old in the installer? How can I fix it?

Regards,

Stefan

---

### Post by hans_olo on 2008-03-04
[http://ubuntuforums.org/showthread.php?p=4450771#post4450771](http://ubuntuforums.org/showthread.php?p=4450771#post4450771) has the solution. I forgot to mirror debian-installer from updates and security. 

Now it works fine.

Cheers, Stefan

---

### Post by zwastik on 2008-05-11
I have the same* problem while installing ubuntu from the alternate cd, I set up (manual) lvm+encryption and while partitioning it stuck at 47%.

The log shows this message:

resolver (efi-modules): package doesn't exist (ignored)
resolver (libnewt0.52): package doesn't exist (ignored)

---

