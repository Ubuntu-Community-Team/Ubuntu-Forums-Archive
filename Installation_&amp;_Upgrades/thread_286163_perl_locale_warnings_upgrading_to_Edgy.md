---
title: "perl locale warnings upgrading to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by TheSqueak on 2006-10-27
I'm upgrading to edgy at the moment, and the upgrade process is throwing up an awful lot of the errors below:

```
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

This started just after the upgrade run had put the new version of perl on, is this something I should be worried about?

---

### Post by prkfriryce on 2006-10-27
The same is happening for me as well. I will let the upgrade complete and wait for a reply

---

### Post by pommattski on 2006-10-28
I'm in the process of upgrading right-now and I've seen this error fly by countless times...
Is it anything to worry about?

("en_AU:en" in my case though...)

---

### Post by em es on 2006-10-28
I upgraded yesterday and it showed those warnings too.

But after the installation was complete only the xserver was missing, I installed it using
```
sudo apt-get install xserver-xorg
```

But the Perl warnings didn't seem to trigger a reaction.

---

### Post by buddachile on 2006-10-28
I've noticed these perl locale errors during upgrades to dapper and edgy but have not noticed any ill effect.

---

### Post by ryan on 2006-10-28
> **buddachile said:**
> I've noticed these perl locale errors during upgrades to dapper and edgy but have not noticed any ill effect.

I had the same problem but by the time I finished the upgrade it got sorted out.

---

### Post by pufuwozu on 2006-10-28
It's nothing to be worried about, but if you want the messages to disappear:

```
sudo dpkg-reconfigure locales
```

---

### Post by JaRoLLz on 2006-11-13
I've got the same problem too. I've run:

```
sudo dpkg-reconfigure locales
```

many times, but I still got the same problem.
I cancel my upgrading to edgy because of that.

---

