---
title: "Rc"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by perika on 2010-04-23
Hello!

I've now tried to install RC (clean install from CD) with a disappointing result. I havn't managed to install any of the betas so I had hopes that the RC would work better.
1st try - as with the betas, screen just went black after the first screen.
2nd try,  - I got to the installation setup screen. Hit F6 and turned off (put a cross in front of all alternatives), and deleted the quiet part of the script. After 3-4 minutes of installation it just stopped.
3rd try - finally it worked (almost) all way through, and I could set up keyboard, timezones etc. By the final re-boot it hanged again. After 5 minutes I did a manual re-boot and now I just get a blank screen.

To be honest, I don't know anything about Ubuntu, the machine I'm using is in no way critical, I'm just curious and want it to work. For example I have no clue what the F6 routine does...

So, I just hope that the final version will work...

/Per

---

### Post by coffeecat on 2010-04-23
> **perika said:**
> So, I just hope that the final version will  work...

Unlikely, I regret to say, taking into account your experience of the  betas and RC. It's possible that the live CD is choking over some aspect  of your hardware. Or perhaps the ACPI in your macine is buggy - I've  experienced something similar.

> **perika said:**
> 2nd try,  - I got to the installation setup  screen. Hit F6 and turned off (put a cross in front of all  alternatives), and deleted the quiet part of the script. After 3-4  minutes of installation it just stopped.

Did you get scrolling text? Was there an error message near the end,  just before everything came to a halt?

> **perika said:**
> 3rd try - finally it worked (almost) all way  through, and I could set up keyboard, timezones etc. By the final  re-boot it hanged again. After 5 minutes I did a manual re-boot and now I  just get a blank screen.

Do you mean you managed to install to the hard drive, and now it won't  reboot? It's not clear what you mean here.

> **perika said:**
>  To be honest, I don't know anything about Ubuntu

Several points:

Trying to learn Linux on a Beta is unwise. But, having said that, I  think your problem is an aspect of your hardware. I suggest you download  the ISOs for both the previous still-supported versions: Jaunty 9.04  and Karmic 9.10. If you can run and install either or both of them, so  much the better. You can find your way around Ubuntu with an earlier  version and then retry Lucid when you have more trouble-shooting  experience.

If not, and you wish to persevere with Lucid, you could  post a support  thread clarifying some of the points I've raised in  another part of the  forum - say Installation and Upgrades. But I suggest  you wait a week  until after Lucid goes final. Then, more than just the  development  testers will be getting experience of Lucid.

This subforum is not a good place for support for inexperienced users  and, besides, it will be locked and made read-only in a week's time when  Lucid goes final.

---

### Post by dino99 on 2010-04-23
when you ask for help, first give real info about your config/hardware and which release (ubuntu, xubuntu, kubuntu, ...), in anyway blahblah is useless.

As you can boot, you can use console: run these commands one by one

sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade

what you've described might be a video problem, so check system --> admin --> hardware driver to see if your driver is activated (what kind of graphic chipset)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by forcecore on 2010-04-23
Have you tried safe graphics mode?, this should work always.

---

### Post by perika on 2010-04-23
Hello,
Thanks for all comments. I'm fine waiting for the final version, but as I said, I'm curious, and I have been using the 2 previous versions of Ubuntu with basically no problems. 

I use this computer connected to a TV, used only by my kids and I run only Spotify, Firefox and XBMC on it. I'm just suprised that I have so severe problems installing on my machine.

/Per

---

### Post by perika on 2010-04-25
Hi again,
I tried to install 9.10 during the weekend, but did not manage, as I thought that I may have had a hardware error, I re-installed an old Windows XP which worked without problems. I do hope the final release will work!

/Per

---

