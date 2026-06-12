---
title: "Grub 2 - rootnoverify gone, how to boot BeOS??"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by FA-2 on 2010-01-17
I was using a previous version of ubuntu that came with grub 0.97 (I think).  I was able to boot to BeOS on its own partition using the following:

BeOS 
   rootnoverify (hd0,5)
   chainloader +1

rootnoverify is what made it work.  Without rootnoverify, BeOS would not boot.

When I upgraded to ubuntu 9.10, it "comes with" Grub 2.  grub didn't find the partition automatically, so I added the entry above to the /etc/grub.d/40_custom file, ran update-grub, and rebooted.

Grub 2 no longer supports rootnoverify.  It told me so when I attempted to boot BeOS.  I did some searching, and rootnoverify has apparently been declared "useless' (I found that on a Grub 2 page on the ubuntu site).  I tried changing it to root=(hd0,5) and I get a signature error & no boot.

What should be used in place of rootnoverify?  It does not seem too useless to me! :confused:

on edit:  I forgot to mention, I am trying to boot BeOS PE5 MAX, if it makes a difference.

---

### Post by kansasnoob on 2010-01-17
Try:

```
sudo gedit /etc/grub.d/40_custom
```

And edit to look like this:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "BeOS" {
    set root=(hd**[COLOR="Red"]X,Y[/COLOR]**)
    chainloader +1
}

```

Of course the X,Y must be replaced with the disc and partition numbers. **[COLOR="Red"]But grub2 numbering changed slightly:[/COLOR]**

Discs still begin with 0 (zero) just like legacy grub, but **partitions now begin with 1 (one)**, so sda1 is now (hd0,1) instead of (hd0,0) like in legacy grub.

You were using (hd0,5) which is /dev/sda5. Is BeOS on sda5? or sda6?

Oops forgot to say, must update-grub after each change to /etc/grub.d/40_custom:

```
sudo update-grub
```

---

### Post by kansasnoob on 2010-01-17
Oh, and just so you don't panic, if all else fails you can revert to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Hopefully you'll only do so as a last resort though :)

Grub2 really is nice once you get used to it, although there are still a few corner issues where it may not work, that's why I wrote that HowTo.

---

