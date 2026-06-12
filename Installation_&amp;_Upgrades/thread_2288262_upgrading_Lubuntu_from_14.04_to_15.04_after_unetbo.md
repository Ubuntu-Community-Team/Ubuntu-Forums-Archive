---
title: "upgrading Lubuntu from 14.04 to 15.04 after unetbootin installation"
date: 2015-07-25
forum: Installation &amp; Upgrades
---

### Post by rgoulet on 2015-07-25
When upgrading I received this message several times:

> GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 148.

After upgrading, I used apt-get --reinstall install ubuntu-desktop and apt-get --reinstall install lubuntu-desktop and I didn't receive the message again.

Now (once in a while) I'm getting a message that "Ubuntu has had an internal error" and I have chosen to send the information about the error.
Everything seems to be working fine... :x

Also, I haven't actually tried to run the command gdk-pixbuf-query-loaders, but to install it I have to install many dependencies and libgdk-pixbuf2.0-dev.
I'm wondering if I should...

---

### Post by dino99 on 2015-07-26
if your installation is Lubuntu, then only lubuntu-desktop is required (as a metapackage) but dont confuse your system by installing an other desktop (ubuntu-desktop in your case, as you may fight against versions conflicting and unattented crossed dependencies)

---

### Post by rgoulet on 2015-07-26
When I tried running gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache, I was told:
> bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied

I tried it as a user and using sudo.

---

### Post by rgoulet on 2015-07-27
> dont confuse your system by installing an other desktop
When I upgraded, a large amount of packages were installed, but I got that message that my installation was probably broken so I thought that it was trying to upgrade ubuntu-desktop but was missing files since only LXDE was installed. So, I tried reinstalling ubuntu-desktop to see if I got those messages when installing Ubuntu instead of Lubuntu, and it did seem to work, since I didn't receive that message again. But, like I said, now every so often it says that Ubuntu has experienced an internal error. I choose to send the information and everything seems to continue working like it should, but I'm not sure what exact problem I'm having.

---

### Post by rgoulet on 2015-07-30
> dont confuse your system by installing an other desktopWell, I didn't install ubuntu-desktop until I received the messages. Also, I guess I might as well say that this is on an ASUS laptop (K55A). I had some trouble installing Linux at all, since it came with secure boot, which I didn't know about. Luckily, I had openSUSE and I could install it and then use unetbootin from there to install Debian/Ubuntu/Lubuntu. :D

---

### Post by rgoulet on 2015-08-01
When I updated my software, it said software has been updated since 15.04 release and updated some software, but when I checked under the software updater settings it said that I'm downloading updates for 14.04 instead of 15.04. All my software downloading when I was downloading using the updater I originally used and looking at the details said Trusty.

:mad:

---

### Post by rgoulet on 2015-08-02
Never mind. Under software updater and apt-get update / apt-get upgrade it says Vivid. 15.04 (Vivid Vervet).

---

