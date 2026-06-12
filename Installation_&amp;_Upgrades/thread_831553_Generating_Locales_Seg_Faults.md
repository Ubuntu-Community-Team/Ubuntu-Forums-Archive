---
title: "Generating Locales Seg Faults"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by Hellfire51 on 2008-06-16
I have an Ubuntu 8.04 (x64) box that I haven't booted for a while. I am transition from an older computer to this one, and I needed to apply several updates. I ran the usual apt-get update, apt-get upgrade and apparently one of the package updates (not sure which) wants to regenerate Locales. Problem is, every time it tries to do this, the computer freezes. Then I attempt to run dpkg --configure -a to get apt-get working again, same deal. I ran a dpkg --remove --pending in order to try again with apt-get, to no avail.

I believe I have just the default UTF-8 english locale set.
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
etc...

On occasion, it will get past one (with a failure) and get to maybe the second one down the list. Usually it just locks up at that point, otherwise it Seg Faults, and on one occasion it said "memory exhausted"

This is not a low-end system, until a few months ago it was my gaming PC.

AMD 3500+ (x64)
2GB RAM
200GB Hard Drive

---

### Post by Hellfire51 on 2008-06-17
*bump*

I still haven't figured this out. Anybody able to help? Thanks.

---

### Post by Hellfire51 on 2008-06-18
I went though all of my installed language-pack packages. I found that by removing:

language-support-translations-en
language-pack-en-base
language-pack-en

the problem no longer occured (because I no longer had any locales)

Now it is falling back to "C" locale. I still would appreciate any help getting these packages to work, since I am concerned that they may be dependencies for things in the future.

---

