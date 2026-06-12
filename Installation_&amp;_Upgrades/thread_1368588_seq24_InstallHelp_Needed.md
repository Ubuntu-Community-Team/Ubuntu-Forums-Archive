---
title: "seq24 Install:Help Needed"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Gomeriffic on 2009-12-30
So, I am trying to install seq24 from source since it is spontaneously closing when I use the install from the repos. I retrieved the source, used the ./configure after I navigated to the extracted folder, and came up with this:

```
configure: error: Package requirements (gtkmm-2.4 >= 2.4.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the DEPS_CFLAGS and DEPS_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```
I went ahead and did as usual when I installed dependencies and tried:
```
sudo apt-get install gtkmm-2.4.0
```
There is no package, so I googled the file and came up with nothing.

Help would be greatly appreciated.

---

### Post by lolbot on 2010-01-09
Hi!
Have you found any solution? I also noticed spontaneously closing and think about compile seq24 from source. I have Ubuntu Karmic.

edit: Better forum section for this thread is Multimedia Production.

---

### Post by Gomeriffic on 2010-01-09
> **lolbot said:**
> Hi!
Have you found any solution? I also noticed spontaneously closing and think about compile seq24 from source. I have Ubuntu Karmic.

edit: Better forum section for this thread is Multimedia Production.

Actually, since I was using Jaunty, I decided to update to Karmic, regardless of my Gnome-Do problem. After reinstalling, I actually got Seq24 to work!!! Only problem, the tools portion doesn't work.

---

### Post by lolbot on 2010-01-10
> **Gomeriffic said:**
> Actually, since I was using Jaunty, I decided to update to Karmic, regardless of my Gnome-Do problem. After reinstalling, I actually got Seq24 to work!!! Only problem, the tools portion doesn't work.

Thanks. I`ll look deeper in my setup and maybe will find what`s wrong.

---

### Post by Gomeriffic on 2010-01-10
> **lolbot said:**
> Thanks. I`ll look deeper in my setup and maybe will find what`s wrong.

I am using Karmic, 32 bit, Compaq Presario V2000.

---

