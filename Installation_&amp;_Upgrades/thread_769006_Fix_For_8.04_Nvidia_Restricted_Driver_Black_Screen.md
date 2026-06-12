---
title: "Fix For 8.04 Nvidia Restricted Driver Black Screen or X Crashing"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by dayzed2 on 2008-04-26
I reported the fix here [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173418](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173418)

--------

For those of you having problems with the nvidia restricted driver either crashing X or displaying a black screen with Ubuntu 8.04 use the latest nvidia beta driver found on the nvidia website it is version NVIDIA-Linux-x86-173.08-pkg1.run. I am running the Quadro NVS 140M on a Dell D830 and this fixed my problem. The driver can be found here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and then click on archive and find the 173.08 driver.

Here are the steps:
1. Purge the nvidia restricted package if installed by doing a "dpkg --purge nvidia-glx-new"
2. Kill the gdm server, "/etc/init.d/gdm stop"
3. Install the driver mentioned above.
4. start gdm server "/etc/init.d/gdm start"
When X starts you should now see the nvidia logo with the the words beta in red. If you don't edit you xorg.conf file and replace nv with nvidia and restart X.

Hope this helps someone!!

---

### Post by ynnek63 on 2008-04-26
> **dayzed2 said:**
> I reported the fix here [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173418](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173418)

--------

For those of you having problems with the nvidia restricted driver either crashing X or displaying a black screen with Ubuntu 8.04 use the latest nvidia beta driver found on the nvidia website it is version NVIDIA-Linux-x86-173.08-pkg1.run. I am running the Quadro NVS 140M on a Dell D830 and this fixed my problem. The driver can be found here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and then click on archive and find the 173.08 driver.

Here are the steps:
1. Purge the nvidia restricted package if installed by doing a "dpkg --purge nvidia-glx-new"
2. Kill the gdm server, "/etc/init.d/gdm stop"
3. Install the driver mentioned above.
4. start gdm server "/etc/init.d/gdm start"
When X starts you should now see the nvidia logo with the the words beta in red. If you don't edit you xorg.conf file and replace nv with nvidia and restart X.

Hope this helps someone!!

Didn't work for me and now I just get the blinking cursor. this was my 13th and probably last attempt to get kubuntu/ubuntu hardy running.

---

### Post by dayzed2 on 2008-04-27
I would also like to add something else to my fix. After rebooting X will fail with the beta driver. I have no idea why but the only way I was able to fix this was to uninstall the nvidia-kernel-common package in addition to the nvidia-glx-new. So here is revision 2 of the work around.

1. Download the 173.08 nvidia beta driver here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) click on archive and find the 173.08 driver.
2. Purge the nvidia restricted package and the nvidia-kernel-package if installed by doing a "dpkg --purge nvidia-glx-new nvidia-kernel-common"
3. Kill the gdm server, "/etc/init.d/gdm stop"
4. Install the driver downloaded in step 1, unless you are brave you need to let the nvidia installer modify the xorg.conf file.
5. start gdm server "/etc/init.d/gdm start"

---

### Post by bierholen on 2008-04-29
I can't uninstall the "nvidia-kernel-common" package because of dependencies. The beta driver still fails every time the X-server is restarted. The only workaround for me so far is reinstalling the driver every single time.

---

### Post by dayzed2 on 2008-04-29
>I can't uninstall the "nvidia-kernel-common" package because of dependencies.
Come on, were you to lazy to list the dependencies and why you need them? Please list the dependencies and what makes you think you need them.

---

### Post by bierholen on 2008-04-29
> **dayzed2 said:**
> >I can't uninstall the "nvidia-kernel-common" package because of dependencies.
Come on, were you to lazy to list the dependencies and why you need them? Please list the dependencies and what makes you think you need them.

```
dpkg: dependency problems prevent removal of nvidia-kernel-common:
linux-restricted-modules-2.6.24-16-generic depends on nvidia-kernel-common
```

If I include "linux-restricted-modules-2.6.24-16-generic" I get the next dependency error:

```
dpkg: dependency problems prevent removal of nvidia-kernel-common:
linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-16-generic
```

And so on...

---

### Post by kaziu on 2008-04-29
I fix this problem after Upgrade to 8.04. First remove your nvidia-glx (or nvidia-glx-new):

```

sudo dpkg --purge nvidia-glx-new

```

and after this:

```

sudo aptitude install nvidia-glx-new linux-restricted-modules-$(uname -r)

```

I install nvidia-settings too:
```

sudo apt-get install nvidia-settings

```

I hope that it fix your problems with nvidia crads :)

---

### Post by yomyom on 2008-04-30
> **kaziu said:**
> I fix this problem after Upgrade to 8.04. First remove your nvidia-glx (or nvidia-glx-new):

```

sudo dpkg --purge nvidia-glx-new

```

and after this:

```

sudo aptitude install nvidia-glx-new linux-restricted-modules-$(uname -r)

```

I install nvidia-settings too:
```

sudo apt-get install nvidia-settings

```

I hope that it fix your problems with nvidia crads :)


Thanks for the tip kaziu, this fixed my problem with a GeForce Go 7600 :)!

---

### Post by bierholen on 2008-04-30
> **kaziu said:**
> I fix this problem after Upgrade to 8.04. First remove your nvidia-glx (or nvidia-glx-new):

```

sudo dpkg --purge nvidia-glx-new

```

and after this:

```

sudo aptitude install nvidia-glx-new linux-restricted-modules-$(uname -r)

```

I install nvidia-settings too:
```

sudo apt-get install nvidia-settings

```

I hope that it fix your problems with nvidia crads :)

This doesn't do if for me:( I still need to reinstall the driver every time I restart the X-server.

---

### Post by dayzed2 on 2008-04-30
bierholen,

ok then try using apt to remove these pachages, example:
apt-get remove nvidia-glx-new nvidia-kernel-common linux-restricted-modules-2.6.24-16-generic

---

### Post by bierholen on 2008-04-30
> **dayzed2 said:**
> bierholen,

ok then try using apt to remove these pachages, example:
apt-get remove nvidia-glx-new nvidia-kernel-common linux-restricted-modules-2.6.24-16-generic

That seems to work :). I hope I didn't destroy any other functionalities by removing linux-restricted-modules-2.6.24-16-generic though.

---

### Post by dayzed2 on 2008-05-10
There is a better way than to uninstall the nvidia-kernel-common package and that is to blacklist the nv driver. I originally tried to do this in the "/etc/modprobe.d/blacklist" file but that failed hence the reason why I said to uninstall the nvidia-kernel-common package (I was in a hurry). The right way is to black list the nv driver in the "/etc/default/linux-restricted-modules-common" file.

Revision 3
1. Download the 173.08 nvidia beta driver here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) click on archive and find the 173.08 driver.
2. Purge the nvidia restricted package if installed by doing a "dpkg --purge nvidia-glx-new"
3. Kill the gdm server, "/etc/init.d/gdm stop"
4. Install the driver downloaded in step 1, unless you are brave you need to let the nvidia installer modify the xorg.conf file.
5. Black list the nv driver in the "/etc/default/linux-restricted-modules-common" (should look like this DISABLED_MODULES="nv")
5. start gdm server "/etc/init.d/gdm start"

---

