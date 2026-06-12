---
title: "Live CD Out of Memory error"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by GoldenKevin on 2010-11-13
Hey guys, I hope this is the right forum.

Today, I burned a copy of Lubuntu 10.10 Maverick Meerkat and tried installing it on my old 2.4Ghz Celeron 192MB RAM (actually 256MB with 64MB dedicated by the BIOS for the internal video card) laptop, which installed Lubuntu 10.04 Lucid Lynx with absolutely no problems. However, when I tried inserting the disk for Maverick this time around, the live CD boot always hangs during Plymouth, and pressing Esc shows:

```
Generating locales...
  en_US.UTF-8...
```

I modified the boot options and removed splash and quiet, and I got a whole lot of messages that seemed like errors, but I think the root of the problem was this:
```
Out of memory: kill process 620 (localedef) source 929 or a child
Killed process 620 (localedef) VS2: 59500kB, anon-rss: 57596kB, file-rss: 820kB
```

After that, it got a few messages about localedef timing out for 120 seconds or something.

Now I'm no idiot, I'm well aware that my laptop is cutting it very close to the minimum RAM requirements of the live CD, but it's just the live CD that stops me from running Lubuntu, because once it's installed, I have no problems. I ran Lubuntu 10.04's Live CD with no problems and the installed LXDE system ran amazingly fast. I'm sure if I could just install Lubuntu 10.10, it would run at the same speed. The problem is that the [Lubuntu wiki]("https://wiki.ubuntu.com/Lubuntu") still writes the minimum system requirements of:
> A Pentium II or Celeron system with 128 MiB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use. If you have less than 160 MiB of RAM, you will need to use the Minimal installation instructions.
This should be updated for the requirements of the new live CD introduced in 10.10.

And I'm a bit worried how the new live CD uses much more RAM than the previous one. I was able to run it on my 256MB laptop with no problems though.

So now I'm on my way getting the minimum installation. Does anybody know how I use the alternate cd to install everything Ubiquity installs? I do have access to ethernet, but I'd prefer if I can do it without a network install because it is rather inconvenient for me. I probably rambled on about a lot of stuff, but what I really want to ask is whether the alternate CD installs the system exactly like the GUI installer does, and if somebody could update the Lubuntu wiki page so that it shows the updated RAM requirements.

---

### Post by GoldenKevin on 2010-11-13
Actually, I just tried the alternate CD now and it wouldn't even get past the ISOLinux menu. Either it froze or my keyboard stopped working - I couldn't even select a language.

I run on a Compaq Presario 2190US, and it appears as though I have the same problem as this guy running a Presario 2170US: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/662286](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/662286)

---

### Post by searchfgold6789 on 2010-11-13
I would install 10.04 and then upgrade from the Update Manager.

---

