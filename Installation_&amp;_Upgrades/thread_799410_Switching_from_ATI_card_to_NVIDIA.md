---
title: "Switching from ATI card to NVIDIA"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Ricket on 2008-05-19
Hi all,

My laptop's NVIDIA graphics card broke, and I called up Dell. They were out of stock of the replacement card but they sent me a less-powerful ATI video card, which I promptly received and installed.

This was about a month ago. Sometime within this time period I clean-installed Ubuntu 8.04 to this computer. It is using the ATI proprietary accelerated graphics driver, and otherwise I have left it as it installed itself, but I get the feeling (correct me if I'm wrong) that settings were put into place at install time that are specific to handling this certain ATI video card.

Last week Dell informed me that they were back in stock, and after giving them my address they ordered me a card. It is due to arrive Friday. When I remove the ATI card and put in the NVIDIA card, what will happen to Ubuntu? Will it boot at all, or kick me to a text-only emergency shell state? What do I need to do to switch to this NVIDIA card, or should I just backup and reformat? What settings are specific to the ATI card, that I need to change so that my NVIDIA card works as expected?

I don't have a whole lot of data in Ubuntu because I use my other larger drive with Windows Vista on it most of the time. But I like messing with Ubuntu, and am trying to figure out how to program on it (really wish it had an equivalent to Visual Studio!). So, reformatting wouldn't be a big deal I guess, but if I can avoid it (and learn more about Ubuntu along the way), then I would like to do that.

Otherwise, I'm really excited about getting my NVIDIA card back! For those of you that keep track of graphics cards, the NVIDIA GeForce Go 7900GS was replaced by an X1400. I lost a LOT of graphics performance (the 7900GS is about 3x more powerful than the X1400) at the price of the small increase in battery life. Needless to say, I've kept on top of Dell to get me my 7900GS back ASAP, and due to my awesome warranty, they have been pretty compliant. I don't think they are completely to blame for the lack of cards (probably NVIDIA's fault, really), and the new card will be just that - new, not refurb'd as many warranty replacements are, and might even have upgraded firmware or components on it (a supervisor once mentioned that NVIDIA was fixing some problems, and used that as the reason for being out of stock).

Thanks for the help! Let me know if there is any other info you need.
-Ricky C.

---

### Post by sdennie on 2008-05-19
One thing you could do would be to use envyng and just install the nvidia driver just before you shutdown the machine to put the new graphics card in:

```

sudo apt-get install envyng-gtk
envyng-gtk

```

Select nvidia, manual install, and the 169.12 driver.  I have no way to test this but, that should install the right driver and then configure everything so that the next time you reboot, everything will work just fine.

---

