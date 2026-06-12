---
title: "Installer fails on CD Check."
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by useperl on 2005-06-02
Downloaded a iso last night and today. 

Both fail the integrity checks during the installation phase.

Is their a known issue? Perhaps OS-X is munging the CD?

This is on a Dell D610 which from all accounts (google) seems to work well.

-useperl

---

### Post by mingus on 2005-06-02
Have you checked the MD5 sum?

[http://releases.ubuntu.com/hoary/MD5SUMS](http://releases.ubuntu.com/hoary/MD5SUMS)

If this is new, there are a number of free pgms to do this with, search the forums or google.

---

### Post by useperl on 2005-06-02
$ md5sum ubuntu-5.04-install-i386.iso
 
f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso

f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso

They match.

Any other idears?

---

### Post by mingus on 2005-06-02
In the forum thread:

[http://ubuntuforums.org/archive/index.php/t-25388.html](http://ubuntuforums.org/archive/index.php/t-25388.html)

deals with corrupted files, even when the md5 is clean.  Note last post.

No idea of course if this is your specific problem.  Search forums & google for more ideas.

---

### Post by alastair on 2005-06-02
I don't know what the problem is, but I have had problems in the past with CD's caused by DMA. You might try booting with the option (I think) : "ide=nodma". See if this helps. It will be a lot slower on an install though (if it works).

---

