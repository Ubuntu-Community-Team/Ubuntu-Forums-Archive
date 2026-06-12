---
title: "[SOLVED] Update failed - Out of space?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2008-05-26
Running an update and it fails with the following message:

dpkg: error processing /var/cache/apt/archives/linux-ubuntu-modules-2.6.24.17-generic_2.6.24-17.25_amd64.deb (--unpack):
  failed in buffer_write(fd) (10,ret=-1): backend dpkg-deb during ~./lib/firmware/2.6.24-17-generic/v4l-cx2341x-dec.fw' : no space left on device

It's obvious to me that I'm out of space on a device, but which one is a mystery.  All of my drives have several GiB of free space, so I'm stumped.

Can someone tell me where to look?  Is any other info necessary?

---

### Post by zvacet on 2008-05-26
You can try this commands and see if they make any change

```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by Bill Roberts on 2008-05-26
Already been there - it's not the archive that's out of space, it's the destination.

---

### Post by zvacet on 2008-05-27
```
sudo apt-get autoremove
```

---

### Post by iaculallad on 2008-05-27
Or you could remove older/unused linux-images to free spaces.

---

### Post by Bill Roberts on 2008-05-27
> **iaculallad said:**
> Or you could remove older/unused linux-images to free spaces.

Please tell me where to find and how to identify them.

---

### Post by forestpixie on 2008-05-27
Have a quick look in your menu list to see what you have in the list

```
cat /boot/grub/menu.list
```

Then check in synaptic for linux image and there will be all the kernels there - uninstall the old ones.

To check space on your drives use

```
df -h
```
If you have a seperate /boot partition check that in particular - but you can tell which is full - it gives a %

IF not sure post df -h here

---

### Post by yogo on 2008-05-27
> **Bill Roberts said:**
> Please tell me where to find and how to identify them.

But if you have several gigs left, that should not be necessary.

---

### Post by zvacet on 2008-05-27
> Please tell me where to find and how to identify them.


In synaptic type in search box **linux-image**,and you will see list of that packages.Delete ones with lower number and leave 2.6.22-14 (Gutsy kernel).

```
sudo update-grub
```

---

