---
title: "Prompted to uninstall ubuntu-desktop (???)"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Chriswaterguy on 2007-11-16
I've finished playing with eog and evince, and didn't want to be continually prompted for updates (large files, slow connection) so I decided to uninstall them. 

Whichever one I try to uninstall, Synaptic tells me it's also going to remove ubuntu-desktop. And from a quick search, I don't think that's something I should be uninstalling, is it? Is this a bug? How can I safely removed them? Thanks.

---

### Post by erfahren on 2007-11-16
that's not a bug. it's a metapackage, see: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)
you can let ubuntu-desktop be removed, if you want just reinstall it afterwards

---

### Post by Chriswaterguy on 2007-11-18
Thanks - now I understand what a meta-package is. 

This is strange behavior though (prompting to uninstall), and it's not documented. That page doesn't explain why it happens, and it doesn't make it clear whether uninstalling is safe. I'll just have to take your word for it. Another way in which Linux is completely confusing for a newbie.

---

### Post by erfahren on 2007-11-18
confused me too at first.The way I understand it is that it's sort of like a list of packages. When one of the packages on the "list" is removed the list is removed as well.

I agree that there's not much documention about it. It's description just says:
> 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

I've seen it mentioned by many others more knowledgable than I that it's safe to remove. I always uninstall evolution and it gets removed as well. I just go back and reinstall it afterwards.

---

### Post by Chriswaterguy on 2007-11-20
> **erfahren said:**
> I always uninstall evolution and it gets removed as well. I just go back and reinstall it afterwards.

I've just tried this, and when I try to reinstall ubuntu-desktop, it says **...the following changes are required... To be installed: eog, evince**. I.e. the very programs I deliberately uninstalled.  :confused:

---

### Post by erfahren on 2007-11-21
that's odd, I tried uninstalling eog and evince and it happened to me as well. It also wanted to reinstall all the evolution stuff and a couple of other things I had removed as well (totem-mozilla for one).

I went ahead and reinstalled everything and then removed all the evolution (and other stuff) again and It didn't prompt to remove ubuntu-desktop. I'm confused now since I'm certain it did the first time and I was able to reinstall ubuntu-desktop without everything else. Maybe not.

I think I figured it out after some experimenting. When I removed evolution using Synaptic there was a remnant of the complete package that I overlooked and didn't remove. When I went to remove it I was then prompted to remove ubuntu-desktop. So it appears that as long as everything associated with the complete package isn't removed then ubuntu-desktop isn't removed as well.

Likewise for my totem-mozilla. It's part of the metapackage, but it was just a plugin for totem and the complete package wasn't removed. (I use VLC by the way, seem to have better luck with it.)

but eog and evince are complete packages by themselves.

Anyway, there are a couple things you can do:
eog and evince aren't big programs. Looking at the packages on [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/) - they are only about 1meg each. 
(you can search for that with Google doing like "evince site:packages.ubuntu.com/gutsy/") 
-- so if your mainly concerned with getting less updates you could lock the versions in Synaptic (highlight the package and in Synaptic's menubar go to Package > Lock Version)

After reading a couple other old threads (links below) it seems that the only real problem with removing ubuntu-desktop is that it really needs to be present during distrubition upgrades. So you could remove it until you go to do a dist upgrade (from Gutsy to Hoary) and just reinstall it for that purpose.

[http://ubuntuforums.org/archive/index.php/t-10704.html](http://ubuntuforums.org/archive/index.php/t-10704.html)
[http://ubuntuforums.org/archive/index.php/t-136047.html](http://ubuntuforums.org/archive/index.php/t-136047.html)

---

