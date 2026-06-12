---
title: "The Incredible Growing Ubuntu-docs Package"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by talkingwires on 2009-10-15
I started the daily dist-upgrade, and noticed that the upgradeable packages would need an additional 64Mb of space. A quick investigation revealed that it was the ubuntu-docs package that wanted all the extra space. A look at it in Synaptic (see screenshot) revealed a horrible truth: 237Mb of disk space used for help files.

Isn't one of the big points of internationalization that we can split packages like this up so our disks aren't filled with stuff we can't even read? And if text-based files really explode to sizes like when they're not compressed, couldn't we store the files as gzip's on disk? I mean, gzip is pretty fast, and it's not like a second or two more to load a help file would hurt anything.

---

### Post by emarkay on 2009-10-15
Interesting - I guess sometimes the developers forget that some of use still have 50Gig or less hard drives!

Comments welcome.

---

### Post by ohzopants on 2009-10-15
Damn! That is HUGE!

Did you happen to check what depends on it?  I'm not on my ubuntu pc right now so I can't check myself; I just hope not everything that has a man page requires it.

---

### Post by mc4man on 2009-10-15
> what depends on it?

basically nothing (the ubuntu help center uses the doc's

If you're never going to reference it then your free to remove. if you think maybe there might be something useful it's also available online after the release

[https://help.ubuntu.com/](https://help.ubuntu.com/)

( I guess there could be an 'online' option for the help center for use in the absence of the local doc's, though there is in a round about way - 'free support' -> ' documentation'

---

### Post by joey-elijah on 2009-10-15
I wonder if this is included in the netbook remix too? Because when space is at a premium and the device is design as a mobile internet device - is there any need for local copies?

---

### Post by 23meg on 2009-10-15
[Bug #451764]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/451764") welcomes you.

If you actually go and check the installed file sizes, you'll see that's definitely not the actual size of the package. It's 19MB.

---

### Post by talkingwires on 2009-10-15
> **23meg said:**
> [Bug #451764]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/451764") welcomes you.

If you actually go and check the installed file sizes, you'll see that's definitely not the actual size of the package. It's 19MB.

Ah, good eye. Nice to see that somebody else raised their eyebrows when they saw the reported size of the update.

---

### Post by 23meg on 2009-10-15
> **talkingwires said:**
> Ah, good eye. Nice to see that somebody else raised their eyebrows when they saw the reported size of the update.

Being the release manager must have helped...

---

