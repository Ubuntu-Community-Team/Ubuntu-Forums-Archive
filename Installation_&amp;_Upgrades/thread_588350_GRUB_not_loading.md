---
title: "GRUB not loading"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Jyothisankar on 2007-10-23
I was having ubuntu on my computer ..... I tried to make it dual boot by installing Windows.... but after that GRUB is not loading..... computer is loading just to windows..... I have my important documents in ubuntu.... how can i repair this???
My hardware is 
pentium 4 processor
845GVSR chipset
768 MB RAM
One 40 GB hard disk
and other 160GB(Master) on which I installed Windows

---

### Post by dabang on 2007-10-23
Maybe this will help you:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Always install Windows first as it will overwrite your MBR.

Once booted back to Ubuntu add Windows to Grub by editing /boot/grub/menu.lst. Should look something like this:

```
# Boot Windows Vista
title           Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Adjust "(hd0,0)" to your Windows partition.

---

### Post by Jyothisankar on 2007-10-23
How can I boot back to Ubuntu? My system is  booting directly to Windows ...... i haven't seen GRUB after installing windows

---

### Post by meierfra on 2007-10-24
Your first need to reinstall grub by using the Ubuntu Live Cd and follow   the howto from the  link in  dabang's post. If you need help with that let  us know.

Alternatively you can use [Supergrub ]("http://supergrub.forjamari.linex.org/")to reinstall grub. Here is some more information on Supergrub: [Hemanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Jyothisankar on 2007-10-24
Thanks to both of you I solved the problem:)

---

