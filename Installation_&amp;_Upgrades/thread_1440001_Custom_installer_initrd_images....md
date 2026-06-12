---
title: "Custom installer initrd images..."
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by pjfasano on 2010-03-26
I need to install Ubuntu on approximately 50-60 netbooks. None of them have CD drives, and I don't want to have to install them individually, walking around with a USB stick. I figured the fastest way to install on so many machines is to use a combination of apt-cacher ([http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)) and netbooting. I have successfully booted one machine to test, but as soon as the kernel comes up, support for the network interface is gone. Specifically, the "atl1c" module is not included on the netboot initrd image. Also, I would like to try to use preseeding, and I need to get that onto the initrd as well.

So, to summarize my question: **How can I create a custom *install* kernel and initrd?** I have a feeling it's related to the "debian-installer" category in the package repository, but I have not found any good documentation about doing this.

Thank you in advance!

---

### Post by pjfasano on 2010-03-27
Did I post this in the correct category? I'm new here... should I have posted in one of the development forums?

---

### Post by pjfasano on 2010-03-27
Maybe I can rephrase this question... how is the netboot ([http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/)) image created?

---

### Post by pjfasano on 2010-03-31
Okay, I solved this a different way:

**IMPORTANT: The PXE/BOOTP/DHCP3/TFTP/NFS server needs a STATIC IP!**

**[SIZE=3]1) Install software/tools[/SIZE]**
```
# We need a DHCP server, TFTP server, and NFS server
sudo apt-get install dhcp3-server tftp-hpa nfs-kernel-server
```[B][SIZE=3]
2) Download necessary files:[/SIZE][/B]
Ubuntu Netbook Remix ISO: [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
Ubuntu netboot image (for PXELINUX): [http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

[B][SIZE=3]3) Unpack everything
[/SIZE][/B]First, unpack the SYSLINUX/PXELINUX package
```
cd /var/lib/tftpboot
sudo tar xvfz *</path/to/netboot.tar.gz*>
```Next, mount the UNR iso loopback:
```
sudo mount -o loop *</path/to/unr.iso>*
```Copy vmlinuz and initrd from iso:
```
sudo cp /mnt/casper/vmlinuz /mnt/casper/initrd.lz /var/lib/tftpboot
```[SIZE=3]
[B]4) Modify PXELINUX configuration files:
[/B][/SIZE]Edit /var/lib/tftpboot/pxelinux.cfg/default to say: (modify "file=" option if using preseeding)
```
kernel vmlinuz
append  file=/cdrom/preseed/netbook-remix.seed boot=casper initrd=initrd-new.lz nfsroot=*<server.ip>*:/mnt netboot=nfs --
```[SIZE=3][B]
5) Modify the initrd
[/B][/SIZE]Firstly, make a working directory and unpack the initrd into it:
```
mkdir -p ~/workdir/custom-initrd
cd ~/workdir/custom-initrd; lzcat /mnt/casper/initrd.lz | cpio --extract
```Next, mount the squashfs from the UNR iso:
```
mkdir ~/workdir/unr_squashfs
sudo mount -o loop -t squashfs /mnt/casper/filesystem.squashfs ~/workdir/unr_squashfs
```Now comes the cool part... copy whatever files you want on the initrd (presumably kernel modules) from the squashfs:
```
# In my case, I want the atl1c driver:
cp -r ~/workdir/unr_squashfs/lib/modules/2.6.31-14-generic/kernel/drivers/net/atl1c* ~/workdir/custom-initrd/lib/modules/2.6.31-14-generic/kernel/drivers/net/
```Now repackage the initrd:
```
cd ~/workdir/custom-initrd; find . -print | cpio -H newc -o | lzma > /var/lib/tftpboot/initrd-new.lz
```[SIZE=3][B]
6) Set up DHCP and NFS[/B][/SIZE]
In your /etc/dhcp3/dhcpd.conf:
```
default-lease-time 600;
max-lease-time 7200;

allow booting;
allow bootp;

# The next paragraph needs to be modified to fit your case
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.253;
  option broadcast-address 192.168.1.255;
# the gateway address which can be different
# (access to the internet for instance)
  option routers 192.168.1.3;
# indicate the dns you want to use
  option domain-name-servers 192.168.1.3;
  next-server 192.168.1.3;
  filename "pxelinux.0";
}

group {
  next-server 192.168.1.3;
}
```In your /etc/exports file:
```
/mnt 192.168.1.0/24(rw,no_subtree_check,no_root_squash)
```[B][SIZE=3]
7) Bringing it all together[/SIZE][/B]
(Re)start all the necessary services:
```
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/tftpd-hpa restart
sudo /etc/init.d/dhcp3-server restart
```Boot your machine up off the network!

---

### Post by pjfasano on 2010-04-03
Since I solved this, could a moderator please delete the #2 and #3 posts, this post, and mark the thread as [SOLVED]?

EDIT: Thank you!

---

