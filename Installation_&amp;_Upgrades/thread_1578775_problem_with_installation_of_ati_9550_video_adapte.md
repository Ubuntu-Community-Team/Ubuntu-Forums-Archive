---
title: "problem with installation of ati 9550 video adapter"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by siimoz on 2010-09-20
first of all i'm new user of linux and here is the problem 

[B]i cannot install my video card ( ati 9550 ) in linux ubuntu 10.04
after downloading the driver files from ati site this appear during installation[/B] 

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.34-02063… make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.yi7vlF


Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.34-02063… make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.yi7vlF

thx

---

### Post by siimoz on 2010-09-21
any one help me pls :confused:

---

### Post by Mark Phelps on 2010-09-21
There are no downloadable drivers that will work with your card and current versions of Ubuntu.  What used to be ATI dropped fglrx driver support for your card a long time ago.

The only working drivers available now are the open-source drivers -- and they are automatically installed with Ubuntu.

So basically, if you're seeing a graphical desktop, you already have the only working drivers installed.

---

### Post by siimoz on 2010-09-21
What Do You mean with a graphical desktop ?
and there isnot any way to setup my driver ??

---

### Post by Mark Phelps on 2010-09-22
> **siimoz said:**
> What Do You mean with a graphical desktop ?

If you're getting a desktop, with bars on the top and bottom, and icons -- that's a graphical desktop.  If you only have a black screen with lines of text -- that's a Command Line Interface (CLI).  If you were getting the latter, I'm presuming you would have said so.

> and there isnot any way to setup my driver ??

As I already said -- no.  IF you download anything and try to force an install, either it will fail, or it will trash your display -- forcing you to go through a LOT of trouble to remove the invalid drivers and restore the ones you already have.

---

### Post by siimoz on 2010-09-24
> **Mark Phelps said:**
> If you're getting a desktop, with bars on the top and bottom, and icons -- that's a graphical desktop.  If you only have a black screen with lines of text -- that's a Command Line Interface (CLI).  If you were getting the latter, I'm presuming you would have said so.



As I already said -- no.  IF you download anything and try to force an install, either it will fail, or it will trash your display -- forcing you to go through a LOT of trouble to remove the invalid drivers and restore the ones you already have.
thank you :)
and i already have a graphical desktop :)

---

