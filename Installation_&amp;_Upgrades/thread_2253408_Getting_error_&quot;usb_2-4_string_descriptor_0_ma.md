---
title: "Getting error &quot;usb 2-4: string descriptor 0 malformed (err = -61)&quot; on boot"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by 6tr6tr on 2014-11-19
I've installed Ubuntu 14.10 on an Acer C720 Chromebook. When it boots up it shows the error below and hangs there for about 20 seconds before finally booting. 

[ 2.022118] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
what is causing this? How do I fix it?

USING:
Ubuntu 14.10
Linux 3.17
Acer C720 32GB, 4GB RAM

---

### Post by ibjsb4 on 2014-11-20
I found a old bug report on this, which still continues on to 2014.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433438)

Indicates that it could be a usb device.  Have you looked in dmesg?
```
dmesg
```

---

### Post by 6tr6tr on 2014-11-24
> **ibjsb4 said:**
> I found a old bug report on this, which still continues on to 2014.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433438)

Indicates that it could be a usb device.  Have you looked in dmesg?
```
dmesg
```

what should I be looking for in dmesg?

---

### Post by BradyJoe on 2015-03-23
Hey!

First, I am aware the last post was in November 2014. I know people in forums can be a bit... odd... about this. I knew if I posted the same thing it would be marked as a duplicate. Bad first post.

Bump.

I recently decided that the C720 had a lot of potential as a laptop, so I completely got rid of Chrome OS and installed Ubuntu 14.04 LTS (NOT ChrUbuntu).
Whenever I start the laptop, I have to wait 20-30 seconds before it will let me pass the error message and boot. I really hate this. Whenever I am not using a device, I always shut them down, so this is a huge inconvenience for me.

Have there been any fixes for this error message yet?

It's the exact same one.

---

