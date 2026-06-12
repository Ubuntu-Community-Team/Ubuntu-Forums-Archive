---
title: "Install edgy with dmraid??"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by zaubara on 2007-03-21
Hey there!


I finally decided to switch to Ubuntu with WinXP in dual boot for some gaming, but I got some problems with my Raid0-Device. :(

Strange enough, I already had Ubuntu up and working on a very similar system, but this time I don't seem to make it :(


First of all: I want to install Edgy, but because I know that dmraid is broken there, I am currently trying to use the dmraid backport.
The original dmraid in feisty works great for me, but I am still unable to install feisty because a debootstrapped system doesn't seem to install without errors (some packages cannot be configured and therefore everything stops after some time).



I am now trying to install edgy over the alternate install, wget'ing this version:
[http://librarian.launchpad.net/5010539/dmraid_0.9.9%2B1.0.0.rc13-0ubuntu2_i386.deb](http://librarian.launchpad.net/5010539/dmraid_0.9.9%2B1.0.0.rc13-0ubuntu2_i386.deb)
By installing zlib, libsepol and libselinux, dmraid seems to be working, BUT it does _not_ activate my nvidia raid device, although recognized:

Activating the raid:
```
# dmraid -ay
/dev/sda: "sil" and nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and nvidia" formats discovered (using nvidia)!
```
The output seems to be identical to the (working) one of feisty.

Deactivating the raid:
```
# dmraid -an
/dev/sda: "sil" and nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and nvidia" formats discovered (using nvidia)!
RAID set "nvidia_cadahceb" is not active
```
This one should give the same output as -ay, but I guess thats because it was not able to activate the raid device before anyway!
(ls /dev/mapper/nvidia_... does not even exist, actually not even the "mapper"-one!)


Still, it seems to recognize my stripearray:

```
# dmraid -s
/dev/sda: "sil" and nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and nvidia" formats discovered (using nvidia)!
*** Set        # I think that should normally say "Activated Set" or something
name   : nvidia_cadahceb
size      : 625163520
stride:  : 128
type     : stripe
status   : ok
subsets : 0
devs     : 2
spares  : 0
```


I am really out of ideas, maybe you guys could help me?

Really appreciate your help, I don't want to get back to XP :(
Greetings

---

### Post by tomm3h on 2007-03-22
I believe you've already found the other [Edgy fakeraid thread]("http://ubuntuforums.org/showthread.php?t=316182"), but I've included the link here just in case any others stumble across your thread looking for answers.

---

### Post by zaubara on 2007-03-23
Yup, sorry for not editing my post.

The reworked version of [https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy) did work for me, finally :guitar:

---

