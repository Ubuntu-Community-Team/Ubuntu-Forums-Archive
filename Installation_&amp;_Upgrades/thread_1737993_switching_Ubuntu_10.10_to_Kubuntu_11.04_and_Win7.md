---
title: "switching Ubuntu 10.10 to Kubuntu 11.04 and Win7"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by HappyLinux on 2011-04-24
I'm currently running a dual-boot system with Windows7 and Ubuntu 10.10. This means that I use the GRUB loader to switch between them.

However, because I don't like Ubuntu 11.04 because of Unity, I'm quite happy to switch to Kubuntu 11.04.

However, because I'm also running Windows7, this can prove to be a problem. Typically, I could backup my data in Ubuntu and then do a clean install of Kubuntu (reformatting partitions where necessary.)

If I do a clean install of Kubuntu over Ubuntu, would it replace/upgrade GRUB and keep the listings or would I need to reinstall Windows 7?

I'll be waiting a month before moving to Kubuntu, but I basically need to know as I can only Activate Windows 7 so many times before it starts telling me to make phone calls to get new product keys etc. I really hate Microsoft for that, but I cannot completely move away from them for various reasons.

---

### Post by marin123 on 2011-04-24
you could upgrade to kubuntu, but that might fail. if it does, just reinstall kubuntu 11.04 and grub will have win 7 as boot option.

you can install kde on existing ubuntu installation:
```
sudo apt-get install kubuntu-desktop
```

you will get all default apps in kde and you will be able to choose between sessions (gnome or kde).

and if you want to remove gnome after installing kde you can:
```
sudo apt-get remove ubuntu-desktop
```

---

### Post by HappyLinux on 2011-04-24
Cheers.

---

### Post by HappyLinux on 2011-04-28
Just to quickly clarify. If I do a clean install of Kubuntu over Ubuntu and install GRUB, I won't have to reinstall Win7? GRUB will simply update with the newer version (presuming there is a newer version) or completely replace whilst recognising that Win7 is there and add it to the list.

It's just that I'm going to do a clean install of Kubuntu and don't want the hassle of redoing Win7 whilst I'm at it.

---

### Post by marin123 on 2011-04-28
yes, just dont touch windows partition and install kubuntu to same parition where ubuntu was. when you do install, grub is also installed and it will see windows installation...

---

### Post by Hedgehog1 on 2011-04-28
While you are very welcome to load Kbuntu, you can load Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by HappyLinux on 2011-04-29
I've done a successful clean install of Kubuntu 11.04 without having to redo Win7. There are some problems which I've started at least 1 new thread over.

So with my thanks, I'm marking this thread as done.

---

