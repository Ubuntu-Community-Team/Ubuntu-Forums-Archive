---
title: "anyone using the new AWN in Lucid?"
date: 2009-12-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by AndyP79 on 2009-12-30
Hi All,
 I am testing Lucid. Is anyone else who is testing Lucid using the new AWN? I have it running fine in Karmic and in Helena, but after adding the PPA, I still don't have it in Synap. Does anyone know how to install it all and have it run through the Terminal?
Thanks

---

### Post by Paqman on 2009-12-30
Lucid is still very early in it's release cycle. Getting involved in testing is a good thing to do, but if you aren't that familiar with Ubuntu i'd suggest holding off, or limiting your testing to a sandboxed environment (eg: virtual machine, spare computer, etc)

Having said that, which PPA for AWN are you using? If it's [this one]("https://launchpad.net/~awn-testing/+archive/ppa") then they haven't really built the packages for Lucid yet. Like I said, it's *very* early in Lucid's cycle. It's definitely not ready for widespread use yet.

---

### Post by AndyP79 on 2009-12-30
I have been destroying my computers for a couple of years now. I am venturing out by trying Lucid. I have a stable box for my regular stuff, and now use my old computer for mucking with. I find this is much more condusive to me actually using my computers to do stuff. 

So far on Lucid I have got GlobalMenu and Gnome menu, Docky, some really nice icons, a customized theme, screenlets(not happy with yet), window controls in the panel. This is only my second load of Lucid in about 2 weeks. I blew up the first one trying to get RGBA to work, then came across some stuff that made it seem like what I had happen was normal. I actually have been enjoying my Lucid load better then Karmic so far, even in it's Alpha, it feels more stable. I am really wanting the get the AWN running in it, and looking forward to the RGBA that sounds like it will end up coming in an update at some point.  
Anyway...

So i have tried using both the Karmic and Lucid PPA. With the Karmic on Karmic, it automaticlly just put the trunk in Synap, but not with Lucid. I am guessing maybe if I just leave the PPA in my Sources, once it is devoloped, it will just show up, and I will see it being updated?

---

### Post by Paqman on 2009-12-30
> **AndyP79 said:**
> I have been destroying my computers for a couple of years now. I am venturing out by trying Lucid. I have a stable box for my regular stuff, and now use my old computer for mucking with. I find this is much more condusive to me actually using my computers to do stuff. 


Fair enough. If you haven't already you should create a Launchpad account so that you can report bugs. We've got an automated bug reporting tool called apport that can automatically report any crashes and attach useful diagnostic output to the bug report.

You might also like to look into the [Testing Team]("https://wiki.ubuntu.com/Testing") and how you can help.


> I am guessing maybe if I just leave the PPA in my Sources, once it is devoloped, it will just show up, and I will see it being updated?

Absolutely. In the meantime the regular AWN can be got from the Universe repo. Make sure you've got Universe enabled in Lucid and you'll get version 0.3.2.1-4ubuntu2 of AWN through Synaptic. You might find that any version that comes through the PPA will conflict with the stable version you get from Universe, in which case Synaptic will handle uninstalling one and installing the other automatically. Update Manager might get a bit confused by this and offer a "partial upgrade". If so then use Synaptic to do the upgrade, it'll tell you exactly what it will do so you can check before committing to the update.

---

### Post by AndyP79 on 2009-12-30
Cool, I am going to check ou tthe Launchpad thing for testing. i have an account, but it was for the UbuntuOne, but I never used it. 
It is super late here, so I am going to work on this in the morning. Thanks for the cool tips. 
Happy New Years

---

### Post by louieb on 2009-12-30
> **AndyP79 said:**
> I have been destroying my computers for a couple of years now. I am venturing out by trying Lucid. I have a stable box for my regular stuff, and now use my old computer for mucking with.

Those of us nutty enough to install the alpha stage of a release usually post in  [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310"). You will find a sub forum for Lucid.   

lol - never mind - see you have already been posting there. :P
Good Luck with awn.

---

### Post by Joeb454 on 2009-12-30
Moved to Lucid Testing :)

---

