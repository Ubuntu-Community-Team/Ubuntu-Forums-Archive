---
title: "Will not start with 2.6.30-8, will start with 2.6.28-13 ??"
date: 2009-06-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lindsay7 on 2009-06-12
I upgraded to Karmic Koala from 9.04 just a few minutes ago and on the reboot which is set up for version 2.6.30 -8 will not start up and just lets me log in with xorg (I think that what it is called). The start up screens say that the Nvidia driver 173-14-16 failed. I can restart the system and choose the next version on the list 2.6.28-13 and the system starts back up like it should.

How do I fix this or what should I do.

---

### Post by psyke83 on 2009-06-12
> **lindsay7 said:**
> I upgraded to Karmic Koala from 9.04 just a few minutes ago and on the reboot which is set up for version 2.6.30 -8 will not start up and just lets me log in with xorg (I think that what it is called). The start up screens say that the Nvidia driver 173-14-16 failed. I can restart the system and choose the next version on the list 2.6.28-13 and the system starts back up like it should.

How do I fix this or what should I do.

Don't expect the NVIDIA drivers to work yet. Kernel 2.6.30-8 is based on upstream's 2.6.30-rc8, and we have to wait for NVIDIA to provide support for new kernels through their updates. Alpha 2 also hasn't implemented automatic support for restricted drivers (Jockey) yet, as far as I know.

You always have the option to stick with the nv/nouveau driver in the meantime. Search this sub-forum for "nvidia" and you'll find some recent discussions.

---

### Post by Regenweald on 2009-06-12
I'm using the -8 kernel and 180.60 is working here. Was using a ppa in Jaunty, just upgraded.

---

### Post by Darkshade on 2009-06-12
dark@sky:~$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 **NVIDIA 185.18.14**
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
dark@sky:~$ uname -sr
Linux **2.6.30-8**-generic


No problems here

---

### Post by xebian on 2009-06-12
> **lindsay7 said:**
> I upgraded to Karmic Koala from 9.04 just a few minutes ago and on the reboot which is set up for version 2.6.30 -8 will not start up and just lets me log in with xorg (I think that what it is called). The start up screens say that the Nvidia driver 173-14-16 failed. I can restart the system and choose the next version on the list 2.6.28-13 and the system starts back up like it should.

How do I fix this or what should I do.

The simplest way is to change driver to "nv" instead of "nvidia" in your /etc/X11/xorg.conf file.  Assuming of course xserver-xorg-video-nv is installed which is always been the case.

When this happens it drops you to a terminal login.   Just login username/password.

Once in, execute this

```
sudo nano /etc/X11/xorg.conf and then do the changes as above.

NOTE: It will ask you again for password.
```

Reboot.
Good luck.

---

### Post by jimv on 2009-06-12
If you just upgraded, you may just need to reinstall the Nvidia driver.  Try this command:

sudo apt-get install --reinstall nvidia-glx-173

---

### Post by imafatmess on 2009-06-12
I have also got this problem, however, I do not have any nvidia drivers. I have never been able to see the boot splash screen on my computer on any ubuntu version so I couldn't say where the problem occurs. Anyway, if I try and boot up in 2.6.30-8 all that happens is the screen goes black, as usual, I wait about 5 minutes then a white _ flashes in the top left hand corner of the screen. I can't type anything into it though, so it is not as if it is a terminal. However, I can boot successfully in recovery mode or 2.6.30-8 like this person... Any help? Or should I just go ahead and submit a bug report for it?...

---

### Post by chuckyp on 2009-08-20
yeah nvidia-glx-173 and nvidia-glx-96 fail to install on Karmic

---

