---
title: "Problem after installation"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by zezito555 on 2008-06-29
Hello to all
ive got this problem i cant solve
i installed ubuntu and every thing seemed to be fine until i rebooted the pc.
the 1st "page" (where the Ubuntu symbol and password input are shown) is out of site, i mean i can only look at the symbol and i canonly read Ubun ! i hope i can explain myself!
its like, if u split a monitor with a cross, i can only look at the top left image! 
Btw im using a S3 unichrome on board video card.
...But if i run Ubuntu from a CD its normal!!!
Can anyone help me with this!

Thanks

---

### Post by wpshooter on 2008-06-29
My suggestion would be to do the installation from the ALTERNATE (text based) CD instead of the Live CD version.

I would try it as a regular install with the ALTERNATE first and then if that does not solve the problem, I would attempt to install from the ALTERNATE using the safe graphics mode.

Good luck.

---

### Post by Marshal0505 on 2008-06-29
> **zezito555 said:**
> Hello to all
ive got this problem i cant solve
i installed ubuntu and every thing seemed to be fine until i rebooted the pc.
the 1st "page" (where the Ubuntu symbol and password input are shown) is out of site, i mean i can only look at the symbol and i canonly read Ubun ! i hope i can explain myself!
its like, if u split a monitor with a cross, i can only look at the top left image! 
Btw im using a S3 unichrome on board video card.
...But if i run Ubuntu from a CD its normal!!!
Can anyone help me with this!

Thanks

I have solved this on my computer by doing this.
I opened a terminal with ctrl+alt+F1 and typed:

```
sudo nano /etc/X11/xorg.conf
```

I noticed a line that contained something like this:
"virtual mode 21**x15**" (can't remember exactly)and changed it to "virtual mode 1600x1200" ....change it to anything that works for your hardware. 1280x1024 or 1024x768 for instance.

close and save your changes by typing ctrl+x and answering yes (y) to changes. Hope this helps.

---

