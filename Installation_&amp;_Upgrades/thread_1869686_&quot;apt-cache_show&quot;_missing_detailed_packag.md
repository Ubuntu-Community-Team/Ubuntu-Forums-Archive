---
title: "&quot;apt-cache show&quot; missing detailed package descriptions"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by monoab314 on 2011-10-26
Hi all

I have two fresh installs of Lubuntu Oneiric i386.  Apt-cache show is behaving differently on the two boxes even though the config under /etc/apt are identical, even the archive servers in use.  In the one case the detailed package descriptions is missing.  E.g. here is the diff between the two of "apt-cache show hello":

> 
16,23c16
< Description-en: The classic greeting, and a good example
<  The GNU hello program produces a familiar, friendly greeting.  It
<  allows non-programmers to use a classic computer science tool which
<  would otherwise be unavailable to them.
<  .
<  Seriously, though: this is an example of how to do a Debian package.
<  It is the Debian version of the GNU Project's `hello world' program
<  (which is itself an example for the GNU Project).
---
> Description: The classic greeting, and a good example


This is very frustrating when searching for new packages to install.  The descriptions is also missing in synaptic.

Any ideas?
Thanks

---

### Post by monoab314 on 2011-11-07
Found the problem.  We use a proxy at work and it doesn't return the translation indexes.

---

