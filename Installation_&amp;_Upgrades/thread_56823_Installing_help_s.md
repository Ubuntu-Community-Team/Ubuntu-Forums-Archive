---
title: "Installing help :s"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by jiberish61 on 2005-08-14
Ok please dont get annoyed with me if this sounds lame. I'm a noob to Linux.

Ive trying to install a few apps but everytime i get to the $ ./configure part it always comes up with an error:

configure: error: could not detect any suitable interpreter.

Please install either the standalone expect/tk interpreter (expectk) at
  [http://expect.nist.gov/](http://expect.nist.gov/)

Or the tcl interpreter with the additional Expect and Tk packages at
  [http://sourceforge.net/projects/tcl/](http://sourceforge.net/projects/tcl/)

I went and ran Synaptic and had a look, but i have already got tcl and tk installed...I have no clue wht Expect or Expectk is.

Further up after i run the ./configure command it says this:
checking package Expect version... no
configure: could not determine Expect version

So im guessing i need this Expect.....Could anyone point me in the right direction here. ty
Joel

---

### Post by manicka on 2005-08-14
What package are you trying to compile?

I'd suggest seeing if it is available via apt-get or synaptic first before going down the compile from source path

---

### Post by jiberish61 on 2005-08-14
well ive been trying to get sourceinstall and gtkpod to work but i cant.
Ive tried running apt-get....wont work and yer...im kinda stuck :s

---

### Post by manicka on 2005-08-14
gtkpod is available in the multiverse repository, which is not enabled by default.

enable it by manually editing your sources list

sudo gedit /etc/apt/sources.list

and make the main repo look like this

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multivers

or 

open Synaptic

Settings-->Repositories

click on Add, then choose Hoary Hedgehog from the drop down menu and select the extra repos you need (Universe and Multiverse are stable and safe IMO) . Click on Ok, the repos will update and you should be able to search for and install gtkpod and gtkpod-aac

---

