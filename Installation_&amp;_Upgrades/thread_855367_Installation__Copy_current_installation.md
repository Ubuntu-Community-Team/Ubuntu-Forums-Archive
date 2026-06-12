---
title: "Installation / Copy current installation"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Gallardo Spyder on 2008-07-10
Easy question I hope.

I have a new PC (Dual Core) with Hardy 64 bit all nicely configured with all my apps, files, backup scripts, etc.  Weeks of work to get it just right and how I like it.

I just got another PC to replace another older desktop - The new one is a Quad Core different video card, etc.  

If I want to take my current Dual Core Installation of Hardy and have the same setup, files, etc on my new Quad Core - what is the best way to do it.

I think the answer is making a live CD via this post/tutorial:

[http://ubuntuforums.org/showthread.php?t=688872&highlight=custom+iso](http://ubuntuforums.org/showthread.php?t=688872&highlight=custom+iso)

But what I do not know is - does the live CD (like the installation CD) allow for installation - not just a live CD.  If the live CD will allow me to install...  Will the difference between the two PC's make a difference - or like an installation CD of Ubuntu, does it auto recognize the video, quad core, etc. etc.

I would like to avoid doing a new install and getting everything the way I want it - though I can do it in less time than before, I would still be looking at several days.

I read through creating a live CD and it looks like that is what I am looking for - just don't know if it will install and recognize the differences between the dual and quad core, video, etc...

Thanks for any help or recommendations...

---

### Post by louieb on 2008-07-10
For something fairly quick. I think i'd try a partition image with partimage or clonezilla.

Probably going to have video card problems but every thing else should work. 
to get video fix on the new machine boot to recovery mode and choose the** xfix** option then the **resume normal boot option**.  

once you get a GUI you can run **displayconfig-gtk **to set the max resolution.

Have moved Ubuntu to different PC by swapping hard drives before.  Haven't tried the partition image route.  All in all since the PCs are different it may be the easier path to do fresh install and setup.:guitar: You''ll never know till you try.

---

