---
title: "Feisty GUI breaking install"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by macogw on 2007-05-25
This is the WEIRDEST thing ever.  I can't install Feisty on a computer that is currently running it!  I had Feisty on it starting at herd 2 and have been having a lot of problems (for instance, I can't burn cds, sometimes adding applets to my gnome panel gives gconf errors, and compiz lacks window borders).  I thought it was unstable's fault, so I'd do a fresh install on my external hard drive, see if my cd burner works with a fresh Feisty (to prove that I have a dirty install), and if it worked, I'd install it on the internal hard drive, otherwise go back to Edgy.  However, I can't get Feisty installed!  

My optical and external drives are both perfectly fine.  I was able to install Dapper on the external drive and burn cds using that.  It can't be a hardware thing.

I've tried 3 different Feisty live cds (all came out fine when I did "check this disk for erros" and md5sum'd the isos and md5sum'd the burned disks).  Ubiquity ALWAYS segfaults halfway through.  One time I tried adding something to the panel after Ubiquity quit and I got the same gconf errors I get with the currently-installed Feisty. 

I tried the alternate cd (also a good burn, I've installed on 2 other laptops from it).  It got through 6% of "installing software" (after the base system is installed), and then it failed.  I kept trying to restart that part and it wouldn't budge.  

Finally, I told the alternate cd to install a text-only system.  That was able to complete and works fine, from what I can tell.  Somehow, having it install a GUI breaks the installer.

I don't know what to do.  I tried apt-get'ing ubuntu-desktop from the cd (no internet connection from this command line mode), but it failed.

EDIT: Before anyone asks, Intel 950.  The live cd failure wouldn't surprise me if it was anything else (*cough*ati*cough*), though the alternate cd still would.

---

