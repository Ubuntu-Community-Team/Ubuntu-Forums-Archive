---
title: "Console font"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by SlayerMan on 2007-04-24
Hi all,

I just checked out the new Feisty on my laptop. There's one strange thing though:

The console fonts are all messed up. This leads to a crippled screen when running dpkg-reconfigure or other slang/curses based apps.

btw: Since being from Germany I chose "German" at the boot prompt.

Is anybody else experiencing this problem? Should I file a bug to Launchpad? If yes: which package should I associate the bug with?

Kind Regards
SlayerMan

---

### Post by fakie_flip on 2007-06-22
Yes, you should file a bug on Launchpad. I am using US English layout, not German, and my console fonts are messed up too. "sudo /etc/init.d/console-setup reload" only fixes the problem temporarily. You could associate the bug with the package console-setup.

---

