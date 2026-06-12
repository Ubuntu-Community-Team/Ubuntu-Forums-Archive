---
title: "Flash for Firefox broken"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by jtgd on 2011-05-24
Running 10.4 64-bit; XFCE; Firefox 4.0.1; flash 10.2

Flash used to work fine but now it's broke. I think it may have been after trying to upgrade java, but not sure why that would affect it. I follow all the instructions I can find for installing flash (and there are MANY variants) and nothing works.

I have installed from flashplayer10_2_p3_64bit_linux_111710.tar.gz
and copied to /usr/lib/mozilla/plugins/libflashplayer.so
but Firefox says there is no plug-ins installed.
I don't see how to get Firefox to see it.

Firefox 4 was installed from zip and lives in my ~/Installs/firefox4b11 directory. I run it directly from there. That directory has no /plugins/ directory, so I can't copy anything there.

(FWIW, abrowser and Opera work fine with flash)

Does anyone know how to properly install flash and make Firefox see it? 
Thanks in advance.

---

### Post by lovinglinux on 2011-05-25
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. 

Since you are using a custom location for firefox binaries, you need to create a symlink from the system plugins folder to your current installation.

After running the Flash-Aid wizard, do this:

```
sudo ln -s /usr/lib/mozilla/plugins ~/Installs/firefox4b11/plugins
```

---

### Post by jtgd on 2011-05-29
Thanks much, love, that fixed it.  You rock!

---

### Post by lovinglinux on 2011-05-29
> **jtgd said:**
> Thanks much, love, that fixed it.  You rock!

You are welcome.

---

### Post by VanR on 2011-05-29
Doesn't work quite as well on firefox 5 though. Still glitchy.

---

