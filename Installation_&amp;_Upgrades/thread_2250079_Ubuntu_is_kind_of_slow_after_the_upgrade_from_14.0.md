---
title: "Ubuntu is kind of slow after the upgrade from 14.04 to 14.10"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2014-10-26
Has anyone noticed the same issue?

---

### Post by sammiev on 2014-10-26
What seems to be slow? One program or everything?
Have you installed HTOP to see what resources you have left and what is using what?

---

### Post by foxy123 on 2014-10-26
Well, it is kworker, which takes 72% of CPU, but it is just placeholder process for kernel.

---

### Post by sammiev on 2014-10-26
I never had troubles with kworker but read in other post that some had good luck booting into the BIOS and saving on the way out to find that kworker wasn't using anymore resources. Just takes a second to try.

---

### Post by foxy123 on 2014-10-26
> **sammiev said:**
> I never had troubles with kworker but read in other post that some had good luck booting into the BIOS and saving on the way out to find that kworker wasn't using anymore resources. Just takes a second to try.

Thanks a lot for the tip, it actually worked. Got rid of the kworker for now. However, it still takes ages to launch FF and TB for example. Probably there is a tip for them as well :)

---

### Post by sammiev on 2014-10-26
FF is well bloated. Try to disable your plug-ins and see if that helps. I'm having my own troubles with FF but my load times are actually very good.

---

### Post by foxy123 on 2014-11-08
Update and install anything also takes ages. I am thinking to do a clean install but wish I could avoid it...

---

### Post by sp40140 on 2014-11-10
I have recently upgraded couple of machines from 14.04 to 14.10 64 bit. I don't see any noticeable change in performance. There are few things you can try.
For FF.. You can re-set the profile, If you have been running it for a long time, and using lots of add ons (which I do) then FF gathers junk and overtime slows down (on any OS).
For other things, you can try to clean up your system. For ex. use Ubuntu Tweak's Janitor. Cleaning up system of old kernels, old logs and such will give boost to the performance as well.
Yes, there is nothing upgrade specific in my comments but you can try these and see if it helps.

---

### Post by macsociety on 2014-11-11
OK, an oddity for me today I thought I would post.

I also had very slow UI since updating from Ubuntu Gnome 14.04 to 14.10.  Workspace or window switching was slow as molasses.  Seemed the two apps for me that made window switching real slow were Evolution and Firefox.  Once I quit those things seemed normal.

I have been running my i7 based system from the Intel 4000 based on board graphics as I could not get my nVidia 750ti to work.  Therefore I had BIOS set to use the on-board video.

Today I decided to set video back to PCI1 that my nVidia is connected to but leave the HDMI display connected to my on-board video.  Took longer to boot but she did boot and guess what..... my system is running much faster UI now.  Those problem apps from before that bogged down the workspace switching.... not doing it any more.

Really strange but for me.... the UI is peppy again.

I will run like this for a day or two to see what happens.

TJ

---

### Post by sp40140 on 2014-11-12
That is understandable. Few things to note. When you upgrade, you should re-install video drivers. Intel graphic chips are joke. The latest ones in the market currently are better but still in noway can compare to ATI or Nvidia. And as Ubuntu requires lots of graphics power to run Unity, it will make huge diff in performance between Intel and ATI/Nvidia graphics.

---

### Post by macsociety on 2014-11-12
But I am still connected to the same on-board video so that confuses me.  I would think it is using the same Intel driver.  Only thing I did different is have the BIOS try to boot from PCIe slot 1st for video but I have no monitor connected to that card so it resorts back to on-board video port.  Is it maybe using some other generic VESA driver or something now and not the Intel one?  Anyway, yes I have nice fast desktop now.  Need to try again to make nVidia drivers work and switch to my stronger video card. TJ

---

