---
title: "Installation Issue"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by MiDo0o0o on 2010-07-27
Hey all I'm new here..

I installed ubuntu 10.04 before and everything was ok till I get my new graphic card MSI ATI R4670 then everything stops..

I tried to install it again but the installation process after loading for few minutes gave me this message

```
(initramfs) unable to find a medium containing a live
```I tried again and again but nothing changed, by fault I clicked Del key then the loading screen disappeared and stdin error 0 repeated forever and says that the installation cant mount /dev/sr0 from /cdrom or something like that

any ideas.. Thanks in advance.

---

### Post by tommcd on 2010-07-27
> **MiDo0o0o said:**
> 
I installed ubuntu 10.04 before and everything was ok till I get my new graphic card MSI ATI R4670 then everything stops..
So before buying the ati card, I assume you were running the integrated graphics on the motherboard? Is that correct?
What graphics card (or integrated graphics) were you running prior to installing the ati card?
As a test, try removing the ati card, and go back to whatever graphics you were previously using. Then see if you can boot the Ubuntu live CD and install Ubuntu.
If the installation fails with whatever graphics you were previously using, then the problem obviously lies elsewhere.
When you boot the Ubuntu live CD, first choose the option "*check disc for defects*" and let that run. If it reports no errors, then the CD is ok. It is always helpful to rule out a bad CD as the source of the problem. Don't just assume that the CD is good.
If you are able get through the installation with the old graphics, you should then be able to shut down the computer, reinstall the new ati card, and then do your first boot into your new Ubuntu 10.04. You can then decide whether you want to run the open source ati driver provided by the linux kernel, or use the proprietary catalyst driver from ati.

FYI: For what it's worth, at this present time nvidia is still a better choice for a graphics card in linux than ati. This may likely change in the future though, as AMD (which now owns ATI) has decided to make open up the source code for the ati graphics cards to further the development of completely free (as in freedom) ati graphics drivers.

And welcome to the Ubuntu forums!

---

