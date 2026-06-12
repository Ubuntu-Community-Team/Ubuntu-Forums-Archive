---
title: "make dselect download 64-bit packages with 32-bit laptop"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by orangep on 2013-03-09
Hi. I have no internet connection because of a major disagreement with the dishonest phone company called Qwest.
So my current situatioin is that I use the free wifi at the library. That leaves me with one difficult problem: I have 64-bit AMD machines
at home, and carry a 32-bit laptop to the library. Updating the laptop is no problem.

But manually downloading new software for the 64-bit machines is a nightmare because every package that I download manually
needs three more supporting packages and libraries, each of which needs more packages, which need more...
You know, it goes on forever.

A program like dselect solves the problem nicely. It resolves all of the dependencies and fetches all needed supporting packages.
The gotcha is that, so far, it only works with the native 32-bit system in the laptop. It naturally downloads the correct 32-bit packages
for itself.

Is there some way to put an alternate package list (from the AMD 64-bit machines, like /var/cache/apt/* ) somewhere and convince dselect to look at that list and download 64-bit packages, so that I can use the laptop to download complete updates and clusters of packages for the 64-bit AMD machines at home?

Thank you.

---

### Post by tgalati4 on 2013-03-09
I don't know much about dselect, but installing it and reading the man page, you could use the **HOME** switch:

ENVIRONMENT
       HOME   If set, dselect will use it as the directory from which to read the user specific configuration file.  

Now what to put in that configuration file is another matter.  I don't know if there is a setting to ignore architecture (32-bit vs 64-bit).

As an alternative, I assume that dselect is open source, so you could download the source package and look through the code and comment out the check for architecture and recompile it.  Sounds like a lot of work.  Might have better luck finding a used 64-bit laptop to gather your packages or find a better internet service provider.

Another method is to use *apt-cache depends* <package> and print out the package list, then simply pull the deb files for the required packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).  It's a slow method, but can't be any worse than the other methods.  You will get a good understanding of package dependencies.

---

### Post by orangep on 2013-03-11
Thanks for the suggestions. I will look into that. I've also been thinking about chroot, and faking out dselect into looking at a different /var/cache/apt to find its files.

The apt-cache depends command will be a big help for just downloading one or two packages and all dependencies. Thanks

---

