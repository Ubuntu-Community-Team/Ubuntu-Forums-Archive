---
title: "PXE diskless Ubuntu Setup"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by rexzhen on 2010-06-24
I have a PXE server which installed DHCP TFTP AND NFS service. and set them up followed by [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

the boot process hanged here:

   ipconfig: eth0: SIOCGIFUNDEX: No such device
  ipconfig: no devices to configure
  [-n eho]
  . /tmp/net-eth0.conf
  /init: line 3: can't open /tmp/net-eth0.conf
  ...
  
After I google and research it for a couple of days. Nothing helpful.

what i did try to work around is,

1. set portfast to all the ports connected the PXE server and client.
2. edit pxelinux.cfg/default, try different setting in "ip=" ( i did not find any manu in the internet which explain to to configure this file)

Help please.

---

### Post by nerdzero on 2010-06-24
Hi rexzhen,

I have no experience with PXE servers but I checked Launchpad and it seems there is a bug which is probably causing your issue:  [https://bugs.launchpad.net/bugs/181258](https://bugs.launchpad.net/bugs/181258)

---

### Post by rexzhen on 2010-06-24
Hi,

Thank you for your quick reply. I read that post. But I do not know how to do the patch.
Like the last post, we have a link [http://paste.ubuntu.com/427631/](http://paste.ubuntu.com/427631/)
but how to use it?

---

### Post by nerdzero on 2010-06-24
Sorry, applying patches to the kernel/initrd source and recompiling them is still beyond me.  Maybe an expert on those will come along and help.  One thing I noticed though looking over the How-to you used as a source...

> NOTE: If the client source installation you copied the files from should remain bootable and usable from local hard disk, restore the former BOOT=local and MODULES=most options you changed in /etc/initramfs-tools/initramfs.conf. Otherwise, the first time you update the kernel image on the originating installation, the initram will be built for network boot, giving you "can't open /tmp/net-eth0.conf" and "kernel panic". Skip this step if you no longer need the source client installation.

...

> **Setup your client**
Enter your BIOS settings and configure your system to boot from LAN

Are you sure changed your boot order on the client?  Maybe it's still trying to boot from the hard drive as it sounds like it will have the same symptoms as the bug described in Launchpad.

---

### Post by glscat on 2010-06-25
hello nerdzero,

Curious, How far did you get with your PXE boot (on Lucid) ?

I have an almost boot-able system but it fails in the Upstart initialization at "portmap main" & "portmap post-start". This leaves me without a console but I can ssh into the system as root.

I was hoping you may have ran into (and solved) this issue.

---

### Post by rexzhen on 2010-06-25
Hi Thank you take a time looking to it.

1. i am sure i have already boot to Lan, and touch the PXE files in the PXE server. 
2. for the initramfs.conf thing, i think he means if we want to boot from local afterward, we should make sure the initra file is created from the resotreed configure file.

Still fighting setup the diskless Ubuntu.

btw, for excercise, i setup the installation from LAN for ubuntu. it is working. I can install the Ubuntu from pxe server.

maybe i need more knowledge for the pxelinux.cfg setting. Maybe Ubuntu do not support diskless for M610(dell blade server).

---

### Post by glscat on 2010-06-25
I did the following on the system before I transfered it to the PXE boot server:
[INDENT] $ sudo nano -w /etc/initramfs-tools/initramfs.conf
    # MODULES=most
    MODULES=netboot

    # BOOT=local
    BOOT=nfs

 $ sudo mkinitramfs -o /initrd.img.nfs -v
[/INDENT]Then, on the server, setup the pxelinux.cfg/default
[INDENT] $ sudo nano -w /var/lib/tftpboot/pxelinux.cfg/default
    prompt 0
    timeout 0
    default ubuntu-10.04
    label ubuntu-10.04
            kernel os-10.04/vmlinuz
            append initrd=os-10.04/initrd.img.nfs root=/dev/nfs nfsroot=10.2.100.1:/var/lib/tftpboot/os-10.04
[/INDENT]

---

### Post by rexzhen on 2010-06-25
Sill no luck. And It even loaded kernel vmlinuz and initrd.img which i created in the client. But it stopped immediataly at

ipconfig: eth0: SIOCGIFUNDEX: No such device
  ipconfig: no devices to configure
  [-n eho]
  . /tmp/net-eth0.conf
  /init: line 3: can't open /tmp/net-eth0.conf

[   1.110845] Kernel panic -not syncing: attempted to kill init!
[   1.110917] Pid: 1 ,comm: init Not tained 2.6.32-21-generic-pae #32-Ubuntu
[   1.110990] Call Trace:
[   1.111058] [<>c05af225] ? printk +0x1d/0/20
....
....

---

### Post by rexzhen on 2010-06-26
i worked it out.

Before i copy the file system to the NFS share in PXE server. i have to install nfsboot and nfsbooed first.
#apt-get install nfsboot nfsbooted

if we have not install these package, the copied kernal and initr file will not support the NFS mount.

that is the root cause the system can not find the root patition when boot from PXE.

we can say this is fixed.

---

### Post by glscat on 2010-06-26
good to hear you have a pxe netboot
I too resolved my problems.
seems my fstab was causing the upstart initialization to fail

My initramfs.img.nfs is creating tmpfs mounts that I was then trying to recreate in the fstab
            # tmpfs /tmp tmpfs defaults 0 0
            # none  /var/lock tmpfs defaults 0 0
            # none /var/run tmpfs  defaults 0 0
            # none /var/tmp tmpfs defaults 0 0
Also, other nfs mounts in fstab required the "nolock" option

I then had to execute one of my sysinitV scripts with an Upstart "start on runlevel [23]"

Ya, thats why we get payed the big bucks..... ???

I did not need "apt-get install nfsboot nfsbooted" although one node seems to exhibit simular problems to your's, "ipconfig: eth0:" But that appeared to be a H/W fault in an Ethernet device, resolved with switching to a different Ethernet device.
I will look into the  "apt-get install nfsboot nfsbooted" packages you've suggested.

---

### Post by rexzhen on 2010-06-29
One more issue, i can apt-cache find out the nfsboot and nfsbooted package in ubuntu release 9.04. 

But I cannot find it anymore in the release above that. I tried 9.10, 10.10.

Why? and what is the replacement.

---

### Post by nerdzero on 2010-06-29
Glad you found a solution, rexzhen!

Looking at packages.ubuntu.com, it seems like they are meta-packages and they are no longer delivered after 9.04.  Not sure why, there doesn't seem any place to find out that information.

You can install all the packages they would have installed individually I suppose.  These pages list what the meta-packages install.

[http://packages.ubuntu.com/jaunty/nfsboot](http://packages.ubuntu.com/jaunty/nfsboot)

[http://packages.ubuntu.com/jaunty/nfsbooted](http://packages.ubuntu.com/jaunty/nfsbooted)

I hope that is what you were looking for.

---

### Post by gamezr2ez on 2010-09-06
I cant tell your original goal from the posts, if it was to install ubuntu from a disk image over nfs or get a live cd running on a thinclient. However, i was directed here in my search to get ubuntu installed over pxe with nfs.

The problem i was getting was it looking for the disk. I used the provided kernel (%disk_dir%/install/vmlinuz) and was trying to use %disk_dir%/install/initrd.gz

The correct initrd.gz is located %disk_dir%/install/netboot/ubuntu-installer/[amd64,i386]/initrd.gz

My pxelinux config file looks like this:

LABEL ubuntu_10.04
        kernel /var/lib/tftpboot/images/ubuntu/install/vmlinuz
        append root=/dev/nfs nfsroot=192.168.xx.xx:/var/lib/tftpboot/images/ubuntu initrd=/var/lib/tftpboot/images/ubuntu/install/netboot/ubuntu-installer/amd64/initrd.gz ip=dhcp rw

Hope this helps someone stumbling through this thread like i did!

---

