---
title: "Ubuntu 20.04 lts to ubuntu 22.04 lts problem. 22.04 works very poorly"
date: 2022-09-06
forum: Installation &amp; Upgrades
---

### Post by dgundling on 2022-09-06
I have a self made Pentium 4 computer that I use for Ubuntu. It worked fine with 20.04 but not with 22.04. I thought one of the strengths of Ubuntu was that it is backward compatible.
Is this not true with 22.04? I tried to upgrade from 20.04 to 22.04. For light gaming. Explicitly MahJong and also for Firefox as the web browser. Firefox doesn't work at all and Mahjong struggles.
Do I need to go back to 20.04? I expected 22.04 to run slowly because it is on a single core computer and a dual core machine is recommended. BTW I have never been able to get
dual boot to work with Ubuntu and either winxp or win10.

Thanks.

Dave

---

### Post by MAFoElffen on 2022-09-10
Full-blown Ubuntu Desktop? Or one on it's flavors? My hat is off to you for getting Ubuntu 22.04.1 to run at all on that! (Even though slow.)

Can you do me a favor? I am the author of the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and would love to see what hardware you have and the system settings. Besides, it would help with any recommendations on that.

I'm thinking the demand is too much. But depending on the other pieces, I have some good recommends on other flavors... And depending on what "you use" now, how to get there.

---

### Post by Impavidus on 2022-09-10
Ubuntu runs reasonably well on older hardware, but Pentium 4s (various versions) were sold from 2000 to 2008. Ubuntu won't run well on hardware from those days forever.

Using a light flavour (like Lubuntu) may help a bit as it uses less memory, leaving more for your applications. That may be enough for Mahjong. Firefox uses quite a lot of memory and this is increasing independently of the OS, simply because website builders add more and more undisableable (is that a word?) bells and whistles to their websites. Firefox also needs a decent CPU and graphics hardware. There is a point when you can no longer use old hardware to run a web browser, no matter what OS. Of course, the fact that Firefox changed to a snap package in 22.04 doesn't help here.

That computer can still do some useful things, but you cannot pretend that if it worked once, it will work forever. The world moves on for good or evil and you have to follow or be left behind.

---

### Post by tea for one on 2022-09-10
> **Impavidus said:**
> undisableable (is that a word?) bells and whistles  
I don't think that it is a word.
It's difficult to pronounce although the meaning is clearly understood to a native English speaker.

I would use something like [COLOR="#0000FF"]permanently enabled bells and whistles[/COLOR].

---

### Post by oldfred on 2022-09-10
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://opensource.com/article/20/5/linux-desktops](https://opensource.com/article/20/5/linux-desktops)
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I have used Ubuntu since 6.06. Changed to use fallback gui when Ubuntu went to Unity. Several years ago converted desktops to Kubuntu, which is more of a mid-weight flavor but full featured.
Just as a test I tried 20.04 installs on my 2006 laptop core2 duo with 1.5GB of RAM. Ubuntu would not install. Ubuntu server would install and I was able to add fallback gui. But then I tried Kubuntu and it installed and ran ok. Used to newer desktops with SSD, so laptop seemed slow, but was functional.

---

### Post by ne29914 on 2022-09-10
It'll work, but you'll need to use a different browser. Firefox is bloated out of all proportions these days. I don't buy the story about websites adding features, other browsers run well.

I'd suggest the following:

Install Lubuntu 22.04.1 LTS
The first thing you do after that is to open the Muon package manager and remove "snapd". Snap is a pest on older machines.
Install a lightweight browser of your choice. I use Brave myself.
Instructions here:
[https://brave.com/linux/#release-channel-installation](https://brave.com/linux/#release-channel-installation)
After reading/copying the instructions you can remove Firefox as well (using Muon).

Good Luck.

---

