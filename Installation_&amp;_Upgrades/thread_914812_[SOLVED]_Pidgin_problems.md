---
title: "[SOLVED] Pidgin problems"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by SecurityCop on 2008-09-09
So I am trying to install pidgin and I have had 6 problems so far. 5 I have managed to solve, but the sixth solution is eluding me.
Heres what I get.
```
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.

```

Any help?

---

### Post by Partyboi2 on 2008-09-09
trying installing libxss-dev package.
Pidgin is in the ubuntu repo's and is installed by default if you are using gusty or hardy.

---

### Post by JasonSpradlin82 on 2008-09-09
I was having the same problem installing Pidgin 2.5.1, but this fixed it.

---

### Post by SecurityCop on 2008-09-09
Ok that did fix one problem, but now something else came up. And as painfully obvious as it is after this post, I'm going to say it anyways. I barely have any clue what I am doing.

```
X session management development headers not found.
Use --disable-sm if you do not need session management support.

```

I did try Use --disable-sm, and a few others, but I really am bad at this.
And I guarantee this isnt my last post in this thread.

---

### Post by Partyboi2 on 2008-09-09
maybe try installing libsm-dev package

---

### Post by SecurityCop on 2008-09-09
```
Startup notification development headers not found.
Use --disable-startup-notification if you do not need it.

```

**** life.

---

### Post by Partyboi2 on 2008-09-09
install the libstartup-notification0-dev package

---

### Post by SecurityCop on 2008-09-09
```
GtkSpell development headers not found.
Use --disable-gtkspell if you do not need it.

```

Im sorry for not knowing what I am doing and using up your time, but this is friggen impossible to learn in 2 days.

---

### Post by Partyboi2 on 2008-09-09
You are not using up my time, happy to help :) for that one install these 2
libaspell-dev libgtkspell-dev

---

### Post by SecurityCop on 2008-09-09
Well I am thanking you in every post, and thanks again. I plan on reading the tutorials when I have a break from school and work.

```
You must have libxml2 >= 2.6.0 development headers installed to build.

```

---

### Post by Partyboi2 on 2008-09-09
you need libxml2-dev

Edit: Here are a few more you will need installed
libavahi-client-dev
 libavahi-glib-dev 
libdbus-glib-1-dev 
libgstreamer0.10-dev 
tk8.4-dev
tcl8.4-dev
libperl-dev
network-manager-dev
libmeanwhile-dev

Let me know if you get stuck again.

---

### Post by SecurityCop on 2008-09-09
Well I made it a hell of a lot further this time.

```
Neither GnuTLS or NSS SSL development headers found.
Use --disable-nss --disable-gnutls if you do not need SSL support.
MSN, Novell Groupwise and Google Talk will not work without GnuTLS or NSS. OpenSSL is NOT usable!

```

Thanks for all of this man.

---

### Post by Partyboi2 on 2008-09-10
try libnss3-dev

---

### Post by SecurityCop on 2008-09-10
> **Partyboi2 said:**
> try libnss3-dev

There is no package that is called libnss3-dev.

```
krystle@krystleslaptop:~$ sudo apt-get install libnss3-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libnss3-de
```

---

### Post by Partyboi2 on 2008-09-10
What version of ubuntu are you using? libnss3-dev is available for feisty, gusty, hardy.

Edit: you may also need to install libgnutls-dev

---

### Post by SecurityCop on 2008-09-10
So that was the last one. Oh and I have Ubuntu 6.06 LTS. The reason I had to go through all of this is because they didn't code pidgin for 6. So I had to do this for the first time. But thanks man, I owe ya big time.

---

### Post by Partyboi2 on 2008-09-10
your welcome :)

---

### Post by SecurityCop on 2008-09-10
Ok so I configured it, and then typed in make. Now what do I do? Theres nothing installed but at the same time it must have done something , amirite?

---

### Post by Partyboi2 on 2008-09-10
If make passed with no errors
install it with
```
sudo make install
```

---

### Post by SecurityCop on 2008-09-10
> **Partyboi2 said:**
> If make passed with no errors
install it with
```
sudo make install
```

Thanks again man. I'm pretty sure that's all I need.

---

### Post by titotti32 on 2011-01-13
i have same problem.
i disable something when configure them
i need to enable it

```
tito@tito:~/Downloads/pidgin-2.7.9$ ./configure --disable-screensaver  --disable-startup-notification --disable-gtkspell --disable-gstreamer  --disable-vv --disable-idn --disable-meanwhile --disable-avahi  --disable-nm --disable-perl --disable-nss --disable-gnutls --disable-tcl
```

what should i install before configure pidgin?

---

