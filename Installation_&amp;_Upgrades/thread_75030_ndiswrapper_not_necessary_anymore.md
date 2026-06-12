---
title: "ndiswrapper not necessary anymore?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by epohs on 2005-10-13
I've been running Breezy for several weeks now with very little problems.  However, when I first installed, my wireless card (DLink DWL-520G) wasn't recognized so I had installed ndiswrapper and gotten it up that way.

Now that Breezy is official, I'm wondering if I can uninstall ndiswrapper?  If I do so should the card be recognized automatically or will I need to do some configuration?

---

### Post by adwait on 2005-10-13
If you have been updating Breezy regularly, and you required the ndiswrapper, the final release of Breezy is not about to change much. Basically,  if your card vendor has released on a Windows driver, there's really not much Ubuntu can do to support it, except maybe use ndiswrapper to use the windows driver itself.

---

### Post by epohs on 2005-10-13
Well, I fresh installed a breezy preview a month or so ago, and the card wasn't recognized then so I went the ndiswrapper route.  Since then I haven't tried removing ndiswrapper, so I'm not sure if the card is recognized natively or not.

Is there any way to check without uninstalling ndiswrapper?

---

### Post by mariner09 on 2005-10-13
Maybe someone can post a list of which wireless chipsets are known to be supported by Ubuntu's restricted-modules package.

You can try opening Synaptic and looking at the details of the restricted-modules package and see if there's a list there.

My drive died, so I can't look, but if nobody can tell you before I get my replacement drive set up, I will look.

I know my atheros chipset is supported in that package.

---

### Post by Psquared on 2005-10-13
[QUOTE=mariner09]Maybe someone can post a list of which wireless chipsets are known to be supported by Ubuntu's restricted-modules package.

You can try opening Synaptic and looking at the details of the restricted-modules package and see if there's a list there.

My drive died, so I can't look, but if nobody can tell you before I get my replacement drive set up, I will look.

I know my atheros chipset is supported in that package.[/QUOTE]


check here:

[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless)

---

