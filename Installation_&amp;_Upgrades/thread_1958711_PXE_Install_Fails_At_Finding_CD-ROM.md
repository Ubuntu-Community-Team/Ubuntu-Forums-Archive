---
title: "PXE Install Fails At Finding CD-ROM"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by frenzy_usa on 2012-04-14
Trying to install Ubuntu 11.10 via PXE but install fails cause it can't find the cd.

I can mount, browse and copy files from the nfs share.
The iso contents are extracted to /tftpboot/

Contents of /etc/default/tftpd-hpa
```

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="192.168.3.1:69"
TFTP_OPTIONS="--secure"

```

The two lines below are from pxelinux.cfg/default
```
KERNEL ubuntu/server/11.10/i386/vmlinuz
APPEND root=/dev/nfs boot=linux netboot=nfs nfsroot=192.168.3.1:/tftpboot/ubuntu/server/11.10/i386/ initrd=ubuntu/server/11.10/i386/initrd.gz
```

---

### Post by frenzy_usa on 2012-04-15
Some more research lead me to this how-to: [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer) which uses apache2 instead of nfs-kernel-server.

Since I already had everything setup, I installed apache2 and edited /etc/apache2/sites-available/default.

```
sudo apt-get install apache2
sudo nano /etc/apache2/sites-available/default
```

Change line 4 from:
```
DocumentRoot /var/www
```

to:
```
DocumentRoot /tftpboot
```

Change line 9 from:
```
<Directory /var/www/>
```

to:
```
<Directory /tftpboot/>
```

Then modified my PXE boot menu:
```

LABEL 1
    MENU LABEL Ubuntu 11.10 server (32-bit)
    KERNEL linux
    APPEND initrd=initrd.gz

```

Now copy 'initrd.gz' and 'linux' from /tftpboot/install/netboot/ubuntu-installer/i386/ to /var/lib/tftpboot

Restarted the PXE server and then the client and was able to install Ubuntu 11.10 server.

Notes:
1) A kickstart file is not required.
The installation will ask you which mirror to download the files from. When prompted for the mirror to download from, scroll to the top of the list and select 'enter info manually' then enter the hostname or ip address of the pxe server and the path to the files from the cd/iso.
2) When the client restarted after finishing the install, I got a blank screen with a blinking cursor. I fixed it by editing /etc/default/grub and changed line 12 to:
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

Then ran:
```
sudo update-grub
```

followed by another reboot and the server was ready for me to use.

---

