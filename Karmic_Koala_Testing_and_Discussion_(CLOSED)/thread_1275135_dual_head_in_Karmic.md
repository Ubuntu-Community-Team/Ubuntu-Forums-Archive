---
title: "dual head in Karmic?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frogotronic on 2009-09-25
Hi,

I've got an R300 ATI RAdeon card, want to use my dual head monitor set-up.  Noticed that my xorg.conf is minimal.  Is Xorg.conf still being used to set-up dual head?  If not, how do I set that up?  Display manager isn't working.

- CH

---

### Post by dino99 on 2009-09-25
i've never experienced with dual head & don't know how karmic deal with that. But i can remember that i've read on this forum some time ago that we need to tweak xorg.conf & declare display0 & display1.

I think that google can help you " ubuntu dual head" / "karmic dual head"

---

### Post by Longinus00 on 2009-09-25
> **cement_head said:**
> Hi,

I've got an R300 ATI RAdeon card, want to use my dual head monitor set-up.  Noticed that my xorg.conf is minimal.  Is Xorg.conf still being used to set-up dual head?  If not, how do I set that up?  Display manager isn't working.

- CH

What do you mean display manager isn't working? Does it crash? What happens when you start it form the command line?
```
gnome-display-properties 
```

> **dino99 said:**
> i've never experienced with dual head & don't know how karmic deal with that. But i can remember that i've read on this forum some time ago that we need to tweak xorg.conf & declare display0 & display1.

I think that google can help you " ubuntu dual head" / "karmic dual head"

No, this shoulde be completely unnecessary.

---

### Post by frogotronic on 2009-09-25
Hi Longinus00,

  The Display GUI comes up, but the screens are as "Mirrored".  When I uncheck them, it asks me to logout, which I do, but the screens are not as dual head, but again as mirrored.  This used to work in intrepid and jaunty, but it doesn't seem to work in karmic a6.

- CH

---

### Post by Longinus00 on 2009-09-25
> **cement_head said:**
> Hi Longinus00,

  The Display GUI comes up, but the screens are as "Mirrored".  When I uncheck them, it asks me to logout, which I do, but the screens are not as dual head, but again as mirrored.  This used to work in intrepid and jaunty, but it doesn't seem to work in karmic a6.

- CH

So the mirrored button stays checked and everything? When you uncheck mirrored, can you move the screens around first or does it want you to log out right away.

---

### Post by frogotronic on 2009-09-28
No, the button becomes unchecked, I can move the screens around, and it then (after I click OK) asks me to logout.  

Upon logging in, the "Mirror Screens" button is checked and no dual head.

- CH

---

### Post by Longinus00 on 2009-09-28
> **cement_head said:**
> No, the button becomes unchecked, I can move the screens around, and it then (after I click OK) asks me to logout.  

Upon logging in, the "Mirror Screens" button is checked and no dual head.

- CH

So in your absence I tested out dual head by using a usb drive on my main computer. I get the same bug as you unfortunately and my laptop with karmic installed just crashes while trying to detect extra monitors. This is very sad because dual monitors worked so great in 9.04... Anybody else have this problem?

---

### Post by frogotronic on 2009-09-28
> **Longinus00 said:**
> So in your absence I tested out dual head by using a usb drive on my main computer. I get the same bug as you unfortunately and my laptop with karmic installed just crashes while trying to detect extra monitors. This is very sad because dual monitors worked so great in 9.04... Anybody else have this problem?

likely...I'll file a bug report and cross-link it here.

It is an Alpha release...

- CH

---

### Post by Longinus00 on 2009-09-29
> **cement_head said:**
> likely...I'll file a bug report and cross-link it here.

It is an Alpha release...

- CH

I've solved this problem, at least for my computer. The hint for solving it came from when I tried to enable the dual monitors using xrandr directly. The default virtual desktop size is quite small, just 2048x2048. Usually, gnome-display-properties is supposed to change this when you enable dual head but I guess that's broken or something.

My default xorg.conf in /etc/X11/ was
```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Change the Virtual screen to 
```
		Virtual	4096 4096
```
or whatever pleases your fancy.

I also can't find your bug report. Could you link it here so I can comment on it?

***

Just noticed you have a radeon R300. You won't be able to use compiz if you have a virtual desktop larger than 2048x2048 because of the small texture size of the card.

---

### Post by frogotronic on 2009-09-29
> **Longinus00 said:**
> I've solved this problem, at least for my computer. The hint for solving it came from when I tried to enable the dual monitors using xrandr directly. The default virtual desktop size is quite small, just 2048x2048. Usually, gnome-display-properties is supposed to change this when you enable dual head but I guess that's broken or something.

My default xorg.conf in /etc/X11/ was
```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Change the Virtual screen to 
```
		Virtual	4096 4096
```
or whatever pleases your fancy.

I also can't find your bug report. Could you link it here so I can comment on it?

***

Just noticed you have a radeon R300. You won't be able to use compiz if you have a virtual desktop larger than 2048x2048 because of the small texture size of the card.

Hi Longinus00

  Sorry for the delay.  Same problem here.  Your solution worked for me, but I choose

```
		Virtual	2560 1024
```

And I'm good to go.

I've tried to file a bug report using the new ubuntu-bug protocol but it crashes on Karmic.

Will try one more time and then I'll email someone directly and then post the bug report back.

You're also correct about no compiz.

- CH

---

### Post by frogotronic on 2009-09-29
Hi Longinus00,

   Got the bug report filed and crosslinked to this post.

   [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/438715](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/438715) 

  Thanks for your help

- CH

---

### Post by Longinus00 on 2009-09-29
> **cement_head said:**
> Hi Longinus00,

   Got the bug report filed and crosslinked to this post.

   [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/438715](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/438715) 

  Thanks for your help

- CH

Alright, I confirmed the bug.

---

