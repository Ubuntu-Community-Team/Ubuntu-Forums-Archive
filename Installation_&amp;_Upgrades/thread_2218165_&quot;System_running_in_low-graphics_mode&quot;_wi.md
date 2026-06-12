---
title: "&quot;System running in low-graphics mode&quot; with VIA graphics card"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by phsopher on 2014-04-19
I have installed Ubuntu 13.10 on a Fujitsu-Siemens Amilo Pro V2030D but I cannot boot into it. Even before the login screen appears I get an error message which says

"The system is running in low-graphics mode

Your screen, graphics card, and input device settings
could not be detected correctly. You will need to configure these yourself."

When I click "OK" it asks me what I want to do with the options being:

1) Run in low-graphics mode for just one session (nothing happens when I click these option, the computer just hangs witht the black screen)
2) Reconfigure graphics (asks me to use either default or backed-up configuration, neither option does anything)
3) Troubleshoot error (the only thing that works here is "review the xserver log file" which I dont understand)
4) Exit to console login (works but what do I do there?)

I have searched for solutions but these apear to be advising to reinstall graphics drivers and those are for Intel/AMD. According to the site of the manufacturer Amilo Pro has the VIA VN800 intergated graphics card. How do I install that?

When I was intsalling Ubuntu everything appeared to be ok with the graphics. Cant Ubuntu just use the same setting it did during installation?

---

### Post by david98 on 2014-04-19
Have you tried using the shift key then getting into a text screen and changing the words quite splash with the word nomodeset then press f10 ? usually helps with graphics problems.

---

### Post by kansasnoob on 2014-04-19
Google results show this graphics chip:

> Graphics Integrated in VIA VN800 with UniChrome Pro 3D/2D technology up to 64 MB shared memory

I don't know if it was effected but the Openchrome driver was borked for VIA P4M800 and P4M900 in Saucy until just recently:

> xserver-xorg-video-openchrome (1:0.3.1-0ubuntu2.2) saucy; urgency=low

  *Include new patches to fix X.org 1.14 crash (LP: #1251849)
    - debian/patches/fix_incompatibility_X.org_1.14.diff :
    - Removing call to miInitializeBackingStore() no longer
       exist in xorg server 1.14
    - Commit 17973712f083100cc041d50fca30e248846e5fd2
  * Include new patches to fix crash with Chrome 9 HC chips (LP: #1165232)
    - debian/patches/fix_Chrome_9_HC_crash.diff :
    - Commit 76515c8a369346d76864e55610a6a747d9b152d8
  * Update debian/control homepage field. 

 -- Alberto Jovito <thedemon007@outlook.com>  Mon, 24 Mar 2014 00:15:34 -0430

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1165232](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1165232)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1251849](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1251849)

Anyway the updated Openchrome driver in Saucy now works for me, and also works now in Trusty, but I have the P4M800.

---

### Post by david98 on 2014-04-19
If everything is fixed mark thread as solved via top right corner under thread tool's. Just so you know support for saucy salamander end's in july so it might be a good idea to think about upgrading to Trusty Tahr sooner rather than later

---

### Post by phsopher on 2014-04-20
I don't think the problem is confined to Saucy; I got the same error running 12.10 live CD. However, one of the links suggested forsing x to use the vesa driver which seems to have worked. Thanks.

---

