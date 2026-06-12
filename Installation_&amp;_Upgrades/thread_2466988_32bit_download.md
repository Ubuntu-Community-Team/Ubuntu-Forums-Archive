---
title: "32bit download"
date: 2021-09-12
forum: Installation &amp; Upgrades
---

### Post by in2media2 on 2021-09-12
i have an old dell latutde d520 that i want to use for my business paperwork etc, menu design , letters, flyers design and such like. now i have ubuntu 21.04 on my main laptop but its too big and bulky to carry with me on meeting so im wanting ubuntu or a flavor of on the dell. i have 21.04 but its 64bit. ive searched for 32bit but to no joy.

can anyone point to the 32 bit of an ubuntu (or flavor) please

---

### Post by GhX6GZMB on 2021-09-12
Last 32-bit distribution is 18.10
For a laptop that old, you'll probably need Lubuntu 18.04 or 18.10 (careful: first is LXDE, which is no longer supported, the second is LXQt, which is fully supported).

I think there are Debian distributions still supporting 32-bit, but others are more knowledgeable than me here.

---

### Post by Dennis N on 2021-09-12
> **in2media2 said:**
> ..Can anyone point to the 32 bit of an ubuntu (or flavor) please
As far as Ubuntu flavors, you have to go back to 18.04 releases to find any with some existing support. I know Ubuntu MATE has one - it's still on my own 32-bit laptop. The packages on it are no longer all supported - the majority are, however (see report below). If I were looking for something more recent and completely supported, check out this fairly-recent article:

[https://itsfoss.com/32-bit-linux-distributions/](https://itsfoss.com/32-bit-linux-distributions/)

From that list I would check out MX-Linux.

Support status for Ubuntu MATE 18.04
```
dmn@Kayleigh:~$ ubuntu-support-status
Support status summary of 'Kayleigh':

You have 1500 packages (78.5%) supported until April 2023 (Canonical - 5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 412 packages (21.5%) that are unsupported

```

Good Luck!

---

### Post by in2media2 on 2021-09-12
thanks guys, appreciate the help
gonna give mx a try. ive used it on my 64bit  and was impressed but didnt know they still supported 32bit

---

### Post by guiverc on 2021-09-12
As already stated.

Ubuntu 18.04 LTS provided i386 or 32-bit x86 ISOs, just not all options.

There was no Ubuntu 18.04 LTS Desktop ISO for example (just like 17.10 had no desktop ISO); but you could install using a different ISO & add the desktop, or upgrade to 18.04 and you got full support for the *life* of the product.  I'd personally not recommend running Ubuntu desktop on a x86/i386 though; I didn't like the experience on pentium 4/M/D boxes as *lighter* *flavor* desktops were just more *fun* and usable.

All *flavors* of Ubuntu had 32-bit or i386 ISOs.  Only Lubuntu & Xubuntu continued on with 18.10 releases, and didn't stop producing ISOs until mid-*disco* or 19.04 cycle; but if one of these was installed upgraded packages were provided the entire life of 19.04 too.  However as 18.10 & 19.04 were **not** LTS releases they reached EOL before 18.04 did.

Flavors only provided 3 years of support (Lubuntu Next was not a LTS so only had 9 months; I'd not recommend it on 18.04; likewise Ubuntu Studio was not a LTS with 18.04 so only had 9 too).

Use `ubuntu-support-status` as Dennis N suggested to check the security status of your system, ie. packages from 'universe' are already out of support; so you can decide how safe it will be for your intended use.

For non-Ubuntu; I'd recommend Debian as I saw also suggested. I QA-test Ubuntu *flavors*, and do the same with Debian, and used pentium M laptops in QA-testing the recent Debian Bullseye (11) (*my pentium 4 & D boxes refused to power on; PSU issues so I just used laptop/pentium M  devices which are less powerful anyway*).  Maybe of note:  I had 1 box that performed better with Lubuntu 18.04 LTS than Debian Buster (10); but that was a really under-powered celeron desktop (*pentium 4 version was subjectively equal between Lubuntu 18.04 & Debian 10*).

---

### Post by ActionParsnip on 2021-09-13
I'd go with Debian 32bit
[https://www.debian.org/CD/torrent-cd/](https://www.debian.org/CD/torrent-cd/)
(Using torrents adds extra data checking :P)

---

### Post by rsteinmetz70112 on 2021-09-13
Which processor does your Dell have? Some versions came with a Core 2 Duo which is 64 bit.

---

### Post by TheFu on 2021-09-13
> **in2media2 said:**
> thanks guys, appreciate the help
gonna give mx a try. ive used it on my 64bit  and was impressed but didnt know they still supported 32bit

I looked at MX yesterday.  It doesn't use systemd, so you'll need to learn the old init and runlevel methods. Nothing wrong with that, just need to be aware.
Also, they seem to put some commonly used tools into /usr/local/ ... which is a violation of standards.  Again, nothing wrong with it, but it means that distro isn't nearly so compatible with Ubuntu as many would suggest.

There are a few little things that MX has done, probably for security reasons, that have been addressed in different ways in Debian and Ubuntu releases.  For example, ping requires sudo to work on MX.  They elected not to just apply the cgroup for network controls on the ping command so any user can use ping.  

There are probably a number of other little items like that which are different.

A few people in my LUG are MX users and they really like it.

---

