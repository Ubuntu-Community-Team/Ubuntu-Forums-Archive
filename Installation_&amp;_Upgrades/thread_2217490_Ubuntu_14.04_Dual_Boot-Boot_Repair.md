---
title: "Ubuntu 14.04 Dual Boot-Boot Repair"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by davide-maraschio93 on 2014-04-17
Hi all, i want to install Ubuntu 14.04 on my Pc but i have Windows 8.1 already installed. When i have installed Ubuntu 12.04 and Ubuntu 13.10 i have used Boot-Repair; but there aren't any Boot-Repair's package for 14.04(Trusty) yet. So what can i do to use Windows 8.1 and Trusty in dual boot:confused:
I have already tried to install Boot-Repair's version for 13.10 on Trusty but doesn't work. Help me PLEASEEEEE:icon_frown:

---

### Post by oldfred on 2014-04-17
Many of the fixes that Boot-Repair did are not required with 14.04. 

The main one that is a lot easier with Boot-Repair is for those systems where vendor modified UEFI to only boot Windows. And that is the 'buggy' UEFI which I suggest saying no to until proven that it is not UEFI that is hard coded to boot only Windows. Most just need other boot parameter type settings or changes to UEFI settings.

I was able to install Boot-Repair from saucy.
       Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335).
Change trusty to saucy like this but without quote which was only way I could get it to show entire entry:
['http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages]("http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages")'
['http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages]("http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages")'

---

### Post by davide-maraschio93 on 2014-04-18
With the official release of Ubunu 14.04, dual-boot work right without the use of boot-repair :D However here [https://bugs.launchpad.net/boot-repair/+bug/1267702?comments=all](https://bugs.launchpad.net/boot-repair/+bug/1267702?comments=all) there'is a workaround for this problem.

---

