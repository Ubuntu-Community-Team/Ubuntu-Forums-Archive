---
title: "Wubi install of Xubuntu fails"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by TFD on 2011-06-23
I have tried twice to use Wubi to install Xubuntu on a Windows XP machine. Each time the results were the same:

1) Downloads the required stuff.
2) Does some post-download stuff.
3) Says it needs to reboot to finish the installation.
-------------- here is where it goes bad -------------
4) Reboots back into Windows. There is nothing set to choose Xubuntu (no error messages displayed in prior steps). 

Has anyone else encountered this bug?

---

### Post by bcbc on 2011-06-23
1 of 2 things. Either, the Boot manager timeout is set to 0 so it just boots the default (Windows), or there is no entry for Xubuntu.

Right click on My Computer, Properties, Advanced tab, Startup & recovery settings. Check the timeout - set it to 30 or 15. Check the drop down box for the default OS - make sure Xubuntu is listed there.

If Xubuntu is not listed, report back.

Warning - never set the timeout less than 15 and the default as Ubuntu.

---

### Post by TFD on 2011-06-23
> **bcbc said:**
> 1 of 2 things. Either, the Boot manager timeout is set to 0 so it just boots the default (Windows)

Yep, that was it. Thanks!

> 
Warning - never set the timeout less than 15 and the default as Ubuntu.

What is wrong with a default of Ubuntu?

---

### Post by bcbc on 2011-06-23
> **TFD said:**
> What is wrong with a default of Ubuntu?

Nothing. It's the combination of the timeout and the default that can be a problem. Setting it to zero prevents windows booting - and I've heard anecdotally that setting it to 1 does the same. I just say anything less than 15 is a bad idea to keep it simple.

It's not too hard to fix on XP but Windows 7/vista requires a windows rescue prompt and bcdedit or rebuilding the bcd.

And if you find you're booting Xubuntu more than Windows you might want to consider a direct install (rather than Wubi) which is more stable for long term use.

---

