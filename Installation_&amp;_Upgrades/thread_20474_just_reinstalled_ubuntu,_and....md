---
title: "just reinstalled ubuntu, and..."
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by rudeboyskunk on 2005-03-17
i just reinstalled warty, and every time i do apt-get dist-upgrade, i get this error for linux-image-2.6.8.1-3-386 (2.6.8.1-16.1):

There was a problem running depmod.  This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
        depmod exited with return value 0
        depmod got a signal 7
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.8.1-3-386/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot.
Would you like to abort now? [Yes]
dpkg: error processing linux-image-2.6.8.1-3-386 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.8.1-3-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@timebomb:/home/rudepirate #

---

### Post by az on 2005-03-17
" linux-image-2.6.8.1-3-386"

Isn't the newest kernel linux-2.6.8.1-4-386?

If you have two kernel packages installed (you should) try answering no to the do you want to quit now question....

(sudo apt-get -f install)

---

### Post by rudeboyskunk on 2005-03-17
AWESOME, answering no seems to have fixed the problem.  thanks!

---

