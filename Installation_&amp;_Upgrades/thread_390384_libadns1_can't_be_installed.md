---
title: "libadns1 can't be installed"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by anomit on 2007-03-21
I am trying to install Ethereal but it needs the libadns1. When I searched for the package, instead of libadns1 I saw a libadns1-bin package.

When I tried to install libadns-1, I got this error message

```
# apt-get install libadns1-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libadns1-bin: Depends: libadns1 but it is not installable
E: Broken packages

```

Please tell  me what should I do to install this package :confused:

---

### Post by zvacet on 2007-03-23
synaptic>edit>fix broken packages
if that doesn´t help in your FF search engine under ubuntu packages write name of your package

---

### Post by elalbibe on 2007-11-10
Upgraded to Gutsy Gibbon;
Using synaptic to install libadsn1.
I get:

[B]libadns1-bin:
 Depends: libadns1  but it is not installable[/B]

I have tried 'fix broken packages' but n.g.

Any ideas?  Should I try installation from a tar ball?

---

