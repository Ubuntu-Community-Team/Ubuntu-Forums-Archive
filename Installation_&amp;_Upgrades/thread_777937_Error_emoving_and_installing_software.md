---
title: "Error emoving and installing software"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by muskedear on 2008-05-01
Good day,

My Synaptic Package Manager (Ubuntu 8.04) seems to have trouble completely removing nvidia and then installing vim.  It gets stuck while running some post-removal script and then says: 

E: nvidia-glx: subprocess post-removal script returned error exit status 2

Any suggestions as to how this problem can be solved?

Thanks.

---

### Post by El King on 2008-05-01
Open terminal and write
```
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
```

```
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
```

```
sudo dpkg-divert --remove /usr/lib/xorg/modules/libGLcore.so
```

```
sudo apt-get install nvidia-glx-new
```

Also this link mite help
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130208](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130208)

---

### Post by muskedear on 2008-05-01
Thanks.  That did not help, though.  I don't even have an X11R6 directory.  Using my X11 instead did not help either.  Same problem.  It seems to be unable to drop nvidia-glx from the Synaptic.  Any other advice?

---

### Post by muskedear on 2008-05-01
Finally, this worked for me:

:/usr/lib$ sudo mv libGL.so.1.2 libGL.so.1.2.old

---

### Post by El King on 2008-05-02
Great, Maybe u cud tag this as solved so other ppl cud benefit

---

