---
title: "Update to 7.04 all done, only one problem, need help."
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by pansz on 2007-05-30
Hi,

I upgrade my dapper to edge and then edge to feisty, which takes me two nights... I had solved some problems, the serious one is that the new kernel recognize my hard disk as /dev/sda instead of /dev/hda and I need to change my /etc/fstab.

Now everything is done, and the system starts... it takes 6 minutes to startup, but before upgrade my ubuntu could start in 2 minutes.

If I choose "recovery mode", everything seems to be okay and my computer starts up quick.

So, my problem is:
1. my ubuntu start with no "ubuntu" logo now, all I met is the black screen when startup.
2. it seems that the "black screen" hangs there for 4 minutes before my desktop manager loads.

Any one know how could I identify the problem, how can I know what ubuntu is doing instead of just seeing a blank screen.

---

### Post by awaldram on 2007-05-30
press ctrl alt F1

too see what s going on

---

### Post by openmtl on 2007-05-31
Check that your swap is really being loaded too !. I upgraded from 6.10 -> 7.04 and it did that trick of changing /dev/hda -> /dev/sda and altering /etc/fstab to refer to UUIDs BUT due to a problem with the superblock on my swap partition (e.g.. sudo tune2fs -U uuidgen /dev/sda5 says...tune2fs: Bad magic number in super-block while trying to open /dev/sda5, Couldn't find valid filesystem superblock.)  my system upgraded from devices to UUIDs except the swap. At startup the swap did not mount. All sorts of weird things happened due to Out of memory. I fixed my swap the lazy way by reformating and then running the tune2fs to set the UUID i.e.,

sudo tune2fs -U uuidgen /dev/sda5

then running vol_id to verify it was really set i.e.,

sudo vol_id /dev/sda5

and then editing /etc/fstab to use UUID instead of devices. Just a thought.

---

