---
title: "Is there a way to reinstall Linux entirely using the command line?"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by acablue on 2011-03-10
My computer is a netbook with no optical drive. I had a friend bring over an external CD drive to burn the live CD, but I don't have that now. Since then, I've messed up my install beyond easy repair, so I was wondering if there was a simple (or perhaps not so simple) command that would reinstall every package from the software repositories (I do have access to the Internet, just no GUI). I'm talking about a clean install here.

---

### Post by Hedgehog1 on 2011-03-10
acablue,

Googled for "Reinstall Ubuntu From Command Line", and multiple sites say do this one line:

```
sudo dpkg-reconfigure -phigh -a
```

They say it takes about an hour to run.

***The Hedge***

:KS

p.s. Consider creating an Unstall USB to fall back on next time:   [www.pendrivelinux.com]("http://www.pendrivelinux.com/category/usb-installs-from-linux/")

---

### Post by acablue on 2011-03-10
Hrm, this is what I get instead:

```
dpkg-maintscript-helper: error: couldn't identify the package
```

I'm almost positive the original problem has something to do with my proprietary nVidia drivers. Uninstalled them, reinstalled them, to no avail.

I give up. I'm making a bootable USB stick.

Thanks for the tip, Hedgehog1.

---

### Post by Hedgehog1 on 2011-03-10
***Doctor Hedge*** recommends:

Take one **Ubuntu-On-A-Stick!** and call me in the morning.

***The Hedge***

p.s. I am not a real doctor.  In fact, I am not a real hedgehog, either. *My whole on-line life is a lie....*

:KS

---

