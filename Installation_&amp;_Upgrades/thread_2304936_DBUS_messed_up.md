---
title: "DBUS messed up"
date: 2015-12-01
forum: Installation &amp; Upgrades
---

### Post by alex367 on 2015-12-01
Hi,

I was installing the RPM package and in the middle of the installation my network connection disconected.
I restarted and... no X, i did a start x and no success. It looks like a problem with the dbus.

So, lets try to sudo apt-get install dbus --reinstall..... ERROR (Dependencies problem.. run sudo apt-get -f install).

Nice, lets do that.... Error trying to configure fontconfig.

I cannot reinstall the fontconfig or do nothing because the apt-get WANTS me to do an apt-get -f install and it fails (of course).

So, lets take a look in the fontconfig logs... there is a symbol problem, probably some library, but i cannot do a single thing, i tried to find the font cache folder, no luck, i looked if there was a newer version of the library on my system... that is so frustrating.

I tried to do an apt-get clean apt-get autoremove (asked for apt-get -f install).

Is there a way to fix that?

---

### Post by ian-weisser on 2015-12-01
We need to see each of those complete error messages, in context. Preferably in order.
The error messages contain valuable information to help diagnose the problem.
Please use [code] tags to contain the output.

---

### Post by alex367 on 2015-12-01
Humm, actually that will be hard, I am on the same machine that is messed, I cannot copy and paste or boot from another machine. BuI i agree with you. Actually the problem now is that I cannot do an apt-get update, because it fails on the configuration step (because it cannot find some symbols when it tries to regenerate the font cache). so i cannot do an apt-get -f install because it will try to configure the fontconfig.. again.

---

### Post by alex367 on 2015-12-01
The error

```

/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/.local/share/fonts: skipping, no such directory
Re-scanning /usr/share/fonts: fc-cache: symbol lookup error: fc-cache: undefined symbol: FcDirCacheRescan

```

---

### Post by ian-weisser on 2015-12-01
> **alex367 said:**
> Re-scanning /usr/share/fonts: fc-cache: symbol lookup error: fc-cache: undefined symbol: FcDirCacheRescan

Try reinstalling (or upgrading) libfontconfig1

The middle of an upgrade is lousy time for the package manager to abort.
Could be all kinds of problems caused by that...or none.

---

### Post by alex367 on 2015-12-01
That is the problem, the apt-get does not allow me to install a single package, it tells me to finish the pending instalations with apt-get -f install, so i cannot install the library :(

---

### Post by ian-weisser on 2015-12-01
Please show us the actual error message.
There is often a workaround.

For example, you can manually delete the version(s) of libfontconfig1 in /var/cache/apt/archives, then download a fresh one from [http://packages.ubuntu.com](http://packages.ubuntu.com), and do the reinstall with dpkg instead of apt.

---

