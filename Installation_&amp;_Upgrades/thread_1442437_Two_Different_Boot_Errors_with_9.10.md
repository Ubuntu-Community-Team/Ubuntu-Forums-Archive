---
title: "Two Different Boot Errors with 9.10"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by raydot on 2010-03-30
Hi All,

I'm having two distinct Grub boot errors with Ubuntu 9.10, stemming from two different setups.

Anticipating that I'll be asked I ran BootInfoScript on both setups.

This is the first setup, where I put a Flash ROM card in the Flash ROM port in front of the computer.  This setup will not boot at all, and I get a message something like "Insert appropriate media and try again."

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 

```The second setup, without the Flash ROM card inserted, boots to the GRUB rescue screen:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1000944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


```I can see there's no boot loader but have no idea how to get that working.  Thanks!

---

### Post by oldfred on 2010-03-30
Computers boot from the first drive in BIOS and jump to the MBR of that drive to continue to boot. Are you trying to use a flash card like a USB drive? Will your system boot that, I guess it should see it as another drive and give it as a choice. You need to follow the directions to install a boot loader to the MBR. 

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by raydot on 2010-04-13
Yes, I think you're right, that's what I'm trying to do in the end.  Let me look into all of that and get back to you.

Thanks.

---

