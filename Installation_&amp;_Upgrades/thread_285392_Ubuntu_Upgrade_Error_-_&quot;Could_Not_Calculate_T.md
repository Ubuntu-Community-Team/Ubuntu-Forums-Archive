---
title: "Ubuntu Upgrade Error - &quot;Could Not Calculate The Upgrade&quot;"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Chicken001 on 2006-10-26
"Not all updates can be installed"

This is an error message I get, I have installed Ubuntu 6.10 already. But, I was curious so I opened up Update Manager again.

Well, whatcha know, I got this error message. It claims that not all the upgrades can be installed, and it suggests for me to do a distribution upgrade, which I did in the first place. 

So, sure why not I clicked Check, since it said it didn't upgrade fully. It gave me the error, which resulted in the face of, xO, and then, I cried.

Well, that is also, just part of it, because I did type

```
sudo apt-get -f install
sudo dpkg --configure -a
```

Which it missed, one package, so I installed it. Walla! Supposed to work right? Same error. The whole installation caused me to be in great grief because I don't want to install this over again. 

Oh yeah, btw, I have changed the /etc/apt/sources.list File because it was  being gay before anyways. The problem was fixed, until I upgraded it. More problems. Everything works though, everything looks a bit different since the upgrade, but, update isn't working.

Anyone gots a clue? If so thanks!

](*,)

---

### Post by Chicken001 on 2006-10-26
Oh yeah, this is an upgrade from 6.06

---

### Post by orb9220 on 2006-10-26
"Not all updates can be installed"

Has happened more thant once during my using edgy the last month.
This is a problem on their end and usally goes away in a day or two.

Plus this is a bad time to upgrade because everybody and their grandmother are banging the server's within an inch of their Life.

If you wait a day or two then things should get a bit better.

---

