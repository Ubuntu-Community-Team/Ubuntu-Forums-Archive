---
title: "Installation on Dell G3 (GTX 1060, Intel 9462 AC issues)"
date: 2018-06-18
forum: Installation &amp; Upgrades
---

### Post by hasetr on 2018-06-18
Hello,

Today i tried to install ubuntu on my new dell machine.

Unfortunately i was not able to install it correctly. 

At first i had trouble with getting to boot, but setting "nomodeset" helped me to boot into it. What should i follow to make the install permanently working (issue with GTX 1060?)

At second i have problems with my wireless card. The strange thing is that bluetooth is working, but wifi says no adapter installed.. According to this: [http://nucblog.net/2018/04/gemini-lake-nuc-review-nuc7cjyh-linux-htpc-conclusions/](http://nucblog.net/2018/04/gemini-lake-nuc-review-nuc7cjyh-linux-htpc-conclusions/) the card should be working with 4.15 kernel. Unfortunately the wifi is not working as said above.

Could you please help me solve this issue?

Kind Regards,

---

### Post by oldfred on 2018-06-18
With nVidia you need nomodeset to boot installer & first boot or until you install the proprietary driver from Ubuntu repository. since newer nVidia, you may want ppa to get very newest nVidia driver. If you install wrong driver, or update to a different driver, you must purge first or else you get conflicts. New driver does not uninstall old one.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

       Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html) 
    

Best to post separate thread in Network & wireless sub-forum and per sticky thread at top, run the suggested script to fully document wireless details.
Often you need to use wired connection to get correct wireless driver. Almost all systems will work with wired connection, but many wireless systems, so live installer may not have all of them.

---

