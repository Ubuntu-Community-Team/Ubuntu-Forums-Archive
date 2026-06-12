---
title: "Synaptics cannot find packages"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by bnebb on 2009-12-05
I just did a fresh install of 9.10.  Began to add packages.  Installed the Medibuntu repository and it seems OK.  But, Synaptics cannot find packages like w32codecs, etc.  I did install via console but Synaptic cannot find the installed package even.  It appears that it is not reading the database correctly.  

Any idea how to fix this?

Bnebb

---

### Post by MelDJ on 2009-12-05
the w32 codecs and other codecs are under one package named ubuntu-restricted-extras

---

### Post by mkvnmtr on 2009-12-05
The codecs should be a seperate package in your package manager after you have enabled the Medibuntu repository. Check your package manager or software sources to see if medibuntu is enabled. If you left out a letter when you cut and pastes into the terminal it will not be enabled and you will need to do it again.

---

### Post by wilee-nilee on 2009-12-05
You have to add the medibuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bnebb on 2009-12-05
Thanks to all of you.  I found unbuntu-restricted-extras by Synaptic.  Am installing it as I write.  But, I had already installed msttcorefonts and w32codecs before and Synaptic still could not find those packages installed.

I did enable the Medibuntu repositories using the link provided.  It appeared to be successful.

Funny, I have another machine that I installed all this stuff about two weeks ago and went through the same procedure.  Synaptic does find all the packages.

Strange.

Well, let's see what Synaptic does when I finish the general restricted package install.

Stay tuned.

Bnebb

---

### Post by bnebb on 2009-12-05
Well, finished installing the ubuntu restricted extras.  Synaptic still cannot find w32codecs or msttcorefonts.  It DOES find gstreamer and the other stuff in the package.

Go figure.  I'm at a loss to figure it out.

Bnebb

---

### Post by wilee-nilee on 2009-12-05
Have run sudo apt-get update or reload in synaptic w32 wont be there until you reload after installing the medibuntu.

You can install the MS core fonts by installing the msttcorefonts package. To do this, enable the “Universe” component of the repositories.

---

