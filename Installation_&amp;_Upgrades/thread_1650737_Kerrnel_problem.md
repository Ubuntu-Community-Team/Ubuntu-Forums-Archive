---
title: "Kerrnel problem"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Marky Mark on 2010-12-22
Hi All.

I have been running 10.04 quite successfully, when I upgraded to 10.10, I have a problem with the newer kernels.  If I let it boot into the latest one 2.6.35-23, I get the Ubuntu 10.10 splash screen for a second then a blank screen, same with 2.6.35-22.  I have to run with 32-25 to get it to load the gui.

Any ideas gratefully received.

I have an AMD Sempron 2800, 1.6GHz pc, but I'm not sure if it's running 64bit.

ps. relative nooby.

Cheers
Mark

---

### Post by sikander3786 on 2010-12-22
Which graphics card is there? Were any proprietary drivers installed previously and if yes, were they installed from the repositories?

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

---

### Post by Marky Mark on 2010-12-22
Thanks for the quick response.

I think so, but I'll check when I get home.

Cheers

---

### Post by Marky Mark on 2010-12-22
Hi

No proprietary drivers.

marky@marky-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
marky@marky-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: VIA Technology
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x5400004
  Serial number of failed request:  44
  Current serial number in output stream:  44
marky@marky-desktop:~$ 

Hope this helps.

---

### Post by sikander3786 on 2010-12-23
Yep, no proprietary drivers are installed there.

I think only an update can cure that problem with the latest Kernel. There doesn't seem to be any problem with your configuration as the previous Kernel is working fine.

Or some-one else might come in with a better suggestion.

---

### Post by garvinrick4 on 2010-12-23
If I get a kernel that does not match up well with my system and I have had ones that do.
I boot in the one that works, go to synaptics and type in the offending kernel
right click and remove.
In a week or two will be new kernel coming along.
Not worth knocking myself out with can be tedious.
Below is code for seeing your kernel numbers in terminal so can copy into synaptics.
```
grep menuentry /boot/grub/grub.cfg

```

---

### Post by theasprint on 2010-12-23
Hi,

I use Nvidia graphics card.

From my experience, my Nvidia graphics card always have problems like screen-resolution and sometimes black screen. But I solved the problem by installing some drivers from the Nvidia website.
And everytime there is a new kernel update, I would have to reinstall the drivers again.

So I would like to suggest to you is that did you do anything to make your graphics work with your "working graphics" kernel? 
If you do, then you would most probably need to do the same steps again.

---

### Post by Marky Mark on 2010-12-23
Thanks for all the help folks.

Ironically, I have another pc running 10.10 with no problems and that has proprietary video drivers, no problems at all:)

I'll have a look at tidying up my kernels.

Thanks again, Merry Christmas.

MyM

---

