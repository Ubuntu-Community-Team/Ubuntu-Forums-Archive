---
title: "Installing the newest ImageMagic with Q8"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by m3rtijn on 2015-07-29
In the official PPA's there only seems to be a very old ImageMagick and only the Q16 version as well.
What's the most reliable way to install the latest ImageMagick, and be able to choose between Q8, Q16 and Q32 as well?

I'm using Ubuntu Server 14.04.02 LTS.

---

### Post by ian-weisser on 2015-07-30
There is no such thing as an 'official PPA'. Ubuntu-supported packages are in the Ubuntu repositories, not PPAs.
PPAs are, by definition, unofficial and supported only by that PPA maintainer or team. If the Imagemagick Packaging Team PPA is not up-to-date, then feel free to query them directly.

I don't understand what you mean by Q8, Q16, and Q32. Perhaps a clarification would help get the answers you seek.

Your version in Ubuntu 14.04 should be 6.7.7
The version in Ubuntu 15.04 is 6.8.9
The latest version seems to be 6.9.1 

There is no fast, easy, non-technical way for you to upgrade to the latest version of imagemagick using packages...unless somebody backports a newer package for you.
There are ways to do it, but they are not easy nor fast.
There are *many* ways to upgrade to the latest version of imagemagick if you are comfortable compiling or packaging or using advanced features of the package manager.

The best way depends upon your skills and preferences.
Tell us a bit about your skills, and how much time/effort you are willing to invest, and we can guide you further.

---

### Post by steeldriver on 2015-07-30
@ian-weisser I think the OP is referring to the default quantum depth (BPP):

> 
--with-quantum-depth     number of bits in a pixel quantum (default 16).   

  Use this option to specify the number of bits to use per pixel quantum  (the size of the red, green, blue, and alpha pixel components). For  example, --with-quantum-depth=8 builds ImageMagick using  8-bit quantums.  Most computer display adapters use 8-bit quantums.  Currently supported arguments are 8, 16, or 32. We recommend the default  of 16 because some image formats support 16 bits-per-pixel. However,  this option is important in determining the overall run-time performance  of ImageMagick.


[http://www.imagemagick.org/script/advanced-unix-installation.php](http://www.imagemagick.org/script/advanced-unix-installation.php)

I recently built GraphicsMagick with a non-default quantum depth, but have not tried doing so with ImageMagick

---

