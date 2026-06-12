---
title: "Remove Intel Linux Graphics"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by ukbeast on 2013-08-20
Hello, I have Ubuntu 13.04 installed. is it possible to remove it and revert back to default Ubuntu drivers?

---

### Post by SweetAurora on 2013-08-20
What card are you using? Is it an Intel like the title says? If so, there is nothing to remove because the only Intel drivers availible are already the default. If you have one of those funny hybrid systems, that is a different story.
Post the output of 
```
lspci | grep VGA
```
to see exactly what we are dealing with.

Anyways, what exactly is the problem you having with the grahics right now?

---

### Post by ukbeast on 2013-08-20
> **SweetAurora said:**
> What card are you using? Is it an Intel like the title says? If so, there is nothing to remove because the only Intel drivers availible are already the default. If you have one of those funny hybrid systems, that is a different story.
Post the output of 
```
lspci | grep VGA
```
to see exactly what we are dealing with.

Anyways, what exactly is the problem you having with the grahics right now?

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

I am not able to get Mplayer to use vaapi for x264 videos and my GPU is Intel Sandy Bridge.

[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/) is my current drivers. 

Thank you

---

### Post by ukbeast on 2013-08-21
bump

---

### Post by grahammechanical on 2013-08-21
Have you tried going to System Settings>Software and Updates>Additional Drivers tab and selecting the Nouveau driver. I do not have Intel graphics so I have no idea what you will see in the Additional Drivers tab but I know that when we install Ubuntu and tick to install Third Party Software we also get the latest proprietary video driver installed. The way to revert to open source drivers is through Additional Drivers. Or shall I say that is the easy way.

Regards.

---

### Post by SeijiSensei on 2013-08-21
This is a problem with the version of mplayer that Ubuntu distributes, which does not include the Intel vaapi driver.  You can test this by running the command  "mplayer -vo help" at the command prompt to see the list of supported output drivers.  On my 13.04 machine, vaapi is not among them.  

However all is not lost.  See if the instructions on [this page](http://www.webupd8.org/2012/11/install-mplayer-with-va-api-hardware.html) fix the problem for you.  Otherwise you could [compile]("http://ubuntuforums.org/showthread.php?t=2149564") your own copy of mplayer with the Intel vaapi driver included.

Ubuntu now ships with **mplayer2** as the default mplayer binary.  It once had better support for A** subtitles and Matroska ordered chapters than the original mplayer, but I haven't done a comparison of the two versions in a while now.  I don't know which version of mplayer is included in the PPA that article uses.  If you need or prefer mplayer2, but the PPA offers mplayer, you'll be back to compiling your own version from [source](http://www.mplayer2.org/downloads/).

Like the author of that how-to, I use [SMPlayer]("http://smplayer.sourceforge.net/") as a graphical front-end for mplayer and mplayer2.  It has many convenient features and is well-maintained.

---

### Post by MrSteve on 2013-08-21
open the Ubuntu software centre and then put in the search bar 
intel gma

it will bring up a list of intel drivers with vaapi support
the last and latest driver i believe is intel gma3600 ...

---

### Post by SeijiSensei on 2013-08-22
Again, the problem does not lie in the graphics drivers, but in the version of mplayer the OP is using.

---

