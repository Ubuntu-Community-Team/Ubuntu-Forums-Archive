---
title: "Install ubuntu 704 without CD"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by TerabyteUK on 2008-01-01
Hi,

I need to install ubuntu 704 without a CD.
How exactly do I do this? 
The partitions are already setup.
What files do I need, and where can I get them from?
My laptop can run a 'network' boot. 
I've never done this, so if it can be done via the network, please explain in detail.

Thanks.

---

### Post by Craigus on 2008-01-01
[http://ubuntuforums.org/showthread.php?t=427540&highlight=netboot]("http://ubuntuforums.org/showthread.php?t=427540&highlight=netboot")

There are other threads dealing with this as well.

---

### Post by mikesignguy on 2008-01-01
[http://ubuntuforums.org/showthread.php?t=384646&highlight=dpkg-scanpackages](http://ubuntuforums.org/showthread.php?t=384646&highlight=dpkg-scanpackages)

here is another

---

### Post by Craigus on 2008-01-01
If you don't have an OS on the machine already (it sounds as if you don't), this may be the best way to go:

[http://ubuntuforums.org/showthread.php?t=327597]("http://ubuntuforums.org/showthread.php?t=327597")

---

### Post by Pumalite on 2008-01-01
And one more:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)

---

### Post by TerabyteUK on 2008-01-01
I'll take a look at those links

> **Craigus said:**
> If you don't have an OS on the machine already (it sounds as if you don't), this may be the best way to go:

[http://ubuntuforums.org/showthread.php?t=327597]("http://ubuntuforums.org/showthread.php?t=327597")

I do have XP on the machine already.

---

### Post by TerabyteUK on 2008-01-01
> **Craigus said:**
> [http://ubuntuforums.org/showthread.php?t=427540&highlight=netboot]("http://ubuntuforums.org/showthread.php?t=427540&highlight=netboot")

There are other threads dealing with this as well.

I've used this method, sucessfully got through the installation.
Now when I try to boot up ubuntu, the starting up process cuts out at the first 'loading bar'

I tried running the (recovery) entry in grub
and the last piece of text to appear was:

4.904000] usb 3-2: configuration #1 chosen from 1 choice.

It stops here with a flashing _ cursor on the next line.

Any help appreciated. HP 2710p laptop

---

### Post by TerabyteUK on 2008-01-02
for any future curious users
the problem was due to this:

[http://ubuntuforums.org/showthread.php?p=4056106#post4056106](http://ubuntuforums.org/showthread.php?p=4056106#post4056106)

---

