---
title: "Upgrading to 10.04 - broken system"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by Megistos on 2010-06-19
Hi guys,

I avoided upgrading to 10.04 when it was initially released because I couldn't afford for anything to go wrong with my computer around exam time. Sure enough, when I decided to upgrade today, the process got about halfway through and then gave me an error and left me with an unbootable system except in a recovery terminal.

In this terminal I discovered that most of the packages the upgrade wanted to configure depended in some way on shared-mime-info or desktop-file-utils. Configuring these with dpkg --configure gives me an error along the lines of:
```
undefined symbol: g_malloc0_n
```

and an error code of 127. So, dpkg leaves those packages and consequently can't configure many of the subsequent packages in the dist-upgrade.

Anyone know what's going on? Any help would be very much appreciated as it would be nice to be able to avoid the hassle of reinstalling the OS.

Thanks!

---

### Post by soadrocks79 on 2010-06-19
yes the same thing happened to me as well. Is this a common problem?

---

### Post by kansasnoob on 2010-06-19
Are you able to boot the system at all?

Did you upgrade from 8.04?

Or from 9.10?

What's the latest "known good" version of Ubuntu Live CD (or Live USB) you have available?

Do you multi-boot?

---

### Post by soadrocks79 on 2010-06-19
Im not able to boot the system at all. I upgraded from 9.10. THe last cd i have i think was from 8.04. THis is the first time this problem has ever happened. I am multibooting thankfully because it allows me to check these forumns and then try solutions very quickly.

---

### Post by kansasnoob on 2010-06-20
> **soadrocks79 said:**
> Im not able to boot the system at all. I upgraded from 9.10. THe last cd i have i think was from 8.04. THis is the first time this problem has ever happened. I am multibooting thankfully because it allows me to check these forumns and then try solutions very quickly.

So, what OS are you multi-booting with? Another Ubuntu? 

If you have another Ubuntu OS installed you could mount and chroot the "sick" OS from it, or you could do it from your 8.04 Live CD.

The basic procedure is explained here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course a lot of this depends on your skill level, but if you can successfully mount and chroot the proper partition(s) I'd begin with:

```
apt-get clean
```

```
apt-get update
```

```
apt-get dist-upgrade
```

And at any time the following may be useful:

```
apt-get -f install
```

```
dpkg --configure -a
```

Quite often the terminal output will reveal what steps need to taken next. If you need more detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by revhead347 on 2010-06-20
Just upgaded to 10.04 last night, and I haven't had any problems.  Yet......

Kurt

---

