---
title: "Updates: Latest Release to upcoming LTS version. Current LTS to future LTS version."
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by kleenex on 2012-03-22
Hello, does update from latest standard **11.10** version to the upcoming **12.04 LTS** version runs normally? I do not know exactly what I mean by writing 'normally'. This update will be available e.g. via the Update Manager? I mean generally the updates from the normal/standard version to version of the long support - LTS. And what about updating from current **10.04 LTS**   version to the next, future **12.04 LTS**  version? Is it possible? Whether there will be no problems? At last, this is an update of two numbers!

Best regards to all!

---

### Post by wojox on 2012-03-22
You can update both 11.10 to 12.04 and 10.04 to 12.04.

Just back up as always before.

---

### Post by snowpine on 2012-03-22
The more people test the upgrade, the better it will work:

[https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

This is your opportunity to get involved. :)

---

### Post by Bucky Ball on 2012-03-22
Just like to make a point, here: changing from one release to a newer one is not an ***update***, it's a release ***upgrade***. ;)

PS: Ubuntu has been upgradable from LTS to LTS release for awhile now. The upgrade from the Update Manager is not yet available though you could do it via a terminal. If you need a stable machine, I wouldn't try it for now. Wait.

By all means test and help, but install 12.04 LTS on another box or partition so you have a stable release to fall back on if you need one. Maybe install 10.04 LTS on another partition/box, then try the upgrade to 12.04 LTS and report the results, as Snowpine suggests. ;)

---

### Post by Pand5461 on 2012-03-22
Hi!

I'm fairly sure that upgrade from 10.04 to 12.04 won't run smoothly. In principle, this is possible but most likely you will end up with a system not bootable into a graphical DE.

Update from 11.10 to 12.04 will probably run "normally" (more or less) but, well, it depends.
In general, the more packages you have installed, the more likely will something break. Also, programs from third-party repositories may not upgrade and cause conflicts.

You can install 10.04 or 11.10 in Virtualbox, then install the packages you use and try to update to the current beta. If everything runs OK, you're a lucky one. If not, you should think about fresh install.

Actually, restoring your environment after a fresh install is not a big work. Just make sure you've backed up your home folder with all the hidden subfolders before the installation. The best way imho is to have home folder on a separate partition and choose to use it as /home without formatting at the installation. Hidden files and folders in your /home/user mostly contain application settings, so when you re-install the system and restore your home folder, you can just install your favourite apps and use them with the same settings you had in the old system.

---

### Post by kleenex on 2012-03-22
**Bucky Ball; **Your proposed on *install 10.04 LTS on another partition/box, then try the upgrade to 12.04 LTS and report the results* is quite interesting, because I have one free computer, which will be designed to test various things like grsecurity and maybe SELinux etc, but If I find some more free time, I think, that I will test this solution.
[B]
Pand5461[/B]; Your several possible solutions are very interesting, but from some time I do not like VirtualBox, please don't ask why. ;- ) You mentioned about back up. I'm also think, that the best way is to have home folder on separate partition. Such solution simplifies many things.
[B]
snowpine[/B]; Your proposal about The Ubuntu Testing Team is also very interesting. I need to think carefully about this.
[B]
wojox[/B]; No need to add anything, really ;- )

I think, thread seems to be solved. Thank you for your answers and suggestions. By the way; a couple of days ago, - unfortunately I do not remember where and did not have the source -  I have read, that upgrade from current 10.04 LTS version to the next Long Term Support version should be smooth and easy. If I remember correctly, Mr Mark Shuttleworth assured of this.

Best regards!

---

### Post by Bucky Ball on 2012-03-22
> **Pand5461 said:**
> Hi!

I'm fairly sure that upgrade from 10.04 to 12.04 won't run smoothly. In principle, this is possible but most likely you will end up with a system not bootable into a graphical DE.

Not sure where you got this information but upgrading LTS to LTS has been an option for quite a while. This option will be available when 12.04 LTS is released. I have four machines upgraded from 8.04 LTS to 10.04 LTS with no issues whatever. 

There is absolutely no reason to upgrade to 11.10 first. 

PS: If problem solved please mark it that way from 'Thread Tools' at top right. Cheers, enjoy and good luck. ;) ;)

---

### Post by Dutchman54 on 2012-03-22
Well 11.10 has much to desire, I installed it and instantly felt like a fish out of water after running previous releases 6.? 7.04 8.? & 10.04 Which I really liked. I hope that 12 will present user configure-ability to the stupid unity dash! I really expect this post to be deleted as it seems any off color comments about unity have been closed to further comment.

---

### Post by Bucky Ball on 2012-03-22
If you don't like Unity then you can immediately install xfce via Software Centre. Install 'xfce4', log-out, choose 'xfce session' from the Sessions pop-up menu, log-in. See what you think.

You can get back to Unity (or any other DE you have installed) by repeating the process and choosing 'Unity' session, or whatever it may be called). ;)

Yes, people's dislike of Unity is a recurring topic but many have found alternatives. I generally go for a Ubuntu install with xfce DE (or sometimes xubuntu-desktop added). This time I'll be going straight Xubuntu minimal install for 12.04 LTS, but my machines are hybrid beasts anyhow with added bits (pcmanfm for file manager, Edubuntu artwork, UStudio apps on one, minmal install on a partition with my favourite bits as some examples).

---

### Post by kleenex on 2012-03-23
I hope that the update from normal version to the LTS will runs smoothly without major problems. Same thing with update from LTS to LTS.

Best regards!

---

