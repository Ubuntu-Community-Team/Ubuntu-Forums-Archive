---
title: "Help! Unity panels lost"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by nibal on 2014-03-22
I use Ubuntu 13.10 64x desktop. Neither the ubuntu package nor the latest stable from wine ppa did what i wanted to, so i opted for the latest ppa release. Crashed my Xserver. Tried removing it, but it took half of my distro along with it. Is this a bug? I don't remember installing all these files when installing wine. Since then i replaced most of my applications. However, when I logged in again, I didn't have my unity side and top panels. Furthermore, while I am getting my desktop, I cannot run X-applications in it (gnome-teminal, browser, etc.). I suspect something wrong with my gnome Xsession. I use Ubuntu 10.36 64x Desktop

 The only relevant errors I can find in the logs are from /var/log/lightdm/x-0-greeter.log:

```


(at-spi2-registeryd:1167):WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.ServiceUnknown: The name org.gnome.SessionManager was not provided in any .service files
(at-spi2-registeryd:1167):WARNING **: Unable to register client with session manager
.
.
.
(gnome-settings-daemon:1187): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.ServiceUnknown: The name org.gnome.SessionManager was not provided in any .service files

```

Also the only unity component running is:
```

$ pgrep -fl unity
1844 /usr/lib/unity/unity-panel-service

```

 Although I have the other unity components installed, application-lens, files-lens etc., they do not run, because of the same gnome Xsession problem. Can i fix it, or should i reinstall Ubuntu from scratch? :(

TIA

---

### Post by nibal on 2014-03-23
> **nibal said:**
> 
 Although I have the other unity components installed, application-lens, files-lens etc., they do not run, because of the same gnome Xsession problem. Can i fix it, or should i reinstall Ubuntu from scratch? :(

TIA

Too late. Reinstalled Ububtu 13.10 and swore off wine. Problem was that I had a custom kernel to see my metwork, so i couldn't get any updates during installation. And had to compile kernel sources and driver, before any updates, which was a mess for 10/36 (screen flickering, and various system settings not working...). Anyway, now it is fine and all is well that ends well ;-)

---

