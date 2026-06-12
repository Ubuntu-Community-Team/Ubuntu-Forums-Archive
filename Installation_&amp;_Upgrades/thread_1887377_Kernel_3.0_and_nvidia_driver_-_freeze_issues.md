---
title: "Kernel 3.0 and nvidia driver - freeze issues"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by xigen on 2011-11-26
I just upgraded to 11.10 with the 3.x kernel.  Unfortunately, my system runs for about 30 seconds and then freezes.   My guess is that the nvidia video driver is not set correctly for the new kernel.

How do I update the nvidia driver given that my graphics freeze?  

..............
Ubuntu 11.10 32 bit
Nvidia Gforce9500gt

kernel 3.x

---

### Post by MAFoElffen on 2011-11-27
> **xigen said:**
> I just upgraded to 11.10 with the 3.x kernel.  Unfortunately, my system runs for about 30 seconds and then freezes.   My guess is that the nvidia video driver is not set correctly for the new kernel.

How do I update the nvidia driver given that my graphics freeze?  

..............
Ubuntu 11.10 32 bit
Nvidia Gforce9500gt

kernel 3.x
Please upload these files as attachments to your post:
```

~/.xsession-errors
/var/log/Xorg.0.log
/var/log/syslog1

```Note: on errorm next boot grab/copy syslog1 to your home directory and append ".txt" to it's name... Copy the other to files to Home and append ".txt" to their file names.  This forum's attachments for text files require that file extension.

Are you using the NVidia Binaries or Ubuntu's packaged drivers? If binaries, then also post the /var/log/nvidia-installer.log

---

### Post by xigen on 2011-12-06
Well - ugh!

I gave up and reinstalled. 

Then the kernel got updated from 3 0 0 12   to  3 0 0 13 and now I have driver issues again.

There must be a better way.

---

