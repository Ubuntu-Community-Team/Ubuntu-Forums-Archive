---
title: "Install on computer with no internet access"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by JaySeeJC on 2011-07-09
Just wondering if it's possible to install kubuntu on an isolated computer and then be able to copy all the debs from the cache of another computer. Basicly what i want ot do is the following:
-Install Kubuntu on a fresh, isolated computer
-Copy the online package list to that new computer from an old Kubuntu install (both are 11.04) so that i can satisfy dependencies of the debs i wish to reinstall
-Reinstall the debs onto the new installation with proper dependency resolving
I definately hope it's possible, but if not the 2nd step is skippable

---

### Post by ajgreeny on 2011-07-09
Have a look at aptoncd, which can be used to do what you want.

Or you can simply copy all the .deb files from /var/cache/apt/archives on a connected machine that has all the packages installed, to the same folder in your non-connected machine, then use synaptic or any other method to install those same packages.  I do it very often to save time and bandwidth.

---

### Post by JaySeeJC on 2011-07-09
> **ajgreeny said:**
> Have a look at aptoncd, which can be used to do what you want.

Or you can simply copy all the .deb files from /var/cache/apt/archives on a connected machine that has all the packages installed, to the same folder in your non-connected machine, then use synaptic or any other method to install those same packages.  I do it very often to save time and bandwidth.

I have tried tha.
The only problem i get is that the isolated computer doesn't know about most of the dependencies and so give me tons of errors. What i really need to know is how to copy the local list of all instalable packages to the isolated computer.

---

### Post by ajgreeny on 2011-07-10
> **JaySeeJC said:**
> I have tried tha.
The only problem i get is that the isolated computer doesn't know about most of the dependencies and so give me tons of errors. What i really need to know is how to copy the local list of all instalable packages to the isolated computer.
I do not understand why the isolated computer does not know about the dependencies needed.  If you installed, or used synaptic simply to download all the packages with their dependencies, they would all be in /var/cache/apt/archives, and when copied over to the isolated computer should be found and installed.

If you want a list of all installable packages as a text file of some sort, that will not be of any help, as it is the actual packages you need, not just a list of their names.  And to download "all installable packages" would be a huge download, though I have no idea just how many GBs it would be.

Have I misunderstood you, or have you misunderstood me?  How did you use aptoncd, or did you just copy over all the .deb files?  I'm sure it should work, as I have done it this way myself several times, so I am rather baffled.

---

