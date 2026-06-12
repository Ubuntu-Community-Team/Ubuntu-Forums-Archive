---
title: "Ubuntu + ZFS instalation on USB raid"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by egrimisu on 2012-12-02
Hi guys,

i have a hp microserver with 5xSata port that i want to use in a zfs raid setup under ubuntu. of course using 5 ports for hdd ileaves me no room for the os installation. So it is safe and reliable to install the os on a usb stick ( or 2 usb sticks using raid1 if posible, i havemt't checked yet if raidi is possible with sticks). we'll this help, will this be enough for my next zfs setup or i shall go with anither zfs alternative like freenas?

thanks in advance

---

### Post by egrimisu on 2012-12-04
Let me ask this more simple, does anyone know if usb raid is a good thing or shall i install the os on a single usb. I don't want to use 2 usb if there is no way to be able to boot the os if one usb fails.

If one usb fails the rebuild on the replaced usb will work even if changed to another brand with the same or bigger capacity?
The rebuild of the software raid is easy to do or it deserves some "special" skills?

Thanks.

---

### Post by darkod on 2012-12-04
Well, I have never tried raid1 on usb sticks but in theory it should work. The only problem might be if the sticks change the order with the disks, but since the server will be mostly online that's unlikely.

A rebuild should be OK on any stick that has enough space to create a same size partition as the one on the other stick.

But I'm not sure whether ubuntu has made ZFS reliable, until recently it was still in development phase.

---

### Post by egrimisu on 2012-12-04
> **darkod said:**
> Well, I have never tried raid1 on usb sticks but in theory it should work. The only problem might be if the sticks change the order with the disks, but since the server will be mostly online that's unlikely.

A rebuild should be OK on any stick that has enough space to create a same size partition as the one on the other stick.

But I'm not sure whether ubuntu has made ZFS reliable, until recently it was still in development phase.


Thanks for the info, well it seems that zfs for linux is still in development but the latest version is marked as stable and i would like to go with it, freenas and other zfs small distros lack a lot from a server os features.

---

### Post by darkod on 2012-12-04
I'm actually looking into freenas myself because zfs for linux is quite new and I'm not sure how dependable it is. It's not enough to have a stable version, it needs a bit longer history if you want to trust all your data to it.

Of course, it's not a full server OS, and not debian based, which is my problem too because I suck at unix /freebsd.

But I found freenas to be quite flexible and easy to manage even with limited unix and zfs knowledge like mine.

For creating a NAS it looks to me like a very good option, it supports CIFS shares, NFS shares, excellent AD integration...

Now, if you want the same machine to be some kind of webserver, or mailserver, or similar, of course freenas won't do.

---

### Post by egrimisu on 2012-12-04
> **darkod said:**
> I'm actually looking into freenas myself because zfs for linux is quite new and I'm not sure how dependable it is. It's not enough to have a stable version, it needs a bit longer history if you want to trust all your data to it.

Of course, it's not a full server OS, and not debian based, which is my problem too because I suck at unix /freebsd.

But I found freenas to be quite flexible and easy to manage even with limited unix and zfs knowledge like mine.

For creating a NAS it looks to me like a very good option, it supports CIFS shares, NFS shares, excellent AD integration...

Now, if you want the same machine to be some kind of webserver, or mailserver, or similar, of course freenas won't do.

We'll i have to admit that freenas offers quite a lot of features unfortunettly does not have vpn, dlna server(plex), nagios for monitoring the pools and send mail's if problems found, and unfortunettly on my hp microserver copy speed hangned once a few seconds(i have read somewhere that the drivers are bad for freebsd for the hp microserver builtin lan card. After installing opensolaris + zfs nappit speed was good but i felt like in the woods with solaris, i feel more home with debian/ubuntu. 

Of couse everybody want's to move from clasic raid to zfs because of the benefits and one is data safety (of course zfs does not exclude to backup your data, but for a home user zfs is more that a backup in my opinion because i for example i can't afford to backup 20tb).

Anyway if i found good reason to drop ubuntu + zfs for the moment i'll go with freenas so help me found some reasons. :)

---

