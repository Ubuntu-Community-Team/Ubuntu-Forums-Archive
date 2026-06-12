---
title: "Some packages to be REMOVED instead of upgraded - why?"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by AJI on 2005-10-23
Per [https://wiki.ubuntu.com/BreezyUpgrade]("https://wiki.ubuntu.com/BreezyUpgrade") I changed my sources.list to point to breezy instead of hoary.

Ran apt-get update, then apt-get dist-upgrade, and was warned that around 30 packages would be REMOVED, in addition to the bunches to get installed & upgraded (*156 upgraded, 26 newly installed, 33 to remove and 89 not upgraded.*).

For example, gnucash would be REMOVED, and gnucash-docs would be upgraded.

Here's the problem: I don't understand why gnucash would be removed and another similar package would be upgraded, **when both have higher version numbers in breezy than what is currently on my system.**

Here's the info on the packages:

Package: gnucash
Versions:
1.8.10-18(/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages)
1.8.9-4ubuntu2(/var/lib/dpkg/status)

Package: gnucash-docs
Versions:
1.8.5-1(/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages)
1.8.4-5(/var/lib/dpkg/status)

To my untrained eyes, both packages appear to have higher versions in breezy, so **why would only one get upgraded**?

---

### Post by TheOtherShoe on 2005-10-23
The main feature that distinguishes the dist-upgrade operation from the upgrade operation is that dist-upgrade will try to remove packages that introduce conflicts with other packages. It seems that in your case there is a package installed that conflicts with either gnucash or one of its dependencies.

Try upgrading to the new version of gnucash before doing the dist-upgrade. Hopefully that will point to the problem.

---

### Post by AJI on 2005-10-23
[QUOTE=TheOtherShoe]Try upgrading to the new version of gnucash before doing the dist-upgrade. Hopefully that will point to the problem.[/QUOTE]

It did (sort of).  There was a library dependency problem with gnucash, so I just decided to let dist-upgrade remove all those packages and I would reinstall after the upgrade.

Now, I have a more pressing problem: **where is my upgrade?**

I ran apt-get dist-upgrade, let it remove the 30-odd packages, noted that it was holding back 89 packages, and let it download & install.  I rebooted.

Nothing happened Breezy-wise: no new kernel in the boot menu, KDE looked exactly the same, and as far as I can tell, all I have is 150 or so upgraded packages.  **It appears I have not been upgraded to Breezy.**

What in the world do I need to do to actually upgrade?  I'm at a loss here. :confused:

I assume that if apt-cache showpkg ubuntu-base shows this:

Package: ubuntu-base
Versions:
0.80(/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages)
0.43(/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_main_binary-amd64_Packages)(/var/lib/dpkg/status)

that hoary is still here.

---

### Post by AJI on 2005-10-24
](*,)  Sometimes I am my own worst enemy...

Two problems:
[LIST]
[*]I installed ubuntu-desktop instead of kubuntu-desktop (I am using Kubuntu; I followed the upgrade directions too blindly).
[*]My sources.list still had a reference to the Kubuntu Hoary CD from the original install.
[/LIST]
Installed kubuntu-desktop, rebooted (just to be safe), ran apt-get update, then apt-get dist-upgrade and **now I see there's ~650MB of goodness to download**.

May my mistakes save someone else from repeating them!

---

