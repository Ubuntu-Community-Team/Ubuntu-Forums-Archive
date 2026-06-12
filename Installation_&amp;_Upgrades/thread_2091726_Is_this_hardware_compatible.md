---
title: "Is this hardware compatible?"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by jfinner1 on 2012-12-05
It's been a while since I was here (about 2 years) so forgive me if I'm a bit noobish. My old laptop ran Ubuntu for years until it finally died (power supply, cooling fan, hard drive, fail...) but I couldn't install Ubuntu on my desktop for some reason that I don't remember 2 years later. Anyways, I just got a new/used desktop, and I was wondering if I could install Ubuntu on it without too many problems. Looking at either 12.04 or 12.10, whichever people think would work better for me. The new computer is a Compaq Presario SR5605F. All of the specs are [here]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01530046").

My biggest concerns are that it's using an nVidia GeForce 6150SE integrated graphics card, and I remember having issues with nVidia and Ubuntu in the past, and it doesn't come with wireless, so I'll be installing a Linksys Wireless-G PCI adapter, which I also had problems with in the past. I'm really hoping that these quirks have been worked through in the time I've been "gone", because I really really miss Ubuntu. 

If you see anything else that might be a problem, please let me know. It originally came with Windows Vista, but the previous owner upgraded to Windows 7. I'm also debating if I do install Ubuntu, if I should delete the Vista recovery partition or not...

Also, slightly off topic, but I read somewhere that in the new Ubuntu, you can install Microsoft Office? Is that true? Because that would be awesome.

---

### Post by trogdor1138 on 2012-12-05
Nearly anything is compatible... the question is how compatible do you want it? ;)

A lot of your answers depend on how willing you are to go with closed-source, proprietary drivers. Some people care, some don't. If you don't have an opinion either way, I've found that Nvidia provides excellent drivers for their cards. Otherwise, I believe the 'nouveau' driver handles most of their GPU's. I would check sites for both to see what's supported.

As for Office, it's not and never will be possible to directly install it. However, you can install many Windows applications through WINE. WINE provides many of the functions Windows software expects, allowing it to run on a Linux system. Alternatively, you might have heard about Libre or Open Office. These suites are open-source, free, and provide pretty good support for MS Office formats, but they're not perfect and your success with them for your uses may vary.

I think your best bet is to simply download the 12.10 image and flash it to a USB drive. You can then boot the live image to get a good idea of how difficult it will be to get things running to your standard of usability.

---

### Post by mastablasta on 2012-12-06
you can do the same with version 12.04 which is Long term support (supported for 5 years). the 12.10 got mixed reviews. for some it worked well for others it didn't at all. run it live as suggested to see if hardware works. 
 
some MS office versions can run well via wine. there is also crossover (but that one needs to be payed for). you can check compatibility of your version here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
you would usually need rating gold or higher.

---

