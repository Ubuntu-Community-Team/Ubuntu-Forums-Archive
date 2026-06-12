---
title: "When get compatible closed-source ATI driver?"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-03-06
Anyone know when we should expect ATI to release a close-source Catalyst driver that works with pre-release Jaunty?

I'm currently afflicted by a bug in the open-source driver that Jaunty employs, so the closed-source driver is my only real way to use Jaunty at this point.

---

### Post by eyelessfade on 2009-03-06
> **christian.convey said:**
> Anyone know when we should expect ATI to release a close-source Catalyst driver that works with pre-release Jaunty?

I'm currently afflicted by a bug in the open-source driver that Jaunty employs, so the closed-source driver is my only real way to use Jaunty at this point.

Send an email to amd and ask. No one here can give you anything but a guess. And mine is some time inside the beta or rc cyclus

---

### Post by questioning on 2009-03-06
catalyst 9.4 will have xserver 1.6 support.

so fglrx will prolly be ready after jaunty gets released...

---

### Post by jocko on 2009-03-06
> **questioning said:**
> catalyst 9.4 will have xserver 1.6 support.

so fglrx will prolly be ready after jaunty gets released...
...but [catalyst 9.4 will only support R600 (HD2000) and newer hardware]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1").

---

### Post by christian.convey on 2009-03-06
> **questioning said:**
> catalyst 9.4 will have xserver 1.6 support.

so fglrx will prolly be ready after jaunty gets released...

So have I got this right? ...

[LIST]
[*]ATI generally does one release per month.
[*]9.2 is current, and March's release hasn't occurred yet.  So we'll expect 9.3 this month.
[*]9.4 is toted as supporting xserver 1.6 (which Jaunty will have), implying that 9.3 won't support xserver 1.6.
[*]Therefore a proprietary ATI driver won't exist for Jaunty until sometime in April.
[/LIST]

---

### Post by sdowney717 on 2009-03-06
only r600 and above.
All X series cards NO SUPPORT!
HD series get supported.

So will the free driver ever have good 3d?
Will my x1300 work well with google earth?
or will it be slow and bad.

---

### Post by Lorenz on 2009-03-06
> **sdowney717 said:**
> only r600 and above.
All X series cards NO SUPPORT!
HD series get supported.

So will the free driver ever have good 3d?
Will my x1300 work well with google earth?
or will it be slow and bad.

I have a X1300 too, right now it is hell with Jaunty. 
I don't care much if the driver for it is open or closed source, main thing is it works! I can't really follow this whole thing now, will we get working drivers for x1300 cards now? thanks!

---

### Post by sdowney717 on 2009-03-07
there needs to be a WARNING that those with x series and older video cards will not  be able to use the fglrx driver with jaunty.

---

### Post by DougieFresh4U on 2009-03-07
I have an 
**ATI Radeon HD3200**
Is there any thing available for that onboard card?
Direct Rendering works, but just curious.

---

### Post by Lorenz on 2009-03-07
> **sdowney717 said:**
> there needs to be a WARNING that those with x series and older video cards will not  be able to use the fglrx driver with jaunty.

I'm sorry, I still don't get all this stuff with fglrx, open and closed source drivers. Users with an X series card, will they be able to achieve the same quality as with Intrepid (Compiz working, proper video output, no firefox scrolling issues)? Thanks for clarifying!

---

### Post by sdowney717 on 2009-03-07
No, I dont think so
2d will be fine, 3d will suffer
My measure is if Google Earth will work. If it does not, then the driver fails my test.

fglrx is ATI closed source driver, anything else is open source.

"radeonhd", "radeon" or "ATI" is open sourced driver. 

fglrx obviously will work better, so far in my experience this is true

---

### Post by Lorenz on 2009-03-07
Thanks for clarifying!
Now, this seems like a substantial decrease in quality from Intrepid to Jaunty to me. Aren't those ATI x series cards quite common still? What is the reason - ATI decided not to include those cards in their fglrx driver and the open source alternatives do not reach the same quality?


> **sdowney717 said:**
> No, I dont think so
2d will be fine, 3d will suffer
My measure is if Google Earth will work. If it does not, then the driver fails my test.

fglrx is ATI closed source driver, anything else is open source.

"radeonhd", "radeon" or "ATI" is open sourced driver. 

fglrx obviously will work better, so far in my experience this is true

---

### Post by sdowney717 on 2009-03-07
we with older cards are dead in the water

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

"Beginning next month with the Catalyst 9.4 release, support for the R300/400/500 generations of graphics processors will be dropped from AMD's mainline ATI driver. In a move they hope will allow them to focus their efforts on newer and upcoming graphics processors, the mainline Catalyst driver on both Linux and Windows will stop supporting cards older than the Radeon HD 2000 series. Linux customers affected will be encouraged to use their open-source driver stack (xf86-video-ati or xf86-video-radeonhd and Mesa) or stay with the Catalyst 9.3 driver."

and this is devastating here

"Will this move generate greater benefits within the open-source ATI stack? It does not appear AMD will be ramping up on their open-source efforts. In fact, just this week the RadeonHD driver took a serious blow as one of the three Novell developers that were responsible for its development was laid off. The remaining developers are also facing shorter work hours. When it comes to documentation, AMD has now released specifications that cover up through the latest RV770 GPUs, including what is needed for OpenGL acceleration. AMD also released DRM code for the R600/700 series that is needed as the first step in open-source 3D acceleration. At this time, the only benefits for the end-user is the ability to render a basic triangle, 2D EXA acceleration, and basic X-Video support. There is not yet any usable Mesa support for the R600/700 series, which will provide basic OpenGL support, while full-blown OpenGL support will likely not arrive until the Gallium3D infrastructure is in place. This though should all stabilize within the few years before AMD would likely drop R600/700 support from its Catalyst software."

---

### Post by sdowney717 on 2009-03-07
conclusion is who knows how good the open sourced driver will ever get regarding 3d performance.

For the owners of the older ATI hardware, particularly the Radeon X1000 series, your day-to-day usage may not be impacted unless you use the system for gaming or need aggressive power management. You will be fine for a few months, but after that when your kernel and X server become outdated, the Catalyst driver will not be an option. By then, however, hopefully the Gallium3D, DRI2, and kernel memory management areas will be in good standing for ATI hardware.

This legacy driver may or may not end up having X Server 1.6 support. If the legacy driver doesn't end up containing X Server 1.6 support, starting with the round of Q2'09 distribution updates (such as Ubuntu 9.04) there will be no Catalyst support for the R300/400/500 series and immediately you will be forced to either not upgrade your distribution or to use the open-source stack.

If you are using a Radeon R300/400/500 graphics card in a desktop system that is mostly used for desktop applications, you should not have much of a problem switching to the open-source ATI stack. Compiz will work just fine and the 2D performance is great and can actually beat out the proprietary ATI driver in many operations, as is illustrated by the included test results. If you are into a lot of gaming, it may just be time to upgrade. Graphics cards like the ATI Radeon HD 4670 are quite affordable these days and even the Radeon HD 4850 and Radeon HD 4870 have come down in cost.

The area we wish though would have matured in the open-source ATI stack before AMD made this decision to drop the R300/400/500 support in the Catalyst driver was to improve the GPU power management capabilities, as that will be a problem for some users. At least, however, there is work underway in improving GPU power management.

---

### Post by amano on 2009-03-07
[https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-03-03](https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-03-03)

> **Bryce Harrington** (bryce)

_Distro_

* Sponsoring 2hr: qcad(#311476), usplash-theme-ubuntu(#245437),

    * xfsprogs(#65304), xen-3.3(#216761), inkscape (#303708), xfree86-driver-synaptics(#320632) 

_Xorg Work_

    *Wrote up an X.org architecture doc at davidm's request: [https://wiki.ubuntu.com/X/Architecture](https://wiki.ubuntu.com/X/Architecture)
   ** * AMD call about -fglrx; should get new driver by March 16th**
    * Checked with mvo about fglrx/ati migration code for upgraders
    * Follow up to xkeyboard-config and -ati bugs
    * Bug fix uploads to -ati, libxcbfile, mesa, others...
    * Filed sync requests for bunch of X drivers 

That doesn't imply that it will be a x-server 1.6 compliant driver, but why should Bryce wait for a driver that will not work?

---

### Post by CarpKing on 2009-03-07
> **amano said:**
> [https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-03-03](https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-03-03)



That doesn't imply that it will be a x-server 1.6 compliant driver, but why should Bryce wait for a driver that will not work?

For Intrepid Ubuntu shipped a beta ATI driver so it would support the X-server version.  Looks like they may try to do the same again.  It won't change which cards are supported, though, so hopefully the open-source drivers will continue to improve, and get KMS etc done so they can focus on Gallium3D and speed.

---

### Post by Lorenz on 2009-03-07
This is all very confusing for a graphic card noob like me, but on the other hand I probably stand for many (older) ATI users out there who just want their card to work out-of-the box without a serious decrease in quality compared to windows. 

I don't think many people use Linux for gaming (yet?) but atm I cannot even watch a divx movie in fullscreen properly or scroll heavier websites without a terrible lag...as long as this and some compiz-style eye candy will work, it's not that bad, I'd say. 

Btw, I cannot upgrade the graphic card in my laptop, can I? I have a IBM/Lenovo T60 with an ATI x1300.

---

### Post by sdowney717 on 2009-03-07
my x1300 card is working great with intrepid and the fglrx driver.
perhaps you should be using intrepid

---

### Post by MALEADt on 2009-03-07
> **sdowney717 said:**
> No, I dont think so
2d will be fine, 3d will suffer
My measure is if Google Earth will work. If it does not, then the driver fails my test.

fglrx is ATI closed source driver, anything else is open source.

"radeonhd", "radeon" or "ATI" is open sourced driver. 

fglrx obviously will work better, so far in my experience this is true

I'd dare to say that - even with compiz enabled - 80% of the users won't notice fglrx being absent for their hardware (R300 - R500).
As you state 2D will be perfectly fine, but 3D does a good job too. Comparing fglrx against the radeon driver, I can hardly notice any difference warping multiple windows around Compiz' cube, rotating heavily with pixmaps enabled where possible. When talking about Video experience, I'm having a perfectly good time using the open source driver, as it nicely supports Xv, where fglrx is able to mess the video up completely.

Admittedly, when running some more GPU intensive applications, either native (Google Earth) or emulated (games in Wine), the open-source driver is a large part slower than the closed-source one. Alas for those people, but they'll have to hope that upcoming improvements in the graphics stack increases performance.
But is this a large part of the userbase? My experience teaches me not, a regular user won't emulate games, and hardcore games will prefer to boot in a Windows-based OS. Still, it'd be nice to have it all working out-of-the-box, but it's minor IMHO :)

And talking about power usage, a recent test on Phoronix showed that (not mentioning the lower performance), open-source drivers doesn't consome that much more energy. Luckily, AMD has talked about releasing docs on power management soon, so don't worry :)

[small]Also, you're very harsh when disqualifying a marvellous piece of software using only a single criteria...[/small]

---

### Post by sdowney717 on 2009-03-07
well I dont know about it being only a small problem.
Sometimes you want to use an app like google earth and if you cant use it, then it is a big problem.
Besides, if you know your hardware can support the app and yet your system cant run it due to a software issue, then it is a big problem with me.
This would also mean say a 3d game wont run.

I do hope the free driver can someday work well with 3d apps.
But now I am hesitant to upgrade to Jaunty and I was looking forward to that.

---

### Post by arunthopil on 2009-03-19
> **sdowney717 said:**
> only r600 and above.
All X series cards NO SUPPORT!
HD series get supported.

So will the free driver ever have good 3d?
Will my x1300 work well with google earth?
or will it be slow and bad.

Hi

 i think i cud help you...................   read my blog......... i fixed the same kind of issue with my ATI radeon chipset......... i am sure this will help you to fix with an ease effort

[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)

---

### Post by arunthopil on 2009-03-19
Hi

 i think i cud help you...................   read my blog......... i fixed the same kind of issue with my ATI radeon chipset......... i am sure this will help you to fix with an ease effort

[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)

thnx
arunthopil

---

