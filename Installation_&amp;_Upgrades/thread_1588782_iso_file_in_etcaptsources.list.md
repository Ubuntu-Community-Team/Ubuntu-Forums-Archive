---
title: "iso file in /etc/apt/sources.list"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by prudra on 2010-10-05
In my netbook /etc/apt/sources.list contains the cdrom as

deb cdrom:[Ubuntu ....]/hardy main restricted

If I keep the iso file in /ubuntu and then want it to be refreshed during #/etc/apt/apt-get update
how must I motify /etc/apt/sources.list  ?
Thanks.
P.Rudra.

---

### Post by XeonBloomfield on 2010-10-05
You can comment on the cost, that is, add a # before the rest.

It will look like:
# deb cdrom:[Ubuntu ....]/hardy main restricted

After it all necessary files will be downloaded from the Internet, and not every time will be scanned disk.

---

### Post by prudra on 2010-10-06
> **XeonBloomfield said:**
> You can comment on the cost, that is, add a # before the rest.

It will look like:
# deb cdrom:[Ubuntu ....]/hardy main restricted

After it all necessary files will be downloaded from the Internet, and not every time will be scanned disk.

Sorry, I didn't make myself clear. I meant that I copy the ubuntu-10.04-.....iso image in the hard disk at 
/ubuntu/ and then modify the source.list file to refresh this during update.

In opensuse I did this by copying  the .iso image at /suse/CD1/ and modifying the source.list file:
file:///suse/CD1/

This has become necessary because while upgrading my ubuntu-8.04 to ubuntu-10.04 via net and
then replacing hardy by lucid in the sources.list and upgrading has removed lots and lots of files along with installing the new packages. This has made my netbook a complete wreck and only the black screen
rescue mode can be operated upon. The network connection cannot be reached. I have now made the
installation-usb for lucid by the $dd if=ubuntu......iso of=/dev/sda bs=4M in my other laptop and plan to
copy it in the netbook and run #apt-get update.

Help is absolutely essential.
Thanks.
P.Rudra.

---

### Post by zpliang on 2010-10-08
[http://ubuntuforums.org/archive/index.php/t-35807.html](http://ubuntuforums.org/archive/index.php/t-35807.html)
may help you.
to get apt-get get it from /etc/sources.list,you have to add something like
<code>
deb file::///mnt/iso lucid main restricted
</code>

---

### Post by dino99 on 2010-10-08
installing directly from iso:

[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fwww.jellykernel.org%2Fgeek%2Finstaller-ubuntu-sans-cd-ni-cle-usb-ubuntu-netinstall%2F](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fwww.jellykernel.org%2Fgeek%2Finstaller-ubuntu-sans-cd-ni-cle-usb-ubuntu-netinstall%2F)

---

