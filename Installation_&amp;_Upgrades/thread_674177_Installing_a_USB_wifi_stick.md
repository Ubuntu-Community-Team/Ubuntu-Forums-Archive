---
title: "Installing a USB wifi stick"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by jhbgaiem on 2008-01-21
This may be very simple, but I am a beginner. I use Ubuntu 7.10 32bit. I have a usb wifi stick that came with a linus tar.tar file for installing it. 
Can someone please explain simply what I need to do, where (on my hard drive) I have to install it.
Simply terminal command lines would be great!
Thanks in advance
Jon

---

### Post by pytheas22 on 2008-01-21
do you know what kind of wireless card it is, and specifically who manufactured the chipset?  If not, put the stick in your computer and type

```
lsusb
```

in a terminal.  That command should tell you who manufactured the stick, and then you can look up whether its driver is already compiled into the kernel.  There's a good chance that the driver for you stick is already built-in to Ubuntu, if its manufacturer is decent about Linux support.

If not, to install drivers, you generally would first unpack the tar.gz file (aka a tarball) by right click on its icon and selecting "Extract All" (or you can do it from the command line with " tar -xvzf"  I believe).

Net, change to the directory of the unpacked tarball.  The command here depends on the name of the file and where you stored it.  If it's on your desktop and the name of the folder is "USB-DRIVER,"  you would type:

```
cd /home/YOUR-USER-NAME/USB-DRIVER
```

then it's just a matter of

```
make

sudo make install
```

and then loading the driver into the kernel using modprobe, but the name of the module depends on what your device is.

However, especially if you have a proprietary driver, it may be weird and require different steps.  When you unpack the tarball, look for a README file that would explain things.

But first, you should figure out whether you actually need to compile the driver, and take it from there.  If you have more questions, post.

---

### Post by jhbgaiem on 2008-01-21
Thank you very much for the fast reply. 
I tried 'lsusb' as you suggested and it gave me :-
ID 0ace:1215 ZyDAS
So I looked in 'Synaptic Package Manager' and found an entry for ZyDAS which I installed but it hasn't done anything. What should I have done?

The supplied driver is not a 'tar.gz' but a tar.tar. Does this make any difference?

Jon

---

### Post by pytheas22 on 2008-01-21
ok, so the chipset is zydas.  Quick research indicates that there is a driver for that stick built into Ubuntu, but it doesn't work reliably.  Try following the how-to at [http://ubuntuforums.org/showthread.php?t=92327](http://ubuntuforums.org/showthread.php?t=92327) and if run into trouble, post.

Also, what is the name of the package that you installed via Synaptic?  And you are running Ubuntu 7.10, correct?

EDIT: sorry, I see from your first post that you are indeed running Gutsy.

---

### Post by jhbgaiem on 2008-01-21
The Synaptic package is called 'zd1211-source' and yes I am in version 7.10

---

### Post by pytheas22 on 2008-01-21
Thanks.  That package is just the source code for the driver, which doesn't do anything until you compile it and install it.  So follow that how-to and post the results.

Also, just to be sure that the card isn't already detected, can you put it in your computer and post the results of the command

```
iwconfig
```

please?

---

