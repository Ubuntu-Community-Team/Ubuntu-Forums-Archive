---
title: "Installing Amarok 1.4.2 from packages.ubuntu.com"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by sbjaved on 2006-08-26
I want to install the latest amarok 1.4.2 and since i don't have my modem configured in ubuntu...Synaptic is not an option for me. I downloaded the following files from packages.ubuntu.com on another PC running XP.
I don't know how to install or what are "depends"...so if someone could tell me how to install these files so i could run amarok...

Files(downloaded from packages.ubuntu.com):
1. amarok_1.4.2.orig.tar.gz 
2. ruby-defaults_1.8.2-1.tar.gz
3. taglib_1.4.orig.tar.gz
4. zlib_1.2.3.orig.tar.gz
5. freetype_2.2.1.orig.tar.gz
6. glib2.0_2.12.2.orig.tar.gz
7. glibc_2.4.orig.tar.gz
8. kdelibs_3.5.4.orig.tar.gz
9. libart-lgpl_2.3.17.orig.tar.gz
10. libice_1.0.1.orig.tar.gz
11. libjpeg6b_6b.orig.tar.gz
12. libpng_1.2.8rel.orig.tar.gz
13. libsm_1.0.1.orig.tar.gz
14. nas_1.8.orig.tar.gz

** All the corresponding .diff and .dsc files were also downloaded.

Now i need to know how to manually install them :)

---

### Post by geoff123 on 2006-08-26
You're better off getting the modem running.
Compiling everything by hand will probably take more work than you are ready for if you've never don that before.  Try searching the web and this forum for tips on how to compile your own programs. Good Luck.

---

### Post by ChrisNiemy on 2006-08-28
Hi!

here you can get .debs for ubuntu dapper and edgy:

example:
```
deb http://imbrandon.com/packages/ dapper amarok
```

(get pgp-key manually if needed)

THe information i got from this thread:
[http://www.ubuntuforums.org/showthread.php?t=244474](http://www.ubuntuforums.org/showthread.php?t=244474)
the package seems to work great, the debs are from a kde developer (check the other thread) an perhaps soon will appear at kubuntu.org


just installed it and works even better than 1.4.1. faster, and no GUI freezes anymore (e.g. when rescanning your collection) Seems like I don't need now a new pc or more ram ;)

Greets -Chris

---

### Post by srt4play on 2006-10-20
Hello sbjaved,

I really doubt you want to compile all of those packages from source.

Go back to packages.ubuntu.com and this time, for example with the amarok package, click on i386 right under where it says "Download Amarok."  This takes you to a page with a list of mirrors to download from. Choose one close to you.  Repeat for the rest of the packages.

What you want are files that end in .deb not .tar.gz

Once you have all of the .deb files in a directory on your target computer, from a terminal in that directory do:

sudo dpkg -i *.deb

---

