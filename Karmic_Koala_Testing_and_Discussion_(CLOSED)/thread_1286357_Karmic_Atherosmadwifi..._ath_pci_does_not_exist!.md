---
title: "Karmic Atheros/madwifi... ath_pci does not exist!"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aldimond on 2009-10-08
Sorry if it's Not Ok to post Karmic questions here, but I can't find info anywhere else I've looked.

Everyone talking about Karmic betas (including Kubuntu, which I'm using) said madwifi worked, completely out-of-the-box, no messing around.  So I dist-upgraded, and now I have nothing.  No ath_pci module, nothing available in the package manager, nothing available in the little "proprietary drivers" app (should that still exist?).

It's not that I can't get on the Internet.  It's worse than that.  I use my computer as a wireless router, so my girlfriend can't get on the Internet.

I could easily compile a madwifi module, but then I'd have to re-do it every time there was a kernel upgrade, I'd always forget, it would be lame, that's why we have distros and package managers in the first place, 'eh?  What's the proper way for me to get a driver up for my Atheros card?

---

### Post by scorp123 on 2009-10-09
> **aldimond said:**
>  So I dist-upgraded, and now I have nothing. And so? What did you expect?? Last time I checked it said everywhere that Karmic is still a **[COLOR="Red"]"Beta" release[/COLOR]**, e.g. [COLOR="Red"]not ready yet for production use[/COLOR]. I personally don't upgrade my Linux until at least 2 months after a release. Why? Because if there were still bugs then they would be hopefully fixed by then. So that Ubuntu 9.10 will soon be out is nice and all that ... but I personally won't be upgrading until December. :)

> **aldimond said:**
>   No ath_pci module  Check what driver packs you have installed. ```
dpkg -l 'linux*' | grep ii
```

If I had to guess I'd say one of the *bla-bla-something-***modules** or *bla-bla-something-***backports** packages is missing. If you still have the previous release there (you said you upgraded so chances are the old packages are still around?) then you can see what the names should be. You should have the same packages for your current kernel as you had for your old kernel.

But again .... this is [COLOR="Red"]**"beta"**[/COLOR] software. If that package doesn't exist yet then you're out of luck.

---

### Post by t0mppa on 2009-10-09
Starting with Jaunty, the default Atheros driver was changed to ath5k instead of madwifi, so that'd explain the lack of ath_pci.

[QUOTE=aldimond]What's the proper way for me to get a driver up for my Atheros card?[/QUOTE]Linux-backports-modules-karmic should provide the latest build of compat-wireless for Ubuntu which features ath5k and ath9k drivers. Then there are the options of building madwifi yourself or using ndiswrapper.

---

### Post by aldimond on 2009-10-09
Thanks, I'd forgotten about ath5k... when I first installed Ubuntu I tried it and it didn't work, but it looks like it's improved a lot over the last year, and it's working fine for me now.

The reason ath5k didn't "just work" is that the ath5k module was blacklisted.  If anyone else has trouble going from madwifi to ath5k/ath9k, you might try grepping through the files in /etc/modprobe.d for a blacklist on those modules.

---

