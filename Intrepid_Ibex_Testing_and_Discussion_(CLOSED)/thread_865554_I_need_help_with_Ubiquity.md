---
title: "I need help with Ubiquity"
date: 2008-07-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2008-07-20
I have no complaints with the installer but I do need to know which files provide the GUI.

I searched the Ubiquity deb package but I'm having trouble pinning down the sourcecode and would like some helpful links and any important info in it's creation/compiling.

I'm trying to see if I can alter the code for my needs.

---

### Post by psyke83 on 2008-07-20
> **TheForkOfJustice said:**
> I have no complaints with the installer but I do need to know which files provide the GUI.

I searched the Ubiquity deb package but I'm having trouble pinning down the sourcecode and would like some helpful links and any important info in it's creation/compiling.

I'm trying to see if I can alter the code for my needs.

If you're using Intrepid*:
```
$ sudo apt-get source ubiquity
```

If not, download the source files from [http://packages.ubuntu.com](http://packages.ubuntu.com) and use "dpkg-source -x ..." to unpack the source (read the man page for dpkg-source for more details).

*The GUI package (ubiquity-frontend-gtk) is actually part of the "ubiquity" source package.

---

### Post by jerrylamos on 2008-07-21
Install from CD Live doesn't work here.  Period.  That's no surprise since weekly newsletter #99 in Forums says to use the Alternate only, which uses text mode for install.  Alternate CD install works fine for me, except don't use manual partitioning to do any changes to the partitions.  That will screw up your partition table.  Use GpartEd Live or Hardy CD Live partition editor (swapoff of course).

The CD Live gui instll was supposed to work on Alpha 2.  It doesn't.  Now they claim it will work for Alpha 3.  Being a veteran of install malfunctions on Hardy, good luck.

Anyway this is a fresh Alternate Intrepid install, plus 209 updates, plus samba and ubuntu-restricted-extras.  Running sort of O.K.; YouTube was pretty sluggish but BBC News video was O.K.

Jerry

---

### Post by psyke83 on 2008-07-21
> **jerrylamos said:**
> Install from CD Live doesn't work here.  Period.  That's no surprise since weekly newsletter #99 in Forums says to use the Alternate only, which uses text mode for install.  Alternate CD install works fine for me, except don't use manual partitioning to do any changes to the partitions.  That will screw up your partition table.  Use GpartEd Live or Hardy CD Live partition editor (swapoff of course).

The CD Live gui instll was supposed to work on Alpha 2.  It doesn't.  Now they claim it will work for Alpha 3.  Being a veteran of install malfunctions on Hardy, good luck.

Anyway this is a fresh Alternate Intrepid install, plus 209 updates, plus samba and ubuntu-restricted-extras.  Running sort of O.K.; YouTube was pretty sluggish but BBC News video was O.K.

Jerry

I haven't read the newsletter, but I think it's more likely that the Live CD was not "ready" for Alpha 2 (and possibly 1) because of an oversized Live CD, not because of a malfunctioning Ubiquity (or perhaps it was for both reasons).

---

