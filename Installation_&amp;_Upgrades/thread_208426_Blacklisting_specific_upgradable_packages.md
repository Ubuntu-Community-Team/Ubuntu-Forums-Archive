---
title: "Blacklisting specific upgradable packages?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by ipaidforthisname on 2006-07-03
Hello,

I have had inordinate amounts of problems trying to get the fglrx drivers working in Dapper. Finally, after more work than I could have ever imagined, I was able to get the 8.24.8 fglrx drivers working. 

The problem now is that if I apt get upgrade or use adept updater, I am always prompted to upgrade my fglrx drivers. I could exercise extreme caution, but I have a feeling that one day I might accidently install those new fglrx drivers, which will, in turn, re-create the 'mesa' problem.

Is there any way I can permanently blacklist those upgrades so I am not constantly prompted to upgrade them?

Thanks!

---

### Post by tonyr on 2006-07-03
Yes, but it is not simple.  See **man apt_preferences** and the [APT Howto]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html"),
especially section **3.10**.

---

### Post by ipaidforthisname on 2006-07-03
Thanks!!

I went ahead and created the preferences file in /etc/apt/ 

Here are the contents of the preferences file
```
julian@julian-laptop:/etc/apt$ cat preferences
Package: fglrx-control
Pin: 8.24.8-1
Pin-Priority: 1001

Package: fglrx-kernel-2.6.15-25-386
Pin: 8.24.8-1+2.6.15-25.43
Pin-Priority: 1001

Package: fglrx-kernel-source
Pin: 8.24.8-1
Pin-Priority: 1001

Package: xorg-driver-fglrx
Pin: 8.24.8-1
Pin-Priority: 1001
```

Will they upgrade notifications go away, or will it just not allow those packages to be upgraded?

---

### Post by tonyr on 2006-07-03
I don't remember.  I used this a long time ago, and I can't recall what the notifications
were.

---

### Post by ipaidforthisname on 2006-07-03
Tonyr,

Thank you again!! I had to just add the word version in there, and now it says my system is up to date!

---

