---
title: "Monitor doesn't work after upgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by someitalian123 on 2011-04-29
Before ubuntu can even boot I get this on my monitor

Out of range Please set to 1280x1080 @ 60Hz

I get that a grub. I'm not even sure if ubuntu can even boot because my  monitor won't let me see anything. I'm using the driver off the nvidia  website, not the stock one that came with ubuntu.

---

### Post by Hedgehog1 on 2011-04-30
> **someitalian123 said:**
> Before ubuntu can even boot I get this on my monitor

Out of range Please set to 1280x1080 @ 60Hz

I get that a grub. I'm not even sure if ubuntu can even boot because my  monitor won't let me see anything. I'm using the driver off the nvidia  website, not the stock one that came with ubuntu.

Grub is working, just hosing the display with a frequency your monitor doesnt like.

You can arrow up/down and press enter to get into Ubuntu. It may take a few tries to find it.

Once you get into Ubuntu, do this:


```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by someitalian123 on 2011-04-30
I still wasn't able to boot, so I had to reinstall ubuntu, and I still had the problem with grub but at least I was able to get into gnome. I tried what you said and it worked. Thank you, you've been very helpful.

---

