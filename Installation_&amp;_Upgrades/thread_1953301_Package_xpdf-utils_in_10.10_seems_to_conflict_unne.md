---
title: "Package xpdf-utils in 10.10 seems to conflict unnecessarily with other packages!"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by santosh83 on 2012-04-06
Hi all,

Just now when I was installing xpdf to try out a lightweight PDF viewer, when I tried to mark the package 'xpdf-utils' to be installed in Synaptic, a dialog popped up telling me that the following list of installed packages would be removed:

```
bluez-cups
cups
cups-driver-gutenprint
foo2zjs
foomatic-db-compressed-ppds
ghostscript-cups
hplip
hplip-cups
kubuntu-desktop
lsb
lsb-printing
poppler-utils
pxljr
splix
ubuntu-desktop
xubuntu-desktop

```

This seems to me to be a bug in xpdf-utils package. Surely it shouldn't need to uninstall all these packages to function!! Most of them have no relation to PDF files at all!

My system is fully updated Maverick (64-bit.)

The package 'xpdf-utils' seems to have two versions available:
3.02-9ubuntu1.1 (maverick updates) - this is default
3.02-9ubuntu1 (maverick)

When I force the 2nd version, largely the same 'to be uninstalled' list as above is displayed, with the addition of 'xpdf-reader' as well!

Do others have the same issue, either in Maverick or more recent releases? Is this a package bug? Should I report a bug?

Thanks.

---

### Post by Paddy Landau on 2012-04-06
That does seem a bit strange. I am using 11.04, and if I ask to install xpdf it does not try to uninstall anything. I can only guess that the version conflicts with the older versions on Maverick.

You say you need a lightweight reader, which would be why you are not using Adobe Reader. Why don't you use the default (Evince), which is lightweight?

---

### Post by santosh83 on 2012-04-06
> **Paddy Landau said:**
> That does seem a bit strange. I am using 11.04, and if I ask to install xpdf it does not try to uninstall anything. I can only guess that the version conflicts with the older versions on Maverick.

Actually xpdf itself installed fine for me! It was the 'xpdf-utils' package that had this issue.

> You say you need a lightweight reader, which would be why you are not using Adobe Reader. Why don't you use the default (Evince), which is lightweight?

Evince is what I use and am satisfied with it! I actually wanted to try out the others, just for comparison's sake. I've got apvlv, xpdf, gv, and epdfview installed, apart from evince. In terms of point-and-click usability Evince and the slightly lighter weight epdfview win hands down. Am still learn the shortcut-keys to take the other three for a spin! Okular is also great, but it sticks out like a sore thumb on my default GNOME desktop! :-(

As for Adobe Acrobat, 'nuff said! :-)

---

### Post by Paddy Landau on 2012-04-06
> **santosh83 said:**
> It was the 'xpdf-utils' package that had this issue.
It works fine for me. It must be something to do with the older version.

> **santosh83 said:**
> As for Adobe Acrobat, 'nuff said! :-)
Well, I prefer Adobe Reader. It is "heavier" but it has greater functionality, especially with printing, that I often use.

---

### Post by santosh83 on 2012-04-06
> **Paddy Landau said:**
> It works fine for me. It must be something to do with the older version.


Well, I prefer Adobe Reader. It is "heavier" but it has greater functionality, especially with printing, that I often use.

That's true. I hope though Adobe shows more commitment  towards their Linux port of Reader than Flash player. Probably irrational, but I've always been leery of Linux ports of popular proprietary programs. It's not only a blackbox for the community, but it also feels like you're a child whose candy could be snatched away anytime! :-)

---

### Post by BarryDocks on 2013-02-23
same problem with 10.04 LTS

---

