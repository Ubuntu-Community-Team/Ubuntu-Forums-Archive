---
title: "Flash and libswfdec"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forrestcupp on 2009-04-14
When I was in 8.10, I had absolutely no problems with Flash videos.  As soon as I upgraded to 9.04, Flash became unusable.  I could hear the audio, but the video took forever to show, and even then it only showed like one frame every few seconds.

My solution was to remove everything that had to do with libswfdec.  After I removed those packages, Flash videos became smooth again with the flashplugin-nonfree package.

The problem is that removing libswfdec also removed the gnome and gnome-desktop-environment packages.  I know that removing those packages doesn't actually remove the Gnome DE, but there is a purpose for those packages.  It would be nice if they didn't depend on something that makes YouTube unusable.

---

### Post by QwUo173Hy on 2009-04-15
I had no working flash at all so I don't have your exact problem. In case it helps though, here's what I did.

I removed the package flashplugin-nonfree, enabled the 3rd Party Parter Source (In Software Sources) and installed adobe-flashplugin.

[edit] I mis-read your post, apologies! [/edit]

---

### Post by forrestcupp on 2009-04-17
> **jarlath said:**
> 
I removed the package flashplugin-nonfree, enabled the 3rd Party Parter Source (In Software Sources) and installed adobe-flashplugin.

[edit] I mis-read your post, apologies! [/edit]

yeah, I tried adobe-flashplugin, too.  It didn't work.  Nothing did until I removed libswfdec and everything with it.  But it did work just fine after that, so at least it was possible.

Maybe it was just the computer I was running it on.  It was my dad's old laptop.

---

