---
title: "FYI: Conky Packages in Ubuntu 9.10 Karmic Koala"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by londonali1010 on 2009-10-15
Hi all...

If you currently use the Conky package from the Jaunty repos, you'll be on version 1.6.1.  The latest release is now 1.7.2, and is available in the Karmic repos.

However, there are now four versions of Conky in the Karmic repos!  I thought I'd give you a quick guide, so you know which one to use so you get the most out of your favourite desktop monitor :)

The four versions now available are:
[LIST]
[*]conky
[*]conky-all
[*]conky-cli
[*]conky-std
[/LIST]

(First, I should point out that *conky* and *conky-all* are actually the same install...*conky* is in reality just a metapackage that will install the *conky-all* package.  It is there to protect users currently using the repo *conky* package from upgrading and having things break.  The other two packages are options for those who want to have a lighter or minimal Conky install...Further explanation below.)

From the package documentation, here is a brief explanation of the differences between the packages:
> conky-cli is a basic package that can be useful in servers or piped with dzen2.

It includes the following support:

MPD, MOC, math, apcupsd and I/O stats

> conky-std should be a good compromise for most users that do not need special features.

It includes the following support:

X11, XDamage, XDBE, Xft, MPD, MOC, math, hddtemp, portmon, wireless, ALSA mixer, apcupsd, I/O stats and lua

> conky-all includes almost all of the available support:

X11, XDamage, XDBE, Xft, MPD, MOC, math, hddtemp, portmon, RSS, curl, Weather (METAR and XOAP), wireless, IBM, nvidia, eve-online, Imlib2, ALSA mixer, apcupsd, I/O stats, Lua and Lua bindings for the cairo and imlib2 libraries

It is highly advised that you upgrade to one of these packages as soon as you can, as the *conky* metapackage will eventually be removed.

Please feel free to post here if you need any further explanation!

PS. If you need some tips on how to get started with the new features, please have a look on the [Official Conky Blog]("http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started/").

---

### Post by Bruce M. on 2009-10-17
Nice post, great post - very informative - CH! info  :)

Yea, I'm back.

CHIMO!
Bruce

---

### Post by ikt on 2009-10-20
Does anyone have apport waiting to report conky crashing upon login?

From apport.log

```
apport (pid 16376) Tue Oct 20 13:51:35 2009: called for pid 2748, signal 6
apport (pid 16376) Tue Oct 20 13:51:35 2009: executable: /usr/bin/conky (command line "conky -c /home/ikt/Conky/conkymain")
apport (pid 16376) Tue Oct 20 13:51:35 2009: this executable already crashed 2 times, ignoring
apport (pid 18457) Tue Oct 20 16:23:11 2009: called for pid 2582, signal 6
apport (pid 18457) Tue Oct 20 16:23:11 2009: executable: /usr/bin/conky (command line "conky -c /home/ikt/Conky/conkymain")
apport (pid 18457) Tue Oct 20 16:23:13 2009: wrote report /var/crash/_usr_bin_conky.1000.crash
```

---

### Post by TheNessus on 2009-10-20
> **ikt said:**
> Does anyone have apport waiting to report conky crashing upon login?

From apport.log

```
apport (pid 16376) Tue Oct 20 13:51:35 2009: called for pid 2748, signal 6
apport (pid 16376) Tue Oct 20 13:51:35 2009: executable: /usr/bin/conky (command line "conky -c /home/ikt/Conky/conkymain")
apport (pid 16376) Tue Oct 20 13:51:35 2009: this executable already crashed 2 times, ignoring
apport (pid 18457) Tue Oct 20 16:23:11 2009: called for pid 2582, signal 6
apport (pid 18457) Tue Oct 20 16:23:11 2009: executable: /usr/bin/conky (command line "conky -c /home/ikt/Conky/conkymain")
apport (pid 18457) Tue Oct 20 16:23:13 2009: wrote report /var/crash/_usr_bin_conky.1000.crash
```
it happens to me too, and randomly too in regular use. I just notice it's not on and start it again...

---

