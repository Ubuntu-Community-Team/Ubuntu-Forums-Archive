---
title: "[help]How to install Ubuntu automatically?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by anriqing on 2008-11-01
Hi&#65281;
I am learning Ubuntu Document "Automating the installation using preseeding" It's link is:[https://help.ubuntu.com/7.10/installation-guide/ia64/appendix-preseed.html ]("https://help.ubuntu.com/7.10/installation-guide/ia64/appendix-preseed.html")
I'd like to burn a customized CD which I can use to install Ubuntu automatically.

It is  said &#65306;
> 
If you are using initrd preseeding, you only have to make sure a file named preseed.cfg is included in the root directory of the initrd. The installer will automatically check if this file is present and load it. 

but I have a doubt about it: I Put my customized preseed.cfg to the directory of casper where initrd.gz is located, then remastered my ISO image. It's bootable, but it still stops at the "Language Select" Screen and waits for manual select. Why? Am I wrong? What do I need to do to fix that problem? 

I'm hoping for someone to give me an advise.:mad::mad::mad:

---

### Post by grangey on 2010-03-25
[COLOR=black][FONT=Verdana]I am struggling to in this area, but I can offer this,  I think initrd.gz is a compressed file that you can open and you need to put the preseed.cfg file within the root directory of it.  So you need to uncompress it add the file re-compress is and then rebuild your iso image.  checkout [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd) and [https://help.ubuntu.com/7.04/installation-guide/powerpc/preseed-using.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/preseed-using.html).  From there I'm stuck also as it still doesn’t work for me.[/FONT][/COLOR]

---

