---
title: "Tablet PC Fujitsu-Siemens Stylistic ST5112 not booting"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Guruji on 2009-09-26
Hi,
I'm trying to boot on my tablet pc from Live CD/USB but no luck so far.
I see the boot menu, then usplash.. and then a black screen with nothing else. During the black screen if i press the power button, the usplash shutdown appears.
I tried to upgrade the installed jaunty to karmic via software update, but the behavior is the same, usplash->black screen.

If anybody as an idea on how to fix this, you are welcome, if not, you can please help me to put together the informations necessary for a bug report.

Jaunty is working perfectly (well.. a part from the on tablet buttons and sound)

Fujitsu-Siemens Stylistic ST5112
Core2 U7600 1.2Ghz
Intel 945GM chipset

ty
2gb ram

EDIT: started around alpha2, so it's not the recent boot problems

---

### Post by Favux on 2009-09-26
Hi Guruji,

For the bezel buttons in Jaunty see posts #'s 15 and 16 here:  [http://ubuntuforums.org/showthread.php?t=1259154&page=2](http://ubuntuforums.org/showthread.php?t=1259154&page=2)

---

### Post by Guruji on 2009-09-26
well.. didn't fix my karmic problems.. but.. it's... heaven! all the keys are working, rotation is working fully without any script... it's a bit like christmass... well it would be if i got karmic to boot ;)

but anyway, thank you so much for this little link!:D

---

### Post by Favux on 2009-09-26
Hi Guruji,

Great!  You're welcome.

---

### Post by Guruji on 2009-10-01
bump..
no one has the slightest idea of what i could try to boot it on karmic? I'd like to be ready for karmic release, cause for now it's sounding like a "stay forever on jautny you'll never be able to upgrade...":confused:

---

### Post by miegiel on 2009-10-01
> **Guruji said:**
> bump..
no one has the slightest idea of what i could try to boot it on karmic? I'd like to be ready for karmic release, cause for now it's sounding like a "stay forever on jautny you'll never be able to upgrade...":confused:

try installing with the alternate CD

---

### Post by Guruji on 2009-10-01
I tried already from the alternate cd, I can install it.. but after reboot it's the same as starting from the live cd.. usplash and then nothing..

---

### Post by miegiel on 2009-10-01
> **Guruji said:**
> I tried already from the alternate cd, I can install it.. but after reboot it's the same as starting from the live cd.. usplash and then nothing..

That's when X starts, it starts a lot sooner in the boot process compared the jaunty. 

Really "usplash and then nothing.."? Not even a blinking HDD LED ?

I just remembered now, the 1st time I booted after installing from the alternate CD, I had an empty screen for ages (the LCD was on standby or off). At least 15 min but it might have been 30. I went off to do some other stuff :D The only reason I didn't reset was the HDD LED showing some activity. I have no idea what it was doing but eventually X started.

---

### Post by Guruji on 2009-10-02
i'll try to wait 30min to see if something happens, i'll post about it soon.

EDIT:just to be sure, it's just 1 time you had to wait 30min and then it was booting fine?

---

### Post by miegiel on 2009-10-02
> **Guruji said:**
> EDIT:just to be sure, it's just 1 time you had to wait 30min and then it was booting fine?

Yes, I don't have to wait 30 min everytime I boot. That would have been no fun at all.

That was with the alternate CD of xubuntu btw. I tried the desktop CDs of ubuntu and xubuntu, maybe I should have had more patience with those too. The karmic betas have been released too now, going to see how that installs on my machine this weekend.

---

### Post by priegog on 2009-10-02
> **Guruji said:**
> bump..
no one has the slightest idea of what i could try to boot it on karmic? I'd like to be ready for karmic release, cause for now it's sounding like a "stay forever on jautny you'll never be able to upgrade...":confused:

Yeah, I know how you feel, I'm stuck in intrepid in an old tablet I have. 
Here's the bug report I filed, go check it out (even tho it doesn't seem to be the exact same problem) [https://bugs.launchpad.net/ubuntu/+bug/386272](https://bugs.launchpad.net/ubuntu/+bug/386272)
However you can start to diagnose the problem by trying to boot the live cd but turning on the "acpi=off" option on the boot menu. If it boots that way, then it is an incompatibility with your computer's ACPI/motherboard, and you could put that in your bug report. 
Good luck, and let us know.

---

### Post by Guruji on 2009-10-02
miracle happens! I managed to boot on a karmic beta live usb, installed... and back to square 1 but this time not even usplash, 
it goes from grub to some writings to ..nothing..
I'll do some more tests tonight and try acpi=off, i'll post the results.

---

### Post by Guruji on 2009-10-02
well that was a short miracle.. i really don't know why it happend. I tried to boot again from the liveUSB..and no way.
Starting it with ACPI=off works but then everyhting is slow and the pen is not working...

btw, how do i call the grub2 menu at startup on an installed karmic to add the acpi=off lline? I tried Esc but nothing is happening...

---

### Post by priegog on 2009-10-02
> **Guruji said:**
> well that was a short miracle.. i really don't know why it happend. I tried to boot again from the liveUSB..and no way.
Starting it with ACPI=off works but then everyhting is slow and the pen is not working...

btw, how do i call the grub2 menu at startup on an installed karmic to add the acpi=off lline? I tried Esc but nothing is happening...

Yeah, well that's the problem with not having the ACPI functions available, many things won't work: the pen, the buttons, the screen brightness, and when shutting down, it won't properly shut down.
So that's why I'm stuck in intrepid. I think you'd better file a bug report.
And I don't really know anything about grub2, so can't help you there.

---

### Post by Guruji on 2009-10-02
doesn't sound very promising. 

But how come it managed to boot once from the liveUSB ??? with everything working?!

---

### Post by priegog on 2009-10-02
> **Guruji said:**
> doesn't sound very promising. 

But how come it managed to boot once from the liveUSB ??? with everything working?!

No idea, man... but I just tried the beta live cd with my tablet and it happens just as you describe, a black screen and that's it (which is a change from what it does with jaunty, as you can see in the bug page), so maybe our problems are much more related than I previously tought... 
Whatever the case, the fact remains that we are still at the mercy of the developers to get this fixed... otherwise I don't see any workarounds in the near future.

---

### Post by Favux on 2009-10-02
Hi Guruji & priegog,

Could it be an Intel video problem?  Have you looked into that?  Lot's of problems with Intel video in Jaunty, but they've fixed a lot of it in Karmic.

Guruji you said you have the Intel 945 chipset I think.  So in a terminal:
```
lspci | grep VGA
```
And then search the Karmic forum for anything relevant.

---

### Post by Guruji on 2009-10-05
Jaunty might have problems with the intel chipset.. but it was working perfectly.. so if karmic fixed it..hmmm..i don't know how!..

I'll boot from a jaunty liveusb and try "lspci | grep VGA" and follow your advice to see what happens.

---

### Post by Guruji on 2009-10-17
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

this is what lspci gives me, which one would it be 945, 943 or 940?

one more thing, i just noticed , if i boot the live USB in "safe graphics mode" it boots and pen is working. 
I have sound, which i didn't in jaunty, but it slowly fades until it get muted completely, all volumes to the max.

how can i tell the installed karmic to boot into safe grafics mode?

---

### Post by Guruji on 2009-10-17
ok, here's what I did.. not a fix.. but a usable workaround.
I noticed there was no xorg.conf in my system (of course it has never been able to boot) so i copied the one from the liveUSB (booted in safe graphics mode) to the hdd, and now i can boot, no fancy effects, sound working for a few seconds and then fading to nothing (if i close the music player, wait some time (couple of min) and start again, the sound is back.. and fades again to nothing after a few seconds, volume levels didn't change nowhere)

so it's not a fix.. but better than nothing. is there some way to tweak my xorg.conf to get things a little bit further?

thanx

---

### Post by miegiel on 2009-10-18
> **Guruji said:**
> ok, here's what I did.. not a fix.. but a usable workaround.
I noticed there was no xorg.conf in my system (of course it has never been able to boot) so i copied the one from the liveUSB (booted in safe graphics mode) to the hdd, and now i can boot, no fancy effects, sound working for a few seconds and then fading to nothing (if i close the music player, wait some time (couple of min) and start again, the sound is back.. and fades again to nothing after a few seconds, volume levels didn't change nowhere)

so it's not a fix.. but better than nothing. is there some way to tweak my xorg.conf to get things a little bit further?

thanx

In karmic you don't (shouldn't?) need a xorg.conf anymore, that 's why it was missing. I know some people had boot troubles after upgrading jaunty to karmic and solved it by deleting/renaming the old xorg.conf they still had on their disk from jaunty. You should be able to find more info on xorg.conf in karmic in the karmic sub-forum.

As for your sound problem, I've never heard of a problem like that. But I think it definitely deserves it's own thread with a appropriate title ;)

---

### Post by Guruji on 2009-10-18
without the xorg.conf file x wont start...
i tried to tweak it a bit but the only way to get it to work is by setting
"Driver"  "vesa"
else it wont boot at all.
But with vesa i have only 2d working, compiz doesn't work at all.

---

### Post by miegiel on 2009-10-18
> **Guruji said:**
> without the xorg.conf file x wont start...
i tried to tweak it a bit but the only way to get it to work is by setting
"Driver"  "vesa"
else it wont boot at all.
But with vesa i have only 2d working, compiz doesn't work at all.

I understood that, just thought that I'd clarify why xorg.conf was missing and point out that having an xorg.conf can cause problems too. Just so that you're aware.

I had a hard disk related boot problem with karmic. It's fixed now, but I had to add *libata.force=noncq* to the kernel boot options in grub (behind *quiet splash*). Maybe there's a graphics boot option you can use :-k

---

