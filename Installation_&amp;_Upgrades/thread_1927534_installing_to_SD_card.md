---
title: "installing to SD card"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by secretreeve on 2012-02-18
hey guys,

i could do with a little information on installing the latest ubuntu to an SD card as i intend on using it with the rasberry Pi system.

thanks in advance!

---

### Post by athampan on 2012-02-18
Saw this via google:
[http://wiki.geteasypeasy.com/Install:_from_a_Live_Ubuntu_CD_directly_onto_an_SD_card_using_a_desktop%28or_laptop%29_pc](http://wiki.geteasypeasy.com/Install:_from_a_Live_Ubuntu_CD_directly_onto_an_SD_card_using_a_desktop%28or_laptop%29_pc)

Not sure whether it'd be useful to you.

---

### Post by secretreeve on 2012-02-18
i saw that as well, was hoping there would be an easier way.

also is the 32bit viable for the ARM processors?

---

### Post by athampan on 2012-02-18
I thought it was quite easy (especially if you do it the virtualbox way).  As regards your ARM processor... from my understanding from this wikipedia article: [http://en.wikipedia.org/wiki/ARM_architecture#ARM_cores](http://en.wikipedia.org/wiki/ARM_architecture#ARM_cores) and the Raspberry PI FAQs (saying that it sports ARM11 core which translates to ARMv6 per the wiki page), you need 32 bit version of ubuntu.

Update: of course, instead of the eee pc, you will be having your raspberry pi computer (and won't have the complications of eee pc boot procedures).

The way I would go about doing it is:
(a) plug the SD card into my android phone and the android phone into a running ubuntu computer with virtual box (configuring my android to act as mass storage) and it will show up on my ubuntu... I will have to click on the storage configuration in vbox and add a disk from the SD card partition - I assume you will configure it using gparted as an ext4 fs prior to doing all this.
(b) follow the procedure in the link to my first response 
(c) shut down the vbox
(d) unplug android
(e) rip off the SD card
(f) put it into the raspberry pi and boot it up.

However, I admit that I haven't tried it (although it looks to be a do-able thing ... don't have access to/have not explored an easy way of getting raspberry pi in India :-))

---

### Post by efflandt on 2012-02-18
ext2 may be better for SD due to less writes (no journaling).  There is no TRIM for SD (like for SSD), so that is not a reason to use ext4.

I don't remember ever having any problems with ext2, even long ago when drives overheated running SETI@home (100% cpu) after inlet fan totally plugged up with lint (it just threw an error that it could not write the log).  It rebooted fine after after pulling the dust bunny out of it.  One old Celeron 300 PC using ext2 ran SuSE 8.2 headless five years 24/7 without shutting down (July 2006 until shutdown for long power failure July 2011).  Automatic fsck on reboot did not find any problems.

I have had drives fail, but usually gradual deterioration of sectors, always confirmed by mfr diagnostics to be a drive problem.  No warranty replacement ever had a problem.

I use ext2 on the 32 GB SDHC used to boot 64-bit 11.10 on my Acer W500P Tablet PC.

---

### Post by secretreeve on 2012-02-18
wow thanks.

the raspberry pi isnt available as of yet, coming out monday lol.

should be an interesting project i got in mind but your instructions there will be most helpful. i'll just have to setup ubuntu on my desktop first as im on windows at the moment.

a returnung buntu'er lol

---

### Post by athampan on 2012-02-18
@efflandt - thanks for correcting me - yes @secreteve, you might be better off with ext2 fs.  Good luck with your initiative :-)


@secreteeve, there's also virtualbox for windoz here: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) (you could maybe use easeus for partitioning your SD to ext2)

---

