---
title: "Question about 'graphics-driver/ppa'"
date: 2016-02-02
forum: Installation &amp; Upgrades
---

### Post by echotech2 on 2016-02-02
Does [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu") automatically update to the newest NVIDIA graphics driver regardless of your NVIDIA card model or does the driver update depend on your video card model?

  Just curious.

  BTW I have added the above PPA and I noticed Software Updater recently had the latest driver (v361.18) as an update.  It updated and installed on my GTX650ti with no problems.

---

### Post by grahammechanical on 2016-02-02
> automatically update to the newest NVIDIA graphics driver regardless of your NVIDIA card model

The answer to that has to be no. It would be stupid to update a proprietary video driver without taking into account the video card model as newer proprietary drivers often drop support for older card models.

From my experience Additional Drivers will not offer a proprietary video driver that does not support the video card. My video card is a GT220. The newest driver I get offered is 340. If I install a newer driver from the Nvidia web site I know it would break my system. I tried it once and investigating the failure to build a kernel module for the driver was how I learnt that Nvidia considers my video card model obsolete.

My understanding of the purpose of that Ubuntu graphic drivers PPA is to provide users of the newest graphic cards a method of getting the latest bleeding edge video drivers through the Additional Drivers utility. 

In your case, I am glad it succeeded without a drop of "blood" being spilt. Although I would suggest that anyone using this kind of PPA should become familiar with recovery mode and know how to purge a proprietary video driver. By knowing those things I was able to get to a working desktop and start sorting things out.

Regards.

---

### Post by echotech2 on 2016-02-02
Thanks for the info.  Now that you have awoken several of my brain cells your explanation makes perfect sense.

---

