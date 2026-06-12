---
title: "Why in new version(Ubuntu 16.04.2) display this: &quot;sudo: apt&#8208;get: command not found&quot; ?"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2017-02-19
Why in new version(Ubuntu 16.04.2) display this: "sudo: apt&#8208;get: command not found" ?

example: "ubuntu@ubuntu:~$ sudo apt&#8208;get remove skype skype&#8208;bin 
sudo: apt&#8208;get: command not found"

---

### Post by lisati on 2017-02-19
It's possible that you've discovered one of the changes introduced in recent months (years?). You might want to look into using [apt]("https://help.ubuntu.com/lts/serverguide/apt.html") instead of apt-get.

---

### Post by spi2 on 2017-02-19
hello, ok is apt, thanks, and one question yet, how in new version I install Skype?

---

### Post by howefield on 2017-02-19
> **spi2 said:**
> hello, ok is apt, thanks, and one question yet, how in new version I install Skype?

Ordinarily you would have 2 methods, first would be to enable the Canonical Partners repository and install from the Software Centre or terminal

```
sudo apt install skype
```

or you could install the [Skype for Linux Alpha]("https://community.skype.com/t5/Linux/Skype-for-Linux-Alpha-and-calling-on-Chrome-amp-Chromebooks/td-p/4434299") which is the newer version but still has the alpha moniker. It does seem to work well.

Problem with the first method is that Microsoft are apparently about to kill off the older skype clients.

[https://blogs.skype.com/news/2017/02/03/the-skype-you-love-is-getting-better-download-it-for-free-today/](https://blogs.skype.com/news/2017/02/03/the-skype-you-love-is-getting-better-download-it-for-free-today/)
[http://www.windowscentral.com/older-versions-skypes-desktop-app-will-stop-working-march-1](http://www.windowscentral.com/older-versions-skypes-desktop-app-will-stop-working-march-1)

---

### Post by spi2 on 2017-02-19
hello, I have download Skype, but display:
sudo apt install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype

---

### Post by howefield on 2017-02-19
You would only use 

```
sudo apt install skype
```

if you have enabled the Canonical Partners repository and are installing from there.

If you have downlaoded a deb package from somewhere, you could still use apt but would need to use the path to the deb package, for instance..

```
sudo apt install ~/Downloads/skypeforlinux-64-alpha.deb
```

Change path to package and name of package to suit.

---

### Post by oldos2er on 2017-02-19
*apt-get* should still be available for you to use; it is on 16.10. What is the result of ```
which apt-get
``` ?

---

