---
title: "GRUB Menu Trouble"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by puner on 2010-08-08
I need to know if this GRUB menu is supposed to be like this 

[IMG]http://www.imgdash.com/e501.jpg[/IMG]

Thanks

---

### Post by Rubi1200 on 2010-08-08
In a word, yes.

Let me explain:

The first entry represents the latest kernel image

The second entry is for Ubuntu recovery mode (sort of like Safe Mode in Windows as a poor analogy)

The third and fourth entries are the previous kernel versions (before the upgrade/update to the latest version)

The memtest entry is also part of a standard Ubuntu installation.

Windows 7; no explanation needed.

If you would like to know how to edit any of these entries let us know.

Hope this helps.

---

### Post by puner on 2010-08-08
I noticed in Wubi I was given options such as

Ubuntu
Windows

Is it possible to do this with the GRUB menu that I have now? It seems much more simple and clean.

---

### Post by kidpurple on 2010-08-08
I had the same concerns.  I didn't notice the different version numbers until I read this thread.

> **Rubi1200 said:**
> The third and fourth entries are the previous kernel versions (before the upgrade/update to the latest version)

This would make more sense to me if I had been running an older version for a while and been updating all along.  I just happened to download and install 10.04 yesterday, so is that still normal?

---

### Post by Rubi1200 on 2010-08-08
> **puner said:**
> I noticed in Wubi I was given options such as

Ubuntu
Windows

Is it possible to do this with the GRUB menu that I have now? It seems much more simple and clean.
Yes and no; meaning that you could remove older kernel version, the memtest entry and so on. However, actually customizing the menu involves a number of different files across the system as well as creating a custom GRUB menu file. Personally, I don't think the potential mess is worth it. Just my opinion though.

If you are interested, look here:

[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

Pay particular attention to the posts by oldfred and drs305; they know what they are talking about.

---

### Post by Rubi1200 on 2010-08-08
> **kidpurple said:**
> I had the same concerns.  I didn't notice the different version numbers until I read this thread.



This would make more sense to me if I had been running an older version for a while and been updating all along.  I just happened to download and install 10.04 yesterday, so is that still normal?
If there has been an update since then, yes.
Usually, there is an update/upgrade done soon after initial installation. You may not have noticed the update for the newer kernel version, but if when Update Manager finished you were prompted to restart then that was almost certainly the newer kernel version.

I hope this answers your question.

---

### Post by kidpurple on 2010-08-08
That was probably the case - thanks for the info Rubi

---

### Post by ajgreeny on 2010-08-08
Absolutely normal if you installed yesterday, or even today and then updated, as you are prompted to do.  The installation will give you the original kernel shown at the bottom of your list, with the newest at the top.

As you keep updating the system there will probably be several more kernel updates, giving you an even longer menu, because the system never deletes old kernels just because a new one has been installed.

Many people, me included, uninstall the oldest kernels as new ones appear, but always leave two newest versions, just in case something goes wrong with the one you are using.  It has only happened to me once, but I was very glad to have an older version that I knew still worked and could boot to, in order to put the system right.

So, I would advise you to leave well alone at the moment, but when and if you see a new kernel appear on the list, eg 2.6.32-25, uninstall the 2.6.32-21 by searching in synaptic for that number in the search box.  There will probably 3 packages with that number you can remove safely, but as I say, I advise you to keep two known working versions for safety's sake.

---

### Post by Rubi1200 on 2010-08-08
> **ajgreeny said:**
> Absolutely normal if you installed yesterday, or even today and then updated, as you are prompted to do.  The installation will give you the original kernel shown at the bottom of your list, with the newest at the top.

As you keep updating the system there will probably be several more kernel updates, giving you an even longer menu, because the system never deletes old kernels just because a new one has been installed.

Many people, me included, uninstall the oldest kernels as new ones appear, but always leave two newest versions, just in case something goes wrong with the one you are using.  It has only happened to me once, but I was very glad to have an older version that I knew still worked and could boot to, in order to put the system right.

So, I would advise you to leave well alone at the moment, but when and if you see a new kernel appear on the list, eg 2.6.32-25, uninstall the 2.6.32-21 by searching in synaptic for that number in the search box.  There will probably 3 packages with that number you can remove safely, but as I say, I advise you to keep two known working versions for safety's sake.
+1 
Always better to keep at least one "spare" kernel version just in case.

Just to add to what ajgreeny has said; the versions can be found in Synaptic by searching for linux-image and linux-headers (plus the version number) and there will be 3 entries to remove.

---

### Post by shinigami13 on 2010-08-08
Is there a way that after i choose in the windows loader between windows and ubuntu.. it won't go through the grub menu and load the latest kernel instead?

---

### Post by ajgreeny on 2010-08-09
> **shinigami13 said:**
> Is there a way that after i choose in the windows loader between windows and ubuntu.. it won't go through the grub menu and load the latest kernel instead?
Sorry, but you have lost me there.

Are we talking about a wubi install, which then goes to the grub after you choose windows, or have I got you completely wrong?

I can't work out whether you want to avoid grub totally or that you don't see it if you choose windows, or what is meant by your post, I'm afraid.  Give me a full sequence of what happens and what you see now, and also what you would like to see.

---

### Post by bcbc on 2010-08-09
> **shinigami13 said:**
> Is there a way that after i choose in the windows loader between windows and ubuntu.. it won't go through the grub menu and load the latest kernel instead?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

---

### Post by markjreed on 2010-08-25
> **bcbc said:**
> [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

Beware - that trick doesn't seem to work with 10.04+WUBI.  At least, when I tried it, I wound up with an install that just dropped me at the grub shell prompt.

---

### Post by bcbc on 2010-08-25
> **markjreed said:**
> Beware - that trick doesn't seem to work with 10.04+WUBI.  At least, when I tried it, I wound up with an install that just dropped me at the grub shell prompt.

I just tried it - and it worked for me. I did get an exception "unknown command 'keystatus'", but it still booted, with no grub menu prompt.

I think my problem is a mismatch between the wubildr and the version of grub on 10.04.1 (but haven't found a confirmation or fix yet. I could just comment out that part of the code from 30_os-prober I suppose). 

But it didn't drop me at a grub prompt. Perhaps you have some other problem?

---

