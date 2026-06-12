---
title: "GDM error on boot"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by MockY on 2007-03-12
While doing some php scripting this afternoon, I started noticing that everything I saved from a browser got saved in the root directory and not on my desktop. Then after that, every software displayed sqares instead of letters. I thought this was very odd and restarted the computer.

It now refuses to boot into the GUI and instead I get a blue screen of death (thought they were windows native) that says this:

> Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exit. please correct gdm configuration and restart gdm

So I wnt in and followed these steps:

```

ls -las /var/lib

```

The directory was there

```

chown -R gdm:gdm /var/lib/gdm

chmod 750 /var/lib/gdm

telinit q

```


I rebooted the computer and I still have the same issue.
Could someone please tell me what to do? Thanks.

---

### Post by MockY on 2007-03-12
I can boot by typing startx, but I get various error messages and everything is in squares. I can surf and everything is displayed just fine in the browser, but everything in the OS is displayed with squares.  I have tried to reinstall gdm but it does not fix the problem.

Anyone?

EDIT

I solved it by running
```

sudo chmod 4755 /var

```

---

