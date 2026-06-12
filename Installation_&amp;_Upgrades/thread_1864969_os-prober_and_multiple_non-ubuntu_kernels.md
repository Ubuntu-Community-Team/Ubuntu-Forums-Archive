---
title: "os-prober and multiple non-ubuntu kernels"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by redmaniac on 2011-10-19
Hi all,

I have a triple boot system (Ubuntu, Gentoo and Windows) set up. I just did a kernel ubdate on my Gentoo installation. To simplify things I use Grub2 as set up by Ubuntu (11.04). So far  that worked like a charm (update-grub recognized my Gentoo kernel and made a nice entry in the menu).

After the kernel update (I did not delete the old kernel image, rather I added the newer one alongside it) I once again ran update-grub. It recognized the second Kernel alright but for some reason it decided to give both menu entries the exact same title. Is there any way to fix this without hacking the /boot/grub.conf?

Cheers
redmaniac

---

### Post by raja.genupula on 2011-10-19
Hi 
    Actually update of grub will be done everytime after new update of your kernel so you no need to update the grub after kernel upgrade done.

---

### Post by redmaniac on 2011-10-19
Ok, maybe I was not clear enough about what I meant.

1. I use Grub as installed by and managed within Ubuntu.
2. I have a Gentoo Linux installation on another hard drive
3. update-grub (run manually) will find my Gentoo installation on the other hard drive and provides a menu entry
4. I updated my *Gentoo* kernel. 

Now of course after I update the Gentoo kernel this will not trigger update-grub in Ubuntu (which is in a deep coma at this point, so to speak). So I boot into Ubuntu and run update-grub manually (how else will it know that on another hard drive in another OS, something changed).

After the (Gentoo) kernel update + update-grub there is indeed a second menu entry in /boot/grub/grub.conf 
It's just that this new entry has the same title as the old one (which is still there, as it should). So now I have two Gentoo boot menu entries for different kernels, which show the same title and I have no way to distinguish between them (other than hitting 'e' and looking what's going on under the hood). 

I could just edit /boot/grub/grub.conf but this will be overridden after the next *Ubuntu* kernel update --as you pointed out.

---

### Post by redmaniac on 2011-10-19
Ok, marking this as [SOLVED].

What I had to do was to edit the /etc/grub.d/30_os-prober script.
Essentially there is a place where the title is written:

There is a line

```
menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
```

which I changed to (note the ': ${LKERNEL}'):

```
menuentry "${LLABEL}: ${LKERNEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
```

That did the trick.

If anybody has a more elegant solution I'm still interested in it.

---

### Post by arpanaut on 2011-10-19
Not a complete solution but the latest kernel will always be on top.
Otherwise yes you will need to do some configuration elsewhere in grub.
But editing /boot/grub/grub.conf is not a permanent solution as it gets overwritten each update-grub. 

Maybe this will help:  [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by redmaniac on 2011-10-19
Thanks, that forum post is indeed nice. I might give it a swirl next time I boot my Ubuntu. For now my hack works (it just doesn't look as nice).

Cheers
redmaniac

---

