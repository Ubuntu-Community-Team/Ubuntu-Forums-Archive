---
title: "USB install gave me processor errors?"
date: 2020-02-19
forum: Installation &amp; Upgrades
---

### Post by PsychedelicWonders on 2020-02-19
So I was trying to re-install Ubuntu on a SSD that has Ubuntu 16.4  on, but it's been a while & I forgot my user password so I can't seem to do a normal upgrade from within the operating system.

So I was going to re-install it via a USB, but I seem to be getting some errors related to something about a Unique Processor

Here are some screenshots of the bootup sequence:

[ATTACH=CONFIG]285048[/ATTACH][ATTACH=CONFIG]285049[/ATTACH]


[ATTACH=CONFIG]285051[/ATTACH][ATTACH=CONFIG]285052[/ATTACH]

Any idea what's wrong?  Is the .iso install bad on the USB?

---

### Post by PsychedelicWonders on 2020-02-22
Anyone have an idea?  I tried it with two different usb sticks and using the rufus installer and still getting the same errors.

Thanks!

---

### Post by mörgæs on 2020-02-22
An error report mentioning [mce]("https://en.wikipedia.org/wiki/Machine-check_exception") is a bad sign. 

The page offers some advice, and besides that I suggest googling 'mce' + your computer name.

---

### Post by PsychedelicWonders on 2020-03-02
I have an Intel 5820x and I built it myself on an Asrock motherboard.

It  seems one of the reasons this happens is a clogged heatsink and mine is  filthy.  I'm going to try and give everything a good clean and add some  new thermal paste.

Windows seems to work fine?  It has been  loading slow lately, sometimes up to a couple of minutes for an SSD,  which I know isn't right.

But if Windows is booting fine, why would the Ubuntu install fail like this?

---

### Post by Skaperen on 2020-03-03
**do not add new paste over old paste.**  clean both the processor and heat sink down to bare metal then apply new paste exactly as instructed by the paste instructions.

---

### Post by PsychedelicWonders on 2020-03-03
Oh yeah I'm pretty strict about removing all of the old paste completely before any new paste is put down.

But thanks for the tip!

---

