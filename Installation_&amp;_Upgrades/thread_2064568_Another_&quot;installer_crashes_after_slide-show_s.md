---
title: "Another &quot;installer crashes after slide-show starts&quot;"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by pottzie on 2012-09-29
I'm trying to install Lubuntu 12.04 from a live cd, and the installer crashes after the slide show starts. The fix is supposed to be (I thought) opening a terminal and running either " sudo apt-get remove ubiquity-slideshow-ubuntustudio" or "sudo apt-get remove ubiquity-slideshow-ubuntu." When I ran both commands, bash said that neither were installed, but when I tried to install after that, the slide-show started and promptly failed. I still have the "spinning cursor," and the install is going nowhere, as I type this.

 Is there a fix? Seems like I remember being able to install from the command line, but what searching I've done so far hasn't turned anything up.

 Thanks.

---

### Post by haresear on 2012-09-30
There are several flavors of ubiquity-slideshow. I think I used synaptic to search for "ubiquity slideshow", and then uninstalled whichever one came up as installed. I don't remember if synaptic is installed on the Lubuntu live CD, but if not, you can install it first.

Update: I just checked, and there is a "ubiquity-slideshow-lubuntu", so you might want to try uninstalling that.

---

### Post by pottzie on 2012-09-30
"Update: I just checked, and there is a "ubiquity-slideshow-lubuntu", so you might want to try uninstalling that."

 Say the magic words and the duck comes down from the ceiling. Viola! Success.

 Thanks!

---

### Post by haresear on 2012-09-30
Glad I could help.

---

