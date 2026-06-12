---
title: "Installing zsnes on nUbuntu"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by DanielSmith604 on 2006-11-03
I've used Ubuntu before (breezy badger) and was able to use synaptic to search for and install zsnes. Now I have nUbuntu (dapper) installed and I'm not able to find zsnes when I search for it.

I've included the following Repositories:
[LIST]
[*]dapper | main restricted (deb and deb-src)
[*]dapper-updates | main restricted (deb and deb-src)
[*]dapper | universe (deb and deb-src)
[*]dapper-backports | main restricted universe multiverse (deb and deb-src)
[*]dapper-security | main restricted (deb and deb-src)
[*]dapper-security | universe (deb and deb-src)
[/LIST]

I've also tried installing zsnes from the source but I can't use './configure' :-/

Any ideas? I'm a zsnes junkie ](*,)

---

### Post by philippe_carlo on 2006-11-03
> **DanielSmith604 said:**
> I've used Ubuntu before (breezy badger) and was able to use synaptic to search for and install zsnes. Now I have nUbuntu (dapper) installed and I'm not able to find zsnes when I search for it.

I've included the following Repositories:
[LIST]
[*]dapper | main restricted (deb and deb-src)
[*]dapper-updates | main restricted (deb and deb-src)
[*]dapper | universe (deb and deb-src)
[*]dapper-backports | main restricted universe multiverse (deb and deb-src)
[*]dapper-security | main restricted (deb and deb-src)
[*]dapper-security | universe (deb and deb-src)
[/LIST]

I've also tried installing zsnes from the source but I can't use './configure' :-/

Any ideas? I'm a zsnes junkie ](*,)

It's probably in the multiverse repository. 

dapper | multiverse (deb and deb-src)

I can see it from my edgy:
```

~$ apt-cache search zsnes
visualboyadvance - a full featured Game Boy Advance emulator
zsnes - Emulator of the Super Nintendo Entertainment System (TM)

```

---

### Post by DanielSmith604 on 2006-11-03
I get visualboyadvance but not zsnes :-/

```
~$ sudo apt-cache search zsnes
visualboyadvance - a full featured Game Boy Advance emulator
```

edit: oh ya and the dapper | multiverse Repository isn't available in my synaptic. Is there a way I can include it? This might be why.

edit2: fixed the problem. I had to add 2 repositories in synaptic:

[LIST]
[*]deb | [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) | dapper | multiverse
[*]deb-src | [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) | dapper | multiverse
[/LIST]

Thanks for giving me the clue that I didn't have multiverse! :D

---

