---
title: "Upgrade from 9.04 to 10.04 gone bad, screen has no input after ubuntu startup screen!"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by AJack10600 on 2010-06-03
Hi All, 

I tried to upgrade my ubuntu yesterday. The download and install went ok and when it rebooted I got the purple ubuntu screen. After that the screen goes blurry and then switches off, i.e. no input signal...  my PC fan keeps running, my screen is blank, nothing happens anymore... 

After rebooting I just get the same. 

I am no computer expert and I have no clue as to how to resolve this, especially as I installed Ubuntu from the Web, via download. I don't have a CD and I also don't want to loose all my Data on my Ubuntu PC... 

I guess this is the reason some people stay with Windows and just don't want to move to Linux... it's sad really because I really liked using Ubuntu. Now I am stuck with a problem and have no idea how to resolve it... 

Any valuable help is greatly appreciated. 

If it helps, it's a Athlon Dualcore PC with an old Radeon 1900 in it. Just fine for the work I do on Ubuntu. Under 9.04 it worked just fine.

---

### Post by REDace0 on 2010-06-03
I have had a similar problem. Have you tried switching terminals with Crtl+Alt+F1 and then Crtl+Alt+F7?

---

### Post by AJack10600 on 2010-06-03
Sorry I have tried nothing yet, will do that when I get home from work. I abandoned all tries to fix it after the reboot yesterday. Will try to look into it. 

Thx for the hint...

---

### Post by psihokiller4 on 2010-06-03
just hold ```
SHIFT
```button before it's starting booting

---

### Post by AJack10600 on 2010-06-03
Tried all, that is not helping...

Shift will scan my HD and when finished boot and do the same... purple ubuntu screen and then the screen goes blank and turns off...

---

### Post by AJack10600 on 2010-06-03
Ok so I hit "ESC" and I started in Recovery mode, then in low graphix setting and I think this is where teh problem might be. 

I ran Xserver log file... 

I can't type it all but I get a check on all my Radeon Graphics and I guss my card is not there... 

I ran Startup errors... sam thing... 

I can run Ubuntu in Low graphics mode.. so  guess this is a graphics driver issue... but its blown my Wireless instllation as well ... what a great update...

---

### Post by dBuster on 2010-06-03
> **AJack10600 said:**
> Ok so I hit "ESC" and I started in Recovery mode, then in low graphix setting and I think this is where teh problem might be. 

I ran Xserver log file... 

I can't type it all but I get a check on all my Radeon Graphics and I guss my card is not there... 

I ran Startup errors... sam thing... 

I can run Ubuntu in Low graphics mode.. so  guess this is a graphics driver issue... but its blown my Wireless instllation as well ... what a great update...

First off, it is not recommended to skip a release.  Going from 9.04 to 10.04 requires a clean install.  There is no proper way to skip 9.10.  Also it is not recommended to update from 9.04 to 9.10 and then try to go to 10.04.  As there are updates to any release that all updates need to be applied and so forth prior to upgrading to the next step.

I have 9.04 and every time I get a kernel update I have to re-install my nVidia drivers and then my wifi drivers as well.  It is a fact of life.  You say this is probably why so many stay with windows?  Can you go from Windows XP to Windows 7 safely?  Without hassles?  NO.  So it is not much better.  The better thing about Ubuntu or Linux is that there is such a robust support group of other users that can help.  Try that with Microsoft...

---

