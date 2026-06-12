---
title: "Installation: Can't get past welcome screen"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by chockopocko on 2011-03-09
I am trying to install Ubuntu 10.10 onto a slow Windows computer, only having burned Ubuntu onto a CD two days ago.  

When I put in the disc, there is the Ubuntu loading screen, but before the GUI pops up, there is a warning message. It might be a little off; I had to scribble it because it disappeared so fast. (I tried to test Ubuntu/install it on this desktop several times, by the way.)

```
(process:218): GLiB-Warning ++getpwuid_r() failed due to unknown user error (0,0)
```

The first few times I tried to booting up Ubuntu, I was able to reach the screen where I could select a language, and whether to try or install Ubuntu. I pressed Try, but after loading for a few minutes, nothing happened. Eventually, the cursor would freeze. 

I managed to get into the advanced options (by pressing a random key when the CD was booting), and for the boot options I removed the "quiet splash --" or something like that off. I managed to test things out. I also heard some sound coming out my speakers, probably the start-up sound. Anyways, I was testing things out. Whenever I tried opening an application (i.e. Mozilla Firefox), there would be a "Starting ....." on the bottom, but it would soon disappear. The only time that didn't happen was when I loaded the System Manager. The screen froze several times. 

I restarted the computer, and tried to install. No such luck. Even with the removal of "quiet screen --". I always get to the screen with "Welcome. You may want to read the release notes." There is a language selection, and on the bottom, quit, back, and forward.

All in all, things were very slow. I also had to reboot the computer many times by pressing the power button on the box. 

Some help would be much appreciated. 


-- 
Microsoft Windows XP Home Edition
Dell Optiplex GX260
X86
Total Physical Memory 256 MB
Available Physical Memory 12.05 MB
Total Virtual Memory 2 GB
Available Virtual Memory 1.96 GB
Page File Space 625.10 MB

---
EDIT: I also checked the disc for defects, using the advanced options.

---

### Post by Hedgehog1 on 2011-03-10
> **chockopocko said:**
> 
-- 
Microsoft Windows XP Home Edition
Dell Optiplex GX260
X86
**[COLOR="Red"]Total Physical Memory 256 MB[/COLOR]**
Available Physical Memory 12.05 MB
Total Virtual Memory 2 GB
Available Virtual Memory 1.96 GB
Page File Space 625.10 MB


chockopocko,

You system does not have enough RAM memory to run Ubuntu, even in 'try' mode.

You will need to look at smaller distros (Lbunut, PuppyLinux and so on).  **_Or_** use a newer machine with at least 1 gig of RAM and enjoy Ubuntu in all its glory.

***The Hedge***

:KS

---

### Post by mörgæs on 2011-03-10
Agree with Hedgehog. 

The link to Lubuntu is [www.lubuntu.net](www.lubuntu.net). Don't let the ugly web site scare you away; it is a great system.


The Glib-error message you see does not mean anything. The thorough explanation is here
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)
but the short story is: Just ignore it.

---

