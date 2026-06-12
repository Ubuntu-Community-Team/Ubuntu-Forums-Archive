---
title: "Mount fail USB Hotplug ACER Z220 Adroid Lollipop 5.0"
date: 2015-07-25
forum: MINT
---

### Post by Kevin McCready on 2015-07-25
My system is failing to automount ACER Z220 Smartphone Adroid Lollipop 5.0 to make it available to my file manager. 

An  Android icon appears on the desktop. When I hover the mouse over the  icon it says "Removable Volume Not mounted yet". So I left click on in  and select Mount. When I then click on the icon, Thunar (the native file  manager) opens at "mtp://[usb:001,005]/"

I don't feel I'm experienced enough to tweak the fstab, and am not sure how to anyway. 

Any help would be welcome.

Here's what I have:

lsusb
Bus 001 Device 004: ID 0402:7675 ALi Corp. 
Bus 001 Device 005: ID 0502:374f Acer, Inc. [this is the culprit which gets a diff Device number for each hotplug attempt]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 016: ID 0458:0037 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo blkid
/dev/sda1: UUID="0d1a8d35-e9bd-402c-b8fb-ea04d59da414" TYPE="ext4" 
/dev/sda5: UUID="5454b37b-4f46-4300-a56d-317430794ad7" TYPE="swap"  [this is it MAYBE?]

sudo mount -t swap /dev/sda5 /mnt
mount: unknown filesystem type 'swap']
 
I'm running 
RELEASE=17
CODENAME=qiana
EDITION="Xfce 32-bit"
DESCRIPTION="Linux Mint 17 Qiana"
DESKTOP=Xfce
TOOLKIT=GTK

---

### Post by Kevin McCready on 2015-08-01
Bump. Hoping perhaps a moderator can alert Old Fred. Would he be good at this?

---

### Post by howefield on 2015-08-01
Thread moved to the "*MINT*" forum.

Does the phone automount when unlocked?

---

### Post by Kevin McCready on 2015-08-01
No, it doesn't automount when unlocked.

---

### Post by Kevin McCready on 2015-08-06
bump

---

### Post by oldfred on 2015-08-09
I do not know Mint nor Android phones.

My iPhone has given a few issues, but once some software was downloaded & permissions given on phone it now at least mounts so I can manually copy photos.

Seems to also be a Windows issue.
[http://forums.androidcentral.com/general-help-how/495665-how-mount-mtp-ptp-drive-letter-usb-mass-storage-ums.html](http://forums.androidcentral.com/general-help-how/495665-how-mount-mtp-ptp-drive-letter-usb-mass-storage-ums.html)
It is not showing a UUID, so you do not mount swap or one of partitions you show.

Does Disks which is in Ubuntu, not sure what other tools you have to show partitions, show phone?

Found this in Mint forum.
[http://forums.linuxmint.com/viewtopic.php?f=90&t=172586](http://forums.linuxmint.com/viewtopic.php?f=90&t=172586)

---

### Post by Kevin McCready on 2015-08-09
Thanks oldfred. I follwed the MTP clue and after much trying of the following found the system now works:
mtpfs
kio-mtp (didn;t seem to do much)
mtp-server
mtp-tools
qlix
jmtpfs

I also edited "/etc/fuse.conf" and removed the # from the line "user_allow_other":
sudo subl -i 's/#user_allow_other/user_allow_other/g' /etc/fuse.conf

THEN rebooted

I  should have rebooted after each try of these packages and solutions  bvut didn't know that until after, so I don;t know which one made the  difference.

I don't know what finally made it work. But it seems  to be a problem in libmtp. In a few of the packages I got this sort of  message:
 Device 0 (VID=0502 and PID=374f) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team [I have no idea how to do this]
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Android device detected, assigning default bug flags

Other advice in the links was to use AirDroid or ftp, sftp, or samba or shh apps on the android. I din;t try that.

---

### Post by tomasrey88 on 2015-08-09
Unfortunately, you'll need an ACER USB driver only available in windows, not linux. 
[http://us.acer.com/ac/en/US/content/drivers#_ga=1.9395061.1534759372.1439178255](http://us.acer.com/ac/en/US/content/drivers#_ga=1.9395061.1534759372.1439178255)

You'll either need Windows or WINE to run the driver to connect to your phone. You'll need to save the extracted data or put data on it from a windows partition on your HD or at least a USB memory stick with all your files that you want to move to your phone or from your phone to the usb. 

You're welcome :-)

BTW, shameless plug. Please answer my question. Thanks! (link below)
[http://ubuntuforums.org/showthread.php?t=2288606](http://ubuntuforums.org/showthread.php?t=2288606)

---

### Post by Kevin McCready on 2015-08-28
No I didn't need windows. Linux worked fine. problem solved on one computer, now to fix the second computer in the house

---

