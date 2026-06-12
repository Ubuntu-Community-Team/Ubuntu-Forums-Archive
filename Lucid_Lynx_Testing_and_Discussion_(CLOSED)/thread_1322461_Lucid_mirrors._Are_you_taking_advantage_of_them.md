---
title: "Lucid mirrors. Are you taking advantage of them?"
date: 2009-11-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-11-11
Main and US Main aren't always the best. Pick a mirror that's close to you geographically and is tied to a university to guarantee the fastest speeds. **Also, take note that the "pick the best server" function is complete crap.** I live in the US and it gave me German server.

Anyway, here's my sources.list:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha i386 (20090928)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-backports main restricted universe multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ karmic-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/rvm/testing/ubuntu karmic main
deb-src http://ppa.launchpad.net/rvm/testing/ubuntu karmic main
deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main
deb-src http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

###### Third-Party Repos ######

## Medibuntu
deb http://packages.medibuntu.org/ karmic free non-free

## Upstream Opera
deb http://deb.opera.com/opera/ testing non-free

## Wine
deb http://wine.budgetdedicated.com/apt/ karmic main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu jaunty main

## Dropbox
deb http://linux.getdropbox.com/ubuntu karmic main

## Boxee
# deb http://apt.boxee.tv jaunty main

## VirtualBox
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

## Back in Time
deb http://le-web.org/repository stable main

## UbuntuOne
deb http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main

## Google
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://dl.google.com/linux/deb/ testing non-free main

## Miro
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/

## Mendeley
deb http://www.mendeley.com/repositories/xUbuntu_9.04 /

###### PPA ######

## X updates (stable) AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main

## Karmic testing 40618B66 
# deb http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
# deb-src http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main

## Experimental boot
deb http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu karmic main

## Karmic kernel (Andy Whitcroft) CB0B05C0 
# deb http://ppa.launchpad.net/apw/jaunty-kernel/ubuntu karmic main restricted
# deb-src http://ppa.launchpad.net/apw/jaunty-kernel/ubuntu karmic main
# deb http://ppa.launchpad.net/apw/ppa/ubuntu karmic main restricted
# deb-src http://ppa.launchpad.net/apw/ppa/ubuntu karmic main

## VDPAU-team
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main

## Transitional
# deb http://ppa.launchpad.net/apw/staging/ubuntu karmic main
# deb-src http://ppa.launchpad.net/apw/staging/ubuntu karmic main

## ZgegBlog's Themes 881574DE 
deb http://debian.vogelweith.com/ intrepid zgegthemes
# deb-src http://debian.vogelweith.com/ intrepid zgegthemes

## Bisigi themes
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/bisigi/dev/ubuntu karmic main
# deb-src http://ppa.launchpad.net/bisigi/dev/ubuntu karmic main

## Chromium 4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

## Mozilla Daily
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main

# wxWidgets/wxPython repository at apt.wxwidgets.org
deb http://apt.wxwidgets.org/ jaunty-wx main
# deb-src http://apt.wxwidgets.org/ jaunty-wx main

## UNetBootin
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu karmic main

## EarCandy
# deb http://ppa.launchpad.net/earcandy-devel/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/earcandy-devel/ppa/ubuntu jaunty main

## Liferea
# deb http://ppa.launchpad.net/liferea/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/liferea/ppa/ubuntu karmic main

## Webkit 2D9A3C5B 
# deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main

## bcmwl
# deb http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu karmic main
# deb-src http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu karmic main
# deb http://ppa.launchpad.net/timg-tpi/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/timg-tpi/ppa/ubuntu karmic main

## gtg
deb http://ppa.launchpad.net/gtg/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/gtg/ppa/ubuntu jaunty main

## MSN-Pecan B85366AC
deb http://ppa.launchpad.net/msn-pecan/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/msn-pecan/ppa/ubuntu karmic main

## Anjal for Evo
# deb http://ppa.launchpad.net/paulliu/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/paulliu/ppa/ubuntu karmic main

## Banshee unstable
# deb http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu karmic main

## Network Manager
# deb http://ppa.launchpad.net/network-manager/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/network-manager/ppa/ubuntu karmic main

## TortoiseHG
deb http://ppa.launchpad.net/tortoisehg-ppa/releases/ubuntu karmic main
# deb-src http://ppa.launchpad.net/tortoisehg-ppa/releases/ubuntu karmic main

## Listen
# deb http://ppa.launchpad.net/listen-devel/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/listen-devel/ppa/ubuntu karmic main

## Exaile
# deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main

## Empathy
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

## LCD text improvements?
deb http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu karmic main

## Pidgin dev
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/iaz/pidgin/ubuntu karmic main
# deb-src http://ppa.launchpad.net/iaz/pidgin/ubuntu karmic main

## Moblin
# deb http://ppa.launchpad.net/moblin/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/moblin/ppa/ubuntu karmic main

## Bazaar
deb http://ppa.launchpad.net/bzr/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/bzr/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/bzr-beta-ppa/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/bzr-beta-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu karmic main

## uzbl browser
# deb http://ppa.launchpad.net/pplr/uzbl/ubuntu karmic main
# deb-src http://ppa.launchpad.net/pplr/uzbl/ubuntu karmic main

## Gnome-Shell
deb http://ppa.launchpad.net/ricotz/testing/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu karmic main

## E17
deb http://packages.enlightenment.org/ubuntu karmic main extras

## Ubuntu tweak
deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/gnote/ppa/ubuntu karmic main #Gnote
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main #GNOME Do
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main #Ubuntu Mozilla Security Team
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main #Shutter
deb http://www.01.246.ne.jp/~hatch/original/xnp2/ ./
deb-src http://www.01.246.ne.jp/~hatch/original/xnp2/ ./
```

---

### Post by jbernardo on 2009-11-11
That is good for i386/x64, but what about LPIA? For that, it seems there are no mirrors - only ports.ubuntu.com.

---

### Post by qamelian on 2009-11-11
> **Starks said:**
> **Also, take note that the "pick the best server" function is complete crap.** I live in the US and it gave me German server.

Not in my experience. It has always worked well for me. The servers that are geographically closest are not always the servers that will work best for you.

---

### Post by jerrylamos on 2009-11-11
I get good response from Northeastern University in Boston.  Since I'm in southern New Hampshire that's physically relatively close.  Electrically might be different I have no way of knowing.  They seem to be right up to date on the development stuff,  Anyway it's:

mirrors.ccs.new.edu

as found on System > Administration > Software Sources > Download from ....

Jerry

---

### Post by slakkie on 2009-11-11
> **Starks said:**
> **Also, take note that the "pick the best server" function is complete crap.** I live in the US and it gave me German server.


You should have a look in the terminal after you hit that button. You will see how the app determines the best mirror. It does work, if the US servers are busy and a German server has better roundtrips and what-not, it will select that one. It works, that you don't like using German mirrors is besides the point.

Because something doesn't match expectation, doesn't mean it is crap.

---

### Post by Kevbert on 2009-11-11
Using UK server (I'm based just outside London). Best server suggests that I use a Maltese server:confused:

---

### Post by Eestlane on 2009-11-11
On development versions (alphas, betas etc) I use the main server. Then I can have all the updates without delay. I guess there are less development version testers than stable users, so there probably isn´t too much overhaul for the main server in that case.

On stable I use Estonian or whatever is best.

---

### Post by tekstr1der on 2009-11-11
> **jerrylamos said:**
> I get good response from Northeastern University in Boston.  Since I'm in southern New Hampshire that's physically relatively close.  Electrically might be different I have no way of knowing.  They seem to be right up to date on the development stuff,  Anyway it's:

mirrors.ccs.new.edu

as found on System > Administration > Software Sources > Download from ....

Jerry

Southern NH here too. I think you mean:

mirrors.ccs.ne**[COLOR="Red"]u[/COLOR]**.edu

I use the MIT Media Lab (ubuntu.media.mit.edu). Usually get ~2000 kB/s. It's only 15 hops with zero packet loss, so I consider it the most solid I've tried. Oh, and of course you have a way of knowing "electrically"! Here's the pathping to your mirror from Hudson, NH:

```
C:\Windows\system32>pathping -q 5 mirrors.ccs.neu.edu

Tracing route to krypton.ccs.neu.edu [129.10.116.76]
over a maximum of 30 hops:
  0  SysAdmin.xxx.lan [192.168.1.192]
  1  gateway.xxx.com [63.119.xxx.xxx]
  2  Loopback0.GW3.BOS4.ALTER.NET [137.39.3.77]
  3  0.so-0-1-1.XL4.BOS4.ALTER.NET [152.63.22.174]
  4  0.so-7-0-0.XL4.NYC4.ALTER.NET [152.63.17.97]
  5  0.xe-8-1-0.BR2.NYC4.ALTER.NET [152.63.3.134]
  6  204.255.173.54
  7  vlan51.ebr1.NewYork2.Level3.net [4.69.138.222]
  8  ae-4-4.ebr1.NewYork1.Level3.net [4.69.141.17]
  9  ae-1-8.bar2.Boston1.Level3.net [4.69.140.97]
 10  ae-0-11.bar1.Boston1.Level3.net [4.69.140.89]
 11  ae-7-7.car1.Boston1.Level3.net [4.69.132.241]
 12  NORTHEASTER.car1.Boston1.Level3.net [63.211.169.158]
 13  129.10.6.117
 14  icore-sl1-p2p-sliCore2.cne.neu.edu [129.10.6.11]
 15  10.2.24.17
 16  129.10.24.101
 17  krypton.ccs.neu.edu [129.10.116.76]

Computing statistics for 21 seconds...
            Source to Here   This Node/Link
Hop  RTT    Lost/Sent = Pct  Lost/Sent = Pct  Address
  0                                           SysAdmin.xxx.lan [192.168.1.192]
                                0/   5 =  0%   |
  1    0ms     0/   5 =  0%     0/   5 =  0%  gateway.xxx.com [63.119.xxx.xxx]
                                0/   5 =  0%   |
  2    6ms     0/   5 =  0%     0/   5 =  0%  Loopback0.GW3.BOS4.ALTER.NET [137.39.3.77]
                                0/   5 =  0%   |
  3    5ms     0/   5 =  0%     0/   5 =  0%  0.so-0-1-1.XL4.BOS4.ALTER.NET [152.63.22.174]
                                0/   5 =  0%   |
  4   16ms     0/   5 =  0%     0/   5 =  0%  0.so-7-0-0.XL4.NYC4.ALTER.NET [152.63.17.97]
                                0/   5 =  0%   |
  5   15ms     0/   5 =  0%     0/   5 =  0%  0.xe-8-1-0.BR2.NYC4.ALTER.NET [152.63.3.134]
                                0/   5 =  0%   |
  6   18ms     0/   5 =  0%     0/   5 =  0%  204.255.173.54
                                0/   5 =  0%   |
  7   15ms     0/   5 =  0%     0/   5 =  0%  vlan51.ebr1.NewYork2.Level3.net [4.69.138.222]
                                0/   5 =  0%   |
  8   16ms     0/   5 =  0%     0/   5 =  0%  ae-4-4.ebr1.NewYork1.Level3.net [4.69.141.17]
                                0/   5 =  0%   |
  9   24ms     0/   5 =  0%     0/   5 =  0%  ae-1-8.bar2.Boston1.Level3.net [4.69.140.97]
                                0/   5 =  0%   |
 10   19ms     0/   5 =  0%     0/   5 =  0%  ae-0-11.bar1.Boston1.Level3.net [4.69.140.89]
                                0/   5 =  0%   |
 11   40ms     0/   5 =  0%     0/   5 =  0%  ae-7-7.car1.Boston1.Level3.net [4.69.132.241]
                                0/   5 =  0%   |
 12   19ms     0/   5 =  0%     0/   5 =  0%  NORTHEASTER.car1.Boston1.Level3.net [63.211.169.158]
                                0/   5 =  0%   |
 13  ---       5/   5 =100%     5/   5 =100%  129.10.6.117
                                0/   5 =  0%   |
 14  ---       5/   5 =100%     5/   5 =100%  icore-sl1-p2p-sliCore2.cne.neu.edu [129.10.6.11]
                                0/   5 =  0%   |
 15  ---       5/   5 =100%     5/   5 =100%  10.2.24.17
                                0/   5 =  0%   |
 16  ---       5/   5 =100%     5/   5 =100%  129.10.24.101
                                0/   5 =  0%   |
 17   18ms     0/   5 =  0%     0/   5 =  0%  krypton.ccs.neu.edu [129.10.116.76]

Trace complete.
```

YMMV of course. I don't know if there is a equivalent Linux console command other than tracert.

---

### Post by slakkie on 2009-11-11
> **tekstr1der said:**
> [/CODE]

YMMV of course. I don't know if there is a equivalent Linux console command other than tracert.

mtr perhaps?

---

### Post by tekstr1der on 2009-11-11
> **slakkie said:**
> mtr perhaps?

Definitely, thanks! Guess I never looked hard enough. As with most things Linux, this is an even better tool.

---

### Post by ronacc on 2009-11-11
ping and traceroute are both available via terminal and through system>administration>network tools .

---

### Post by tekstr1der on 2009-11-11
> **ronacc said:**
> ping and traceroute are both available via terminal and through system>administration>network tools .

Very aware of that, but thanks. Both mtr and pathping combine and extend the capabilities of those tools.

---

### Post by RussellGee on 2009-11-11
When using a development release its a good idea to stick to the main server, the mirrors can be weeks behind the main server sometimes meaning your always lagging behind development.

---

### Post by LKjell on 2009-11-11
> **RussellGee said:**
> When using a development release its a good idea to stick to the main server, the mirrors can be weeks behind the main server sometimes meaning your always lagging behind development.
Isn't that good? If something breaks you may know that before even experience it.

---

### Post by RussellGee on 2009-11-12
> **LKjell said:**
> Isn't that good? If something breaks you may know that before even experience it.

Not really, the only way broken things can be fixed is when you find them.

I will give you an example.

You find a bug in packages X
You try to report bug on packages X, however the packages has already been upgraded to a newer version in the main archive
Bug triagers then need you to upgrade package X to the latest to check if the bug is still present
If the bug is still present, time spent fixing that bug has been lost because your a few weeks behind developement (plus triage time)
If its been fixed, you have wasted the triagers time and your own.

---

