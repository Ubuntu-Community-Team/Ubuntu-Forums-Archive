---
title: "Ubuntu installation help?"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by revomutharock on 2011-02-11
Hi guys 

I have been having issues when trying to boot ubuntu 10.10 I get this screen and cannot make any progress. [http://img833.imageshack.us/i/1297446955428orig.jpg/](http://img833.imageshack.us/i/1297446955428orig.jpg/)

Any ideas?

Many Thanks

Steve

---

### Post by Quackers on 2011-02-11
Welcome to UF.
That's a kernel panic. What hardware are you installing to?
You may need to use a boot option. When booting from the Live cd, at the first purple screen (with the little man icon at the bottom) press Esc key. Then choose language and on the next screen press F6 key. Some options will appear. You may need to select acpi=off, or one or more of the other acpi related options to progress.

---

### Post by revomutharock on 2011-02-11
Well I am impressed that solved the problem cheers :D I do have a few more questions if you don't mind me asking. Now that I have turned of acpi will ubuntu remeber that when I boot again? Also noticed that when I use my multitouch pad. It seems to be all over the place with ubuntu will I need a driver for that? And finally I previously tried installing ubuntu via usb and wubi and had the same issue so I assume this would be resolved now?

---

### Post by Quackers on 2011-02-11
Whichever option you chose will need to be used again the first time you boot the installation. If that works ok, you can make the change permanent using the guide below.
I'm afraid I have no idea of any impact this may have on your hardware, although it is likely that there will be some. There are some details in the guide.
Maybe others with more experience of this will give you more details.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by revomutharock on 2011-02-11
Cheers one more thing with the multitouch pad I noticed that vertical scrolling is disabled is that just because I'm running a live cd?

---

### Post by revomutharock on 2011-02-11
Two fingered scrolling my mistake XD

---

### Post by Quackers on 2011-02-11
I don't know about that. As I said, turning acpi off will have an impact. How much of an impact I don't know.

---

