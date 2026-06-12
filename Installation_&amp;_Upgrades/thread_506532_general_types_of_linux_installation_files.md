---
title: "general types of linux installation files"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by johntkucz on 2007-07-21
In an effort to sort out the variety of linux installation fikes, I've run into a few roadblocks.

As far as I can tell there are four types of file

[LIST=1]
[*]source code (raw, uncompiled, programming linauage, to use this you must compile it into a binary file)
[*]Binary files -- compiled source code files (lacking any form of configuration files, must be manually placed in a folder and run from there)
[*]Self-Extracting Binaries -- same as a binary file but with an installation gui wizard
[*]Packages -- ending with .dep or .rpm extensions, these are compiled files necessary to run a program
[/LIST]
What, then, is the difference between a package and a binary file?  They're both compiled, they neither have wizards. How do binaries and packages differ?
 

Thanks.

---

### Post by kidders on 2007-07-23
Hi there,

With most distros, there are two types of application installation... supported (ie native), and unsupported (ie non-native). Software packages compatible with the Debian installer (apt) are the only recommended kinds to use on a Ubuntu system, unless you know what you're doing. These may contain a variety of things, including source code & binaries.

Typically, the information necessary to install an application (often called a "package") is nothing more than an archive in some sort of standard format. To answer your question, a binary is a file containing an executable block of bytecode. A "package" is just a generic term for an arbitrary lump of stuff.

Incidentally (since you mentioned them), RPMs are Red Hat software packages. They're used by a variety of distros, including Mandriva.

---

