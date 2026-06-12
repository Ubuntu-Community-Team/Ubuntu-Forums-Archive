---
title: "Installed 12.04. Black screen white cursor."
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Viau on 2012-06-04
Hey! I finally gave Ubuntu a go (after a 5 year vacation from it)
And I followed the tutorial on how to boot with usb drive.
Now Ubuntu is in the usb drive and working perfectly in live mode.
I clicked on install ubuntu and it installed on the hard drive (320gb) and flushed everything. 

After the installation has completed, it is hanging on a black screen and has a white cursor blinking.
Now here is the situation: I thought: oh maybe the installation went wrong somewhere.. So I decided I'd boot from the usb drive again to reinstal. And to my surprise ubuntu loaded with the username I had selected when installing. And it's loading from the USB DRIVE!! (The light is blinking on the pendrive)

I have tried holding the shift key on the keyboard when booting, no go. Now I'm about to give up.

---

### Post by Viau on 2012-06-04
Ok, so I have reinstaled ubuntu, figuring out that maybe the swap was installed on the usb drive (makes a lot of sense).
I partitioned manually the drive, using this guide: [http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)
And now, guess what? It's fixed!! :D

---

