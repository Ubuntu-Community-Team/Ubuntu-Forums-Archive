---
title: "Still struggling with HD space for Feisty upgrade"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Edward The Bonobo on 2007-05-23
I reported here: [http://ubuntuforums.org/showthread.php?t=451330&page=2](http://ubuntuforums.org/showthread.php?t=451330&page=2) that I'm having difficulty freeing up disk space to allow me to upgrade to Feisty.

I've cleared out as much as I could find, including various scraps from my Home folder's hidden files.  I got it down to about 1.6GB.

I ran Upgrade Manager, and it told me I needed another 1000KB or so.

I got rid of about 6MB more and ran Upgrade Manager again.

Now it wants another 20+MB

WTF?

Any ideas?  Any speedy ways of cleaning up all the various scraps in different places? It's taking me hours to search, delete, autoclean, sweep up orphans, etc. etc.

---

### Post by bernied on 2007-05-23
I suppose a new hard drive is out of the question?
Looks like you're pushing windows to the limit as well.

---

### Post by Edward The Bonobo on 2007-05-23
Eek!  That would be an admission of defeat!  Sure, I've got a 3rd-World spec machine, but why shouldn't Ubuntu cope with that?  Appropriate technology.  Reduce, Re-use Recycle!

I'm especially troubled, though, because I easily meet the minimum spec for Ubuntu (2GB) - plus - hey! - I already have Ubuntu (Edgy) up and running.  It's just that I can't upgrade.

Here's an idea:  I *do* have another HD, which is a windows boot and storage.  Is it possible to get the Upgrade Manager to download the update files onto this, but install on my Ubuntu boot?  

Or maybe I can upgrade from a Feisty CD?

---

### Post by phidia on 2007-05-23
> **Edward The Bonobo said:**
> Eek!  That would be an admission of defeat!  Sure, I've got a 3rd-World spec machine, but why shouldn't Ubuntu cope with that?  Appropriate technology.  Reduce, Re-use Recycle!

I'm especially troubled, though, because I easily meet the minimum spec for Ubuntu (2GB) - plus - hey! - I already have Ubuntu (Edgy) up and running.  It's just that I can't upgrade.

Here's an idea:  I *do* have another HD, which is a windows boot and storage.  Is it possible to get the Upgrade Manager to download the update files onto this, but install on my Ubuntu boot?  

Or maybe I can upgrade from a Feisty CD?

Yes you can use the feisty alternate cd to upgrade with. If you use synaptic in synaptic chose the Edit menu item> Add CD-ROM and from there you should be able to upgrade. Check the community docs for more info.

---

### Post by Edward The Bonobo on 2007-05-24
> **phidia said:**
> Yes you can use the feisty alternate cd to upgrade with. If you use synaptic in synaptic chose the Edit menu item> Add CD-ROM and from there you should be able to upgrade. Check the community docs for more info.

Just to check, before I go to the minor bother of downloading the CD...I'm assuming that this method will mean that upgrade files don't have to be copied to my HD before installing over the existing Edgy.  Correct?

---

### Post by bernied on 2007-05-24
> **Edward The Bonobo said:**
> Just to check, before I go to the minor bother of downloading the CD...I'm assuming that this method will mean that upgrade files don't have to be copied to my HD before installing over the existing Edgy.  Correct?
I would guess that this is not correct - the cd will be treated just like any other repository.

Maybe you should think about reducing the size of your system, you are probably carrying a lot of applications that you don't use. They will be part of the ubuntu-desktop meta package. You can remove this and install just the software that you want. But I'm not going to tell you what software that you want. There is probably a way of doing this without uninstalling then reinstalling.

An easier way might be to uninstall gnome and use a lightweight desktop instead.
```
aptitude remove ubuntu-desktop && aptitude install xubuntu-desktop
```
But this might not be what you want. (And I'm not sure that the aptitude remove would get rid of everything anyway.)

That Windows partition seems to be taking up a lot of space...

---

### Post by Edward The Bonobo on 2007-05-24
Oof!  

So...having worked successfully with a nice Gnome desktop with Breezy, then Dapper, then Edgy, I may now have to drop down to Xubuntu?  Nah - I can't believe that!

Yes, my Windows partition is big.  But it *is* on a physically separate device, so I can't do much to repartition it.

Am I correct in assuming that the extra (approx) 1.8GB that's needed for the install is only needed temporarily?  ie files will be dropped there, then removed after the install?  If that's true, I guess I can live with stripping out a few of the packages temporarily.

Not very elegant, though.  Should life be this difficult, **even on a machine which meets the documented Ubuntu system requirements spec?!!!**

---

