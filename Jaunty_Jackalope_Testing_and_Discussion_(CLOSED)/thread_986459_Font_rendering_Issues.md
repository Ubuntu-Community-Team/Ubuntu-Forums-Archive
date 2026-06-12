---
title: "Font rendering Issues"
date: 2008-11-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by softtower on 2008-11-18
First, let me say that I loved how Ubuntu renders fonts (in versions 7.10 and 8.04) when they have BCI turned on by default in FreeType.

But Intrepid (8.10) is a big step backward in terms of font rendering: BCI is obviously not working, as you can tell because without sub-pixel smoothing fonts *always* look jagged, regardless of the level of hinting. And Kubuntu is even worse that that: hinting levels don't do anything there.

Instead of complaining and waiting for external help, I decided to do something about it: get the source for FreeType, study the building instructions and configuration, perhaps package my own deb files for each Ubuntu release or (even better!) collaborate with Ubuntu FreeType maintainers.

I went to ubuntu's site and tried to follow instructions/information for developers who want to join. But the amount of pages/sub-sites is astounding, so frankly I am lost: where do I begin to do what I want to do?

Basically I'm asking for an advice for 2 issues:
- FreeType on 8.10: what happened?
- Starting to contribute to packaging/compilation (and possibly development) process: I want to be in control of my fonts. I am using OSX now and it's dumbed-down approach hurts, but my eyes hurt on Ubuntu hurt even more.

---

### Post by calc on 2008-11-19
> **softtower said:**
> Basically I'm asking for an advice for 2 issues:
- FreeType on 8.10: what happened?


I'm not certain what all changed but as I understand it at least the way sub-pixel hinting is done changed in libcairo, which caused problems with OpenOffice.org.

There is some information in /usr/share/doc/libcairo2/changelog.gz

---

### Post by mdurham on 2008-11-19
softtower, how about a screen shot of what you are talking about. My fonts seem ok to me.
Cheers, Mike

---

