---
title: "Alternatives to &quot;Ubuntu Tweak&quot; or how to commands instead"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by AfrikaDietmar on 2016-10-11
Hi,

it's not possible anymore do install the software Ubuntu Tweak via PPA on the latest Ubuntu versions, it's also not supported. I still have one running on my Ubuntu Mate 16.04 and it's Janitor function is very handy to make space for new updates. Such as to remove apt cache, old kernels, package configs and unneeded packages (See Screenshot). Do you know any good alternatives to Ubuntu Tweak that offer similar functions? Is there a possibility I can copy it from my PC and install it on others? ...or will I need a list of terminal commands to carry out such clean ups? 

Best regards from Sunny Mauritius!

---

### Post by howefield on 2016-10-11
Sounds like Bleachbit might be what you are looking for ?

[https://www.bleachbit.org/](https://www.bleachbit.org/)

Have a look at that site to make sure and it can be installed via the Software Centre or terminal.

---

### Post by oldos2er on 2016-10-11
Clear your apt cache with ```
sudo apt clean
``` ```
sudo apt autoremove
``` should remove old kernels on 16.04.

---

### Post by AfrikaDietmar on 2016-10-12
Would it make a difference if I use **apt-get** instead of just **apt**? 

What does ```
sudo apt-get autoclean
``` do?

Is it possible to remove old config files with this command or not recommended?
```
dpkg -l | grep ^rc | cut -d' ' -f3 | xargs sudo dpkg --purge
```

---

### Post by howefield on 2016-10-12
> **AfrikaDietmar said:**
> Would it make a difference if I use **apt-get** instead of just **apt**? 

No, apt is the newer form of apt-get. The two are almost interchangeable in 16.04.

See man apt and man apt-get for more details. Open a terminal and type eg,

```
man apt-get
```

> What does ```
sudo apt-get autoclean
``` do?

From man apt-get

> autoclean (and the auto-clean alias since 1.1)
           Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes
           package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long
           period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from
           being erased if it is set to off.

> Is it possible to remove old config files with this command or not recommended?
```
dpkg -l | grep ^rc | cut -d' ' -f3 | xargs sudo dpkg --purge
```

Yes, it's possible.

---

