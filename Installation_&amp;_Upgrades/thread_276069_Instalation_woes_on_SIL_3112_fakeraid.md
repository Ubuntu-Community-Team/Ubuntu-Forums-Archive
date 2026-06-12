---
title: "Instalation woes on SIL 3112 fakeraid"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by Juzz on 2006-10-12
Hiyas,

I am going out of my skin here ](*,) 

I am following the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") and I can follow it untill I have to chroot to the newly created environment - but when I need to install dmraid, something goes wrong.

I think I have the problem nailed down to the fact that there is nothing below /sys and dmraid wants to look at stuff in /sys/block.

the raid setup isn't detected after dmraid install (most probably due to the error above).

What can I do - I really need to get this thing going as I have other projects I need to get done before the weekend.

I'd really like to have Ubuntu on the machine, but I am running out of time here :neutral:

Does anyone know of a way to get /sys populated with the things that dmraid misses?

---

### Post by Juzz on 2006-10-12
I scrolled *waaaay* down and saw the troubleshooting dmraid - and remounted /dev /sys and /proc - and now it works...

I'll investigate how much further I can get now... ;)

---

