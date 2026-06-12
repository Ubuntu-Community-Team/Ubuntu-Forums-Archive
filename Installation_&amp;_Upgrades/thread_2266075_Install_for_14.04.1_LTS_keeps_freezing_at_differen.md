---
title: "Install for 14.04.1 LTS keeps freezing at different points"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by john367 on 2015-02-19
I am brand new to Linux and Ubuntu. Sorry I am unable to figure this out but I am tired of windows and want to give it a try. 

I have a second hard drive I installed into my computer and set up the partitions for a Ubuntu install. I downloaded Ubuntu 14.04.1 LTS from Ubuntu.com. 

I set up a boot from USB with the ISO and then select it as the computer starts. At first I was having visual troubles so I found recommendation to use nomodset. I did so and then selected try Ubuntu to make sure I can see it. Sure enough opened up and worked fine. 

I rebooted my computer and was ready for the install. This is when everything seemed to start messing up. The install continues to freeze at different points. Sometimes freezes on first screen before I select a language, sometimes on the language selection, sometimes on the install set up options. 

On the install setup I select the other option because I don't want to replace or install next to windows. I want to put it on my second HDD. I have gotten the the ext4 and swap set up. Twice I've gotten past this. Once it froze when trying to select my time zone. Earlier today I finally made it to install and it froze at installing language packets, didn't let me skip if I wanted. I waited about 6 hours because many said this step takes a while. 

Eventually rebooted my computer and now it keeps freezing on the first screens again.

Please help, I have no idea what to try next. I continue to try and find info online but everything I come across is slightly different and even when I try their recommendations I get no success. 

I am sorry if this has been asked before, I couldn't find it and I'm about to return to windows but hoping someone could help. 

Thanks for your time.

---

### Post by ubfan1 on 2015-02-20
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

