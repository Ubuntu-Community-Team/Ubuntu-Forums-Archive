---
title: "delegate libraries"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-11-21
Hi all,

 how to install the delegate library given here:-

[http://rmagick.rubyforge.org/install2-linux.html]("http://rmagick.rubyforge.org/install2-linux.html")

I want to install the FreeType library, instructions given are for unix
can any give me the ubuntu equivalent instructions ?

NB : i use ubuntu 8.04.1

---

### Post by cariboo on 2008-11-21
> Depending on how you originally set up your system you may already have these tools. If not, you'll need to install

    * make(1) - runs the compile and link commands necessary to build RMagick and ImageMagick
    * gcc(1) - the GNU C compiler
    * ld(1) - the GNU linker, generally packaged as part of the GNU binutils

Generally each system has these tools available as pre-built packages. Consult your system documentation for more information.

Install build-essential

>  recommend these delegate libraries:

    * FreeType, Version 2.0 or above, to annotate with TrueType and Postscript Type 1 fonts.
    * libjpeg to read and write JPEG v1 format images.
    * The PNG library, to read and write PNG format images.
    * libwmf 0.2.5 or later, to read and write Windows Meta File (WMF) format images.
    * Ghostscript version 8.10, to read and write the PDF and PS document formats.


Most of these are installed by default use System-->Administration-->Synaptic Package Manager to search for the packages. Use the search button instead of quick search as it uses the name and description to search.

> Step 2: Install ImageMagick

ImageMagick is in the repositories, use Synaptic

> Step 3: Install RMagick

You'll have to follow the instructions for this part.

Jim

---

### Post by sulekha on 2008-11-24
Thanx a lot

---

