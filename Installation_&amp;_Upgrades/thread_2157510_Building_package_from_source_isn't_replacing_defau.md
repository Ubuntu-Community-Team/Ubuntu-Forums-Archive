---
title: "Building package from source isn't replacing default package"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by ajck on 2013-06-25
Hi,

How do I replace the default version of a package in the default install of my distro (latest Ubuntu 32-bit server) with the latest version I've built from source?

I've built from source a few packages using the standard ./configure or cmake, then make, then make install and yet although the build process seems to go perfectly in each case with no errors, the older default versions that came with Ubuntu are still being used by the system.

Any ideas please?

Further relevant details if needed:

I'm installing something called Pango, which depends on another package Harfbuzz and also FontConfig. Ubuntu shipped with these. I downloaded and built later versions of each from source, yet checking the installed package afterwards with 'dpkg --get-selections' gives the older version.
So a.) I am not sure Pango is being built with reference to the newer Harfbuzz and Fontconfig 've also built from source beforehand, or instead using the older versions that came with Ubuntu, and b.) my C program that I access Pango API with is I assume using older default Pango too (I just tell the gcc compiler to link with the 'pangocairo' library).

For each package, I am building the source in /usr/local/bin/[package name]/
and 'make install' is putting the compiled libs in /usr/local/lib
I then tried copying compiled libs to /usr/lib but the older versions are still in Ubuntu's default location of /usr/lib/i386-linux-gnu/ - I could try deleting these and copying in the latest versions, but this seems messy - is there a cleaner solution or standard practice (I'm not sure what steps I'm missing out or other files/configs that need updating if I start manually copying!)

Many thanks for any info.

Alex

---

### Post by sisco311 on 2013-06-25
Hi and welcome to the forums!

You can use checkinstall to install your compiled packages:
[uhelp]community/CheckInstall[/uhelp]

---

### Post by Kujua on 2013-06-25
Generally when you build from source, executables and libraries are put in directories which have precedence over those coming from packages.
For eg: default binaries might go under /usr/lib, while what you compile might go under /usr/local/lib (based on the arguments to configure script)

To confirm which library your program is using, you can do this:
```
ldd your-program
```

---

