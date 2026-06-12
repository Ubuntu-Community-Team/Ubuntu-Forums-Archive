---
title: "Need Help w/ Installing/Compiling ImageMagicK"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by virv on 2006-09-12
starting from source as a tarball, run into problem compiling.

The configure error I get is: no acceptable C compiler found in $PATH

I assume that is becuase the install is specific to a particular linux op.

Is there a imagemagick installer specifically for ubuntu or do I have to tweek things to get it to work.

Anyone have any experience with this?

here's a source for multiple versions:
[ftp://ftp.fifi.org/pub/ImageMagick/](ftp://ftp.fifi.org/pub/ImageMagick/)

Please help!!!

---

### Post by skymt on 2006-09-12
You should install build-essential (sudo aptitude install build-essential).

---

### Post by virv on 2006-09-12
sorry, new to linux, not sure what you mean.

I pasted that cammand into the terminal and hit enter, and it started to do something, but I didn't point it to anything.

I'm assuming I'd need to drag a file or folder from the uncompressed imagemagick folder...

Like I said very new, can't assume I know things. sorry. Could you be more specific?

---

### Post by ohgod on 2006-09-12
ImageMagick is available in the repositories I believe.  So you could fire up Synaptic (via the System->Administration menu) and search for 'imagemagick' to find the right package to install.

The command 'sudo aptitude install build-essential' should install the compiler and build tools you need to compile programs from source.  You could also install the build-essential package from Synaptic.

---

### Post by virv on 2006-09-12
Fantastick!! Thanks!!

I shoulda asked this Question 3 hours ago instead of trying to figure it out myself. You can really burn up the clock w/ this linux stuff.

You saved me loads of time.

---

