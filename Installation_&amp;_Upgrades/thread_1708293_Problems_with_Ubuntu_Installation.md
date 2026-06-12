---
title: "Problems with Ubuntu Installation"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by HandH on 2011-03-16
Hi,

Im new to the forum and to Ubuntu. I have a HP 'tablet' laptop which has no operating system installed and I was hoping to install Ubuntu.  

I downloaded ubuntu and the software to make it possible to boot from usb. I started the laptop up selected the option to boot from the usb.

But now it says "marking TSC unstable due to TSC halts in idle" and then on the next line it says "switching to clocksource hpet" and it has been like this for hours.

Any ideas as to what's gone wrong?

The laptop specs are: Intel Core 2 CPU T5600 @ 1833MHz with 1GB of RAM.

Many thanks.

---

### Post by HandH on 2011-03-25
Hi people 

Can anybody odder any advice?

Thanks

---

### Post by Quackers on 2011-03-25
Welcome to UF.
I'm not sure about TSC, but hpet is a function within the DSDT, which is part of the computer's bios. I'm wondering if there is a time problem of some kind. I'm guessing the cmos battery may be dodgy? But, in all honesty, I could be way off base here. Sorry I can't be more helpful. My bios knowledge is very limited.

---

### Post by Quackers on 2011-03-25
One thing you could do to check the time aspect is to go into the computer's bios settings and check whether the time shown is correct. If it isn't, set the correct time and other settings and save the changes then exit bios. Turn the computer off and leave it for an hour or two. Then go back in to the bios and check the time again - is it still correct?

---

