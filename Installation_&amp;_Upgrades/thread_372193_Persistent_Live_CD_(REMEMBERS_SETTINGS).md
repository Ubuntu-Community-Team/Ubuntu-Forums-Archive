---
title: "Persistent Live CD (REMEMBERS SETTINGS)"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by tagra123 on 2007-02-27
First of all a persistent CD allows you to install programs, change settings -- pretty much everything you can do with a full installed copy.  You first setup a partition labeled casper-rw and the settings will be saved to that partition. Its a great way to let the older child have his setup with ubuntu and then put the live cd in for the younger one.

I followed this guide and set up a PC for using Edubuntu LIVE CD. Ours is setup on an actual hard drive. Not too difficult even for a moderate user.

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

If you are setting it up on a hard drive instead of a usb stick you really only need to use gparted and create a partition and it doesnt have to be big. Then give the partition the casper-rw label

```
sudo e2label /dev/hdaX casper-rw
```

where hdaX is the drive and partition you are using.

I didn't like having to press F6 and type persistent so I used reconstructor to create an exact copy of Edubunt 6.10 except it has an additional menu item  -- PERSISTENT MODE which it defaults to.

Is there any where this file can be uploaded and shared? 

I didn't want to write a lengthy how to when there is already a good working iso.

---

### Post by tagra123 on 2007-02-28
bump

Is there any where this file can be uploaded and shared?

---

### Post by GadeTerbob on 2007-03-16
I'd sure like to see this published, too!

I have adequate server space, but about 15 downloads would eat my bandwidth!!

---

### Post by Takmadeus on 2007-03-17
how about putting it on bittorrent?

---

### Post by tagra123 on 2007-03-17
> **Takmadeus said:**
> how about putting it on bittorrent?

Good Idea. 

I'll put it together and provide  a torrent link.

---

