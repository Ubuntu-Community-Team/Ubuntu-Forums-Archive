---
title: "E: Package 'python-pil' has no installation candidate"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by Paresh on 2012-07-20
Guys, I have recently upgraded from 11.10 to 12.04 and I have an error message when updating:

```
sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  trac-wikiprint
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

When I try to re-install trac-wikiprint, I get:-
```
sudo apt-get install trac-wikiprint 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 trac-wikiprint : Depends: python-pil but it is not installable
E: Unable to correct problems, you have held broken packages.

```

That's easy, just install pythin-pil & it's all good:
```
sudo apt-get install python-pil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-pil is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-pil' has no installation candidate

```
:confused:

So, where to next?

---

### Post by dino99 on 2012-07-20
I'm on Quantal right now, and there is no python-pil package into the repo.

Looking at the needed python dependencies into synaptic:
-python-pisa
-python-imaging
-python-html5lib
-python-reportlab

so the question is : is the trac-wikiprint package you try to install coming from the genuine ubuntu archive ?

---

### Post by Paresh on 2012-07-20
Well, I've been using Trac on Ubuntu for a few years now and trac-wikiprint is a module for Trac.

All was working fine on Oneric, and trac-wikiprint is listed  [here]("http://packages.ubuntu.com/precise/trac-wikiprint").

---

### Post by Paresh on 2012-07-20
What seems odd to me is that python-pil was not a dependancy in oneric, only in precise, and it looks like it's removed again in quantal.  so maybe trac-wikiprint doesn't really need this.

So, is there any way I can alter the dependancy for trac-wikiprint so it doesn't require python-pil?

It's a production server, so I wouldn't want to put quantal on it until it's stable.

---

### Post by Paresh on 2012-07-30
Updates today seem to have resolved the problem.

---

