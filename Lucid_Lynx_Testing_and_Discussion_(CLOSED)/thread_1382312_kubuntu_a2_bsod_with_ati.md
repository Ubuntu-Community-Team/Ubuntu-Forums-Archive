---
title: "kubuntu a2 bsod with ati?"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by narttu on 2010-01-15
yup, i'm getting a black screen of doom unless i use safe graphics, but that doesn't even boot x.

---

### Post by narttu on 2010-01-15
noone else is getting a bsod?

---

### Post by VMC on 2010-01-15
> **narttu said:**
> yup, i'm getting a black screen of doom unless i use safe graphics, but that doesn't even boot x.

I was just getting a "blue weave" the one with the new login. Now login is automatic, but I'm faced with only that "blue weave". Actually X is working and so is plasma, just nothing else. Alt+F2, works, so I was able to call up some apps I remembered.

Then I went the desprete route and deleted my "**.kde**" folder. On re-boot everything was back to normal. I had to then add in my icons and such.

---

### Post by narttu on 2010-01-15
> **VMC said:**
> I was just getting a "blue weave" the one with the new login. Now login is automatic, but I'm faced with only that "blue weave". Actually X is working and so is plasma, just nothing else. Alt+F2, works, so I was able to call up some apps I remembered.

Then I went the desprete route and deleted my "**.kde**" folder. On re-boot everything was back to normal. I had to then add in my icons and such.

k but exactly the same prob :P

it wont boot the live usb stick i made. it works on my desktop that has nvidia, but on my lappy with ati it just wont boot. it gets to where the splash screen should be and freezes and i cant even ctrl-alt-f1, and my usb stick stops flashing, which is what it always does when its loading stuff. if i make it use safe mode graphics it loads to the text console but nada, no x.

---

### Post by Kevbert on 2010-01-16
This eventually occurred for me on Alpha1 after the segfaults episode. I found a clean install of Alpha2 cured it (but I still get knetworkmanager segfaulting). This is with nVidia graphics.

---

### Post by VMC on 2010-01-16
> **Kevbert said:**
> This eventually occurred for me on Alpha1 after the segfaults episode. I found a clean install of Alpha2 cured it (but I still get knetworkmanager segfaulting). This is with nVidia graphics.
Its so weird that just you and I have this issue. Or it seems. I know that can't be the case. I'm thinking of reporting a bug at kde.org and see if that gets any response.

I did add to an already closed bug report at kde.org and they told me they would re-open the bug if indeed I had the same seg faults.

---

### Post by Kevbert on 2010-01-16
> **VMC said:**
> Its so weird that just you and I have this issue. Or it seems. I know that can't be the case. I'm thinking of reporting a bug at kde.org and see if that gets any response.

I did add to an already closed bug report at kde.org and they told me they would re-open the bug if indeed I had the same seg faults.

Let me know which one and I'll add a comment to it...

---

### Post by narttu on 2010-01-17
so im the only 1 experiencing not being able to boot live stuff?

---

### Post by Kevbert on 2010-01-17
> **narttu said:**
> so im the only 1 experiencing not being able to boot live stuff?

Have you been able to boot other versions of Ubuntu/Kubuntu on this laptop?  What is the model of your ATI graphics card ?  Can you use a live-CD on the laptop ?

---

### Post by narttu on 2010-01-17
> **Kevbert said:**
> Have you been able to boot other versions of Ubuntu/Kubuntu on this laptop?  What is the model of your ATI graphics card ?  Can you use a live-CD on the laptop ?

ya, old versions are sweet, no probs. lappy has an x1200, and i was using a live usb stick, i waste too many cds anyway :P

---

### Post by Lollerke on 2010-01-17
Same here with Ubuntu A2 (and ATI Radeon X200). First time after the white Ubuntu logo I got black screen with no backlight,then after the second try I saw the desktop for 5 seconds then I got black screen again with backlight.
 
Did you try to boot with nomodeset? [http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29](http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29)

---

### Post by narttu on 2010-01-18
> **Lollerke said:**
> Same here with Ubuntu A2 (and ATI Radeon X200). First time after the white Ubuntu logo I got black screen with no backlight,then after the second try I saw the desktop for 5 seconds then I got black screen again with backlight.
 
Did you try to boot with nomodeset? [http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29](http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29)

thanks :D

but now i have this weird corruption problem

[img]http://i47.tinypic.com/5mya92.png[/img]

---

### Post by narttu on 2010-01-18
bump

---

### Post by Ubuntiac on 2010-01-18
I'm having this exact same problem.

Kubuntu Lucid worked fine for me on Alpha 1. It still works fine on my desktop which has an AMD quad core and ATI Radeon 4750. On my laptop (Dell latitude XT) with an Intel Core 2 Duo cpu and ATI Radeon Xpress 1250 I get the following:

[LIST]
[*]Boots to grub fine
[*]Black screenswhen it should bring up xsplash / plymouth
[*]ctrl+alt+f1 / alt+sysrq+resinub Do nothing
[*]Alternate cd seems to install fine, but on reboot does the same as the livecd
[/LIST]

It's a bit hard to troubleshoot when you can't even get the recovery mode or livecd to boot! When I get a chance I'll make a Karmic livecd and see if I can get any clues from the logs.

Has anyone filed a bug on this yet?

As far as I can see, the commonalities seem to be:
a. Kubuntu
b. 64 bit.
c. An older ATI card (ie Radeon Xpress 1200-1250)

For anyone else getting this bug, does your system match all of the above? Can you boot with an older livecd and post your logs in /var/log like Xorg.0.log or kern.log?

---

### Post by Lollerke on 2010-01-18
I filled a bug already. [https://bugs.launchpad.net/ubuntu/+bug/509273](https://bugs.launchpad.net/ubuntu/+bug/509273)
Can you get to the desktop with nomodeset?

---

### Post by Ubuntiac on 2010-01-18
> **Lollerke said:**
> I filled a bug already. [https://bugs.launchpad.net/ubuntu/+bug/509273](https://bugs.launchpad.net/ubuntu/+bug/509273)
Can you get to the desktop with nomodeset?

How do you try? Is this a kernel line option?

---

### Post by Ubuntiac on 2010-01-18
Ah, just found the link in your earlier post. Yes "nomodeset" works for me. Thanks!

---

### Post by Lollerke on 2010-01-19
**narttu: **click on "this bug affects me" here (you have to register first): [https://bugs.launchpad.net/ubuntu/+bug/509273](https://bugs.launchpad.net/ubuntu/+bug/509273)
 
Disabling desktop effects will solve the corruption.

---

### Post by SumTingWong on 2010-01-19
Same problems with Mobility X1600.

---

### Post by Lollerke on 2010-01-19
**SumTingWong: **click on "this bug affects me" here (you have to register first): [https://bugs.launchpad.net/ubuntu/+bug/509273](https://bugs.launchpad.net/ubuntu/+bug/509273)

---

### Post by SumTingWong on 2010-01-19
> **Lollerke said:**
> **SumTingWong: **click on "this bug affects me" here (you have to register first): [https://bugs.launchpad.net/ubuntu/+bug/509273](https://bugs.launchpad.net/ubuntu/+bug/509273)

Done.

---

### Post by Lollerke on 2010-01-19
> **SumTingWong said:**
> Done. Thanks!

---

