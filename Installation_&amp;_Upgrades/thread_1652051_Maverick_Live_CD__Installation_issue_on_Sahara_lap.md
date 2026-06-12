---
title: "Maverick Live CD / Installation issue on Sahara laptop"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by BlueAngel-CPT on 2010-12-24
Hi there everyone,

My sister has this old laptop, it's a Sahara NB610-LE1D, that she wants to use as a karaoke/music machine. Being an avid Ubuntu user for about 2 years now, I recommended an Ubuntu installation with Rhythmbox. Fantastic, she said - you install it and show me how to use it.

I downloaded an iso of version 10.10, burned it and tried to boot up the laptop with it (there is a beta version of Windows 7 on it at the moment that's expired, it's really not usable.)

It gets past the boot-up sound, and the new maverick wallpaper loads, and then it just sits there, with the mouse pointer changing between the pointer and the little circle busy ball. I've left it for a few hours yesterday and nothing else happened.

I've done a memory test, and a disk test, both of which are fine.

I'm about to throw this machine out of the window...

What can I try next?

---

### Post by Rubi1200 on 2010-12-25
Hi,
please post the _full_ specifications for the machine in question.

This sounds as if it might be either a RAM or graphics issue.

Thanks.

---

### Post by BlueAngel-CPT on 2010-12-28
It has a Celeron M 1.6Ghz processor
512Mb RAM
40Gb HDD - with a "beta" version of Windows 7 on it (that has expired)
SiS VGA and (I think) SiS chipset mainboard

---

### Post by Rubi1200 on 2010-12-28
I don't know anything about SIS cards, but I have read that they can be a problem.

Try this though and see if it helps:

When you boot the computer and the GRUB menu comes up and the entry for Ubuntu is highlighted press "e" to edit.

Find the line that ends with > quiet splash

Remove quiet splash and type nomodeset instead.

Then, Ctrl + x to boot.

If that helps we can try and find some other way to make this more permanent.

---

### Post by BlueAngel-CPT on 2010-12-28
Since what I am trying to do is intall Ubuntu, I am booting off the live CD (trying to, at least). What do I need to press to get the grub menu? Because by default it doesn't show.

---

### Post by Rubi1200 on 2010-12-28
Oops! Sorry, thought it was installed already.

To boot from the LiveCD:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop

---

### Post by ubaidillah on 2010-12-28
> **BlueAngel-CPT said:**
> Since what I am trying to do is intall Ubuntu, I am booting off the live CD (trying to, at least). What do I need to press to get the grub menu? Because by default it doesn't show.

I hope this link can help you [http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html](http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html)

---

