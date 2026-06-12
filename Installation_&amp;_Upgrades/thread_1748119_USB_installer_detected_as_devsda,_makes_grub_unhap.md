---
title: "USB installer detected as /dev/sda, makes grub unhappy"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by j8kel on 2011-05-03
I used usb-creator-gtk to create a bootable usb drive using the Ubuntu Server 10.04 lts ISO.  I have two dell machines.  On one of them the usb drive is detected as /dev/sda which causes a problem when installing grub because the machine's hard drive comes up as /dev/sdb.  The grub bootloader gets loaded onto the usb drive instead of the hard drive.  Even if I were able to get grub to install on /dev/sdb, when i reboot without the usb drive, the hard drive will be /dev/sda, and grub still won't work.

On my other Dell box ( a different model ), the same usb drive is detected as /dev/sda.  I have tried changing every BIOS setting I can find on the box that doesn't work, but to no avail.

Does anyone know how to make the hard drive show up as /dev/sda so I can do the install?


Thanks.

---

### Post by oldfred on 2011-05-03
Best just to do manual install. With manual install you get the option on where to install grub2's boot loader and then you can choose sdb.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Even though you only have one drive it is a little more like this since you are installing to sdb:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

With manual install you have to create your partitions, choose which is / (root) & /home. It finds swap but you still have to create it.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by j8kel on 2011-05-04
Thank you for the info.  If I have to use /dev/sdb, I will look into  installing it that way.  I was hoping to use as much standard Ubuntu  software as possible.  And I am also working on making the install  silent (or promptless) as I plan to install it on many machines.  I have  a seed file which accomplishes this, I just need to address the  /dev/sdb issue.

---

### Post by j8kel on 2011-05-19
I have read a bit about udev.  Is that something I could use to help me with this?

---

### Post by j8kel on 2011-06-03
For my purposes, I needed to be able to create a usb stick that could do automated install without user intervention.  I needed the same installer to work on dell appliances that named the usb drive /dev/sda and /dev/sdb.  The solution I found to this was opening the initrd.gz and adding some rules to /etc/udev/rules.d.

When I build the usbdrive, I apply a label to it, either using dos's "label", or linux "mlabel" or "makedosfs".  The rules I embedded into the initrd check for this label being recognized as /dev/sda, and if so, switch it with /dev/sdb.

This happens in time for the installer to proceed normally as though the usb drive was discovered as sdb to begin with.

The rules file is named 99-install.rules and the contents look like this:

```

KERNEL=="sda*",ENV{ID_FS_LABEL}=="INSTALL",NAME="sdb%n"
KERNEL=="sdb*",ENV{ID_FS_LABEL}!="INSTALL",NAME="sda%n"

```

---

