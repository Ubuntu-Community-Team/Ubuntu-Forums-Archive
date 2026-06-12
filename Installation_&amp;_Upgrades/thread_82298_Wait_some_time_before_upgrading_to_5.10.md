---
title: "Wait some time before upgrading to 5.10"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by UzbrojonyBandyta on 2005-10-26
I had 5.04 for a long time, and I was happy with it. But since there are always things that don't work, I decided to change to 5.10.
So I did the apt-get dist-upgrade.

DONT DO THAT !!!!!!
Maybe it is possible to go through all the problems that appear then, but loosing few days on looking for some bugs in dependences isn't worth it.
After one day, I resigned, formatted my disk and installed 5.10 from scratch. I advise you to do the same, if you want to upgrade.
( Oh, and dont choose expert mode during installation - otherwise it will for some strange reason make then problems with administrator mode )

But then, some strange problems started. 
First of all - why are the repositories soooo much reduced ? Why can't I find there things that were is 5.04 ? For example codecs, w32, skype, j2re1.5 and many more. And please don't tell me to add some strange lines to sources.list. They should already be there. Have I heard somwhere that this distribution is supposed to be easy, multimedial and problemlos, even for schools ? 

I really like Ubuntu. It is the best distribution available. But 5.10 still needs muuuch debugging, so as for now I advise to wait few months with upgrading, before everything will settle down.

---

### Post by Xian on 2005-10-26
The reason some multimedia libraries are not in the source list is explained in the [FAQ Guide](http://help.ubuntu.com/starterguide/C/faqguide-all.html). This is not isolated to just Ubuntu, as most of the open source distros are having to be more conscious of including software that has patent and copyright restrictions. Those that are not could get into legal trouble that would be costly no matter what the outcome. 

Other than your issue with the source list what needs to be debugged?

---

### Post by valentin.dumitran on 2005-10-26
What do you mean by "problems with Administrator mode"?
I tried expert mode and I'm having problems with Synaptic ([http://ubuntuforums.org/showthread.php?t=82282]("http://ubuntuforums.org/showthread.php?t=82282"))

---

