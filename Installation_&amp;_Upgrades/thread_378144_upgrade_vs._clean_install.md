---
title: "upgrade vs. clean install"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by azurehi on 2007-03-06
I have a dual boot with windows xp and I would like to replace edgy with feisty final in 4/07.

  I have gotten edgy pretty well configured to my liking and am confused about whether to upgrade to feisty 7.04 from edgy 6.10 (assuming this can be done) or do a clean install from the feisty live cd.  Will upgrading from 6.10 provide the same "package" as the 7.04 live cd?  And allow me to keep my settings?

What is meant by a "clean install"?  To me this means installing from the 7.04 live cd.  Does clean install mean removing edgy by deleting the linux partitions with gparted and using "fixmbr" in the xp recovery console?  Or does "clean install" install over 6.10?

I want to do the most complete install even if I have to reconfigure.

---

### Post by Gerard Barberi on 2007-03-06
Personally I don't see getting anything extra out of clean installing over upgrading.

But, yes, a clean install will wipe everything.  You can avoid some reconfiguring if you mount your /home directory on a separate partition.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Sef on 2007-03-07
>  Personally I don't see getting anything extra out of clean installing over upgrading.

A clean install is recommended because upgrading might cause problems.  Sometimes small, sometimes not.   I never have had a problem with clean installing, but upgrading has caused me minor annoyances.

---

### Post by Kateikyoushi on 2007-03-07
Well you can always try clean install if the upgrade didn't work out, if you make a /home partition clean installs become less painful.

---

### Post by slayerboy on 2007-03-07
I will usually do an upgrade.  If I have problems in a particular program, I usually make a new user to see if I can reproduce these issues.  If I can't, then I know it's a problem with my environment and look for hidden folders in my user folder on /home and delete the folder(s) corresponding to the particular program.

if all else fails, I do a complete clean install but have /home on a separate partition.  it's generally a good idea to keep /home on a separate partition, and I'd like to see this become standard in most distros.  This way I can try out different distros and still keep all my settings and files in the home directory.

---

### Post by zorkerz on 2007-03-07
I have been very luck with upgrading.  I am currently running Edgy having upgraded from breezy to dapper and then from dapper to edgy as each was released.  I experienced no major problems on either upgrade. There were a few minor annoyances at times, non of which I can remember so they could not have been too much trouble.  A successful upgrade is much easier and less time consuming than a fresh install in my opinion.  I am planning on doing a fresh install for feisty.  The major advantage to a fresh install in my mind is knowing that you have an default installation without all the junk build up.  I know that over time i have installed apps i no longer use and forgotten to remove them. All the little tweaks and edited files here and there that might no longer be necessary but i no longer know or remember.  Maybe its more a mental thing for me but I just like the feel of a newly installed os. Like a used to reinstall windows every 6 months to keep it from clogging up.  Though in my opinion XP really does need this where as ubuntu never has for me.
elias

---

### Post by MrEgg on 2007-03-26
Hi, I'm a new comer to Ubuntu (Edgy), and so far I've been more than impressed with what I've seen and with what I've already been able to do. As a new comer, I've done some messing around though, and doing a clean install of Feisty sounds like a better idea for me. That will also allow me to have a better partition strategy, namely by having a separate /home partition. Prior to doing the new install in April, is there a way for me to save my settings so that I don't have to reinstall them all over again in Feisty, like (most important first) : my printers (I have something like 10 of them, over different networks), my display driver (nVidia, over nv), my i8k (I'm on an overheating Dell Inspiron, if that isn't redundant), and my third-party applications like Beryl, Google Earth, etc. ?

Thanks,
Egg

---

### Post by zorkerz on 2007-03-26
you can backup your home partition which has many of the settings for programs you use. To do this i type this command while in my home directory. ```
find . -depth -print0 | sudo cpio --null --sparse -pvd "/backup/dir"
``` simply replace "/backup/dir" with the location you would like to store your backedup home. This by no means fixes all of your problems however. I believe you will still need to install your printers and beryl and nvidia drivers. I may be helpful to save backups of some of your config files if you did any manual editing to them. good luck

hmm i just tried this for myself again and it did not finish copying my whole home over. I is possible i copied the command a little wrong. if trying to do this i would recomend finding one of the much bettter how tos here on the forums.

---

