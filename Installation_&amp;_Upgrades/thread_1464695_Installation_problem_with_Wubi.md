---
title: "Installation problem with Wubi"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by dmata82 on 2010-04-28
Good afternoon,

I am trying to install Ubuntu 9.10 desktop i386 in a Toshiba Satellite L35 with windows XP SP2 using the Wubi installer.

My cd drive is not reading cds so i tried installing from a pen drive with no success. I mounted the ubuntu cd and installed from windows, but when i reboot the computer and choose Ubunt it says that is going to keep with the installation and gives me this message:

[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x149ae000, size0=57d098]

and then stop.

What can I do?

---

### Post by bcbc on 2010-04-28
Any CD you virtually mount from within windows will not be around when you reboot and so not accessible for the installation of ubuntu (that actually happens after you reboot for the first time).

You can download and run wubi.exe from [here]("http://wubi-installer.org/"). It will download the Ubuntu 9.10 CD and store it in a place that's accessible for the wubi install after you reboot. (Downside is you have to download the entire CD to do the install and it's not persisted in a way that you can use it again if you need to reinstall).

Make sure when you restart after the initial install that you select Ubuntu. i.e. don't wander off, or it'll boot windows by default and you'll likely have to repeat the install.

Also, NOTE, after completing the install, you need to replace the wubildr file with an updated version. See [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") for details.

Edit: if you run wubi.exe from a directory that contains the 9.10 iso you may be able to avoid the download.

---

### Post by dmata82 on 2010-04-28
Thank you bcbc,

So there is no way that wubi can use the image i downloaded, wubi must download its own image in order to keep with the installation.

Thank you for your answer

Daniel

---

### Post by bcbc on 2010-04-28
> **dmata82 said:**
> Thank you bcbc,

So there is no way that wubi can use the image i downloaded, wubi must download its own image in order to keep with the installation.

Thank you for your answer

Daniel

To be honest, I am not sure - usually I have installed using the CD, except when I tested the beta lucid - and in that case I ran wubi.exe and let it download the latest image.

As per the edit at the end of my last post, I would try first to run wubi.exe from the same directory as your downloaded image - I believe it will see the image and use it.

---

### Post by dmata82 on 2010-04-28
Ok, i will try at home and let you know how it went

Thank you

---

### Post by dmata82 on 2010-04-28
It Worked!

is installing the system now, i hope it runs good

Thank you very much again

Daniel Mata
Caracas-Venezuela

---

### Post by bcbc on 2010-04-28
> **dmata82 said:**
> It Worked!

is installing the system now, i hope it runs good

Thank you very much again

Daniel Mata
Caracas-Venezuela

Great! You're welcome :)

Don't forget the fix to the wubildr.

---

