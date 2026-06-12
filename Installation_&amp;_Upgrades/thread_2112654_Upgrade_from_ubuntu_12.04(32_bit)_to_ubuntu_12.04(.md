---
title: "Upgrade from ubuntu 12.04(32 bit) to ubuntu 12.04(64 bit)"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by jebaearnest on 2013-02-05
I just want to Upgrade from ubuntu 12.04(32 bit) to ubuntu 12.04(64 bit).


Please suggest me if the option is available.

Else i want to install the fresh ubuntu 12.04(64 bit) from **TERMIAL**.

Suggest me either with commands or any URL.

---

### Post by ibjsb4 on 2013-02-05
You must reinstall, you cannot upgrade to 64 bit.

---

### Post by dino99 on 2013-02-05
you cant upgrade in that case to get a 64 install; you need to install from scratch.

---

### Post by jebaearnest on 2013-02-05
OK. 

Can you Please send me the commands to do the Fresh installation from terminal if available.

---

### Post by dino99 on 2013-02-05
here is how to do (note: instead of that old howto talking about "alternate" iso, which is now deprecated, download the the normal iso, prepare your partitions, then install using the "Something Else" option into the installer)

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by ibjsb4 on 2013-02-05
You keep referring to terminal install.  Are you using the mini or server iso?

You still need to download the 64 bit version.

Maybe this will help you.

[https://help.ubuntu.com/12.04/installation-guide/amd64/index.html](https://help.ubuntu.com/12.04/installation-guide/amd64/index.html)

---

### Post by m3topaz on 2013-02-05
In the past, I ran 32-bit Ubuntu and "upgraded" (read: re-installed) to 64-bit.

With a separate home folder, it's a clean install where you don't re-format /home when you run the 64-bit installer.

To get a list of your installed apps, before you start and to make use of the new installation easier, grab the output of this first:

         $ sudo dpkg --get-selections

Only problems on re-install were related to ia32 libs, most of which are fixed and have workarounds nowadays.

---

