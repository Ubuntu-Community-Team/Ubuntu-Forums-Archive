---
title: "Question on upgrading from Feisty to gutsy re: grub"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Snort on 2007-11-01
Hello

I installed Ubuntu 7.04 in a rather unconventional manner, because the computer I am working from cannot boot from either of its optical drives. I used Wubi, then LVPM to turn it into a dedicated partition.

The problems came up when LVPM failed to install GRUB successfully. I thus had no access to my new ubuntu install. I eventually fixed that with wingrub. Now my bootup is like this: NTLDR loads and gives me the option to go either to windows or grub. I select grub, and then have the option to boot up ubuntu.

So, my question is, how will upgrading that ubuntu install change what I see when I boot? Will it work correctly (i.e. will I be able to boot both windows and ubuntu?)? Does the upgrade install GRUB the normal way? Basically, I am worried that I won't be able to get in to one OS or the other after upgrading. I barely understand how GRUB works, and I am a linux noob, so please word your answers accordingly:).

Thanks to all

---

### Post by louieb on 2007-11-01
Whats LVPM? 
The only thing the upgrade did on mine was replace the Feisty entry with a Gutsy entry in my  Grub menu.

---

### Post by Snort on 2007-11-01
[LVPM]("http://lubi.sourceforge.net/lvpm.html") is for turning the loopmounted wubi install into a real partition.

---

