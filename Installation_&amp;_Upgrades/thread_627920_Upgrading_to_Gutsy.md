---
title: "Upgrading to Gutsy"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by FRuMMaGe on 2007-11-30
Well, after 6 months of Dapper, I am finally ready to upgrade to Gutsy.

One question though, is the hardware compatibility better or worse?

I would like the turnover to be as smooth as possible.

Also, is there a way I can quickly reinstall all the programs I have on my current system? Or at least list them all so I can do it again myself.

---

### Post by FRuMMaGe on 2007-12-01
bump

Please help

---

### Post by Mateo on 2007-12-01
The programs will automatically upgrade themselves, no need to reinstall them.

sudo apt-get dist-upgrade is all you need.

By the way, I've had kinks every single time i've upgraded so hoping there won't be any might be asking too much.  Maybe others have been more lucky though.

---

### Post by maniacmusician on 2007-12-01
If you've installed programs from third party repositories (such as the ones for beryl and compiz) or installed stuff from automatix that's from third party repositories, you almost certainly will have kinks. I would recommend backing up your data, wiping the hard drive while installing Gutsy, and then putting your data back on. 

After that, be careful about what you install and where you install it from. AFAIK, Automatix has made a commitment to making sure their packages won't be a problem anymore, and they apparently have a new team leader. 

The easiest way to reinstall your old programs is to simply go into synaptic or Add/Remove Programs and reinstall them. It's a fairly simple process and the only factor to it is time, depending on how fast or slow your internet connection is.

---

