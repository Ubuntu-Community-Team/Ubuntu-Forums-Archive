---
title: "Driver issues"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by cbiccum on 2007-04-21
Hi All;

I have installed Ubuntu on a laptop with no issues at all, so thought what the heck lets' try a dual boot system on my desktop.  The dual boot works fine, my problem is that I have a few issues I can't fix.  I'm hoping you all can help.  I'm a newbie to all this so please make the advise as basic as possible if possible.

Video card resolution is maxed at 1280, can't go any higher, doesn't look good.
No sound


I'm using a Asus MB A7N8X model, I have a soundblaster card on it, and I have a AT All in one 9600 vid card.

Can someone help me?  The device manager is showing all kinds of issues, but these are the only two that are giving me an issue.

---

### Post by pepsi_max2k on 2007-04-21
For video resolution, have you installed the ati propriatary drivers? Opening desktop effects from the program menu should help you install if not. Then there should be an ati control panel that will help you change resolution/refresh rate settings. If not, you might have to learn how to edit the /etc/X11/xorg.conf file, it's not that hard once you're used to it...

For sound, I know for a fact you've got onboard nforce2 ac97 audio, and also the soundblaster which i'm guessing you've got speakers plugged in to? If so, try plugging them in to the onboard speaker slot and see if you get any sound out of that. If you do, ubuntu's set the onboard nforce2 audio to default. Plug the speakers in to whatever one you want to use as default, then get familiar with ubuntu's sound management progs... There's two in the system menu, though to get the main one you gotta right click on the system text, hit edit, and expand everything until you find a "multimedia..." config entry, tick it, then open it from the menu. Change the default sound device for everything until you find something that works (hit the test button and you'll get a beep). Try to use Alsa where available, so long as it works too (you get beeps). Also, type "sudo asoundconf list" in a terminal and it should give you a list of all your sound cards, kinda like:

Names of available sound cards:
Live
NForce2

Then run something like "sudo asoundconf set-default-card Live" to set the default card (obviously, instead of Live use whatever you want).

---

### Post by cbiccum on 2007-04-22
> **pepsi_max2k said:**
> Opening desktop effects from the program menu should help you install if not. Then there should be an ati control panel that will help you change resolution/refresh rate settings. 

There's two in the system menu, though to get the main one you gotta right click on the system text, hit edit, and expand everything until you find a "multimedia..." config entry, tick it, then open it from the menu. Change the default sound device for everything until you find something that works (hit the test button and you'll get a beep). Try to use Alsa where available, so long as it works too (you get beeps). Also, type "sudo asoundconf list" in a terminal and it should give you a list of all your sound cards, kinda like:


Then run something like "sudo asoundconf set-default-card Live" to set the default card (obviously, instead of Live use whatever you want).

Hi there, thank you so much for the quick reply.  But I'm having issues trying both your suggestions. 

Video, I cannot find the "desktop effects" program any where, I have tried installing it in add/remove and I can't find any program related to that.

For sound I right clicked the system at the top but cannot find anything to do with "multimedia" 

Please help, it sounds like your suggestions will fix my problem but I just can't get into them.  Need a bit more newbie walkthrough.

---

### Post by carusoswi on 2007-04-29
Not certain if this may help anyone else, but, when I went into System-Preferences-Sound, I found the drivers for my Audigy 2 listed:  CA0106

They were listed four times, so that if I selected any of the top three in any of the categories (playback, capture, etc), I got no sound.  If I went through each category, pulled down the list and selected the fourth and final instance of CA0106, the test and, of course, my sound began to work.

I don't understand it, but, I'm happy to have gotten it working.

Caruso  



> **pepsi_max2k said:**
> For video resolution, have you installed the ati propriatary drivers? Opening desktop effects from the program menu should help you install if not. Then there should be an ati control panel that will help you change resolution/refresh rate settings. If not, you might have to learn how to edit the /etc/X11/xorg.conf file, it's not that hard once you're used to it...

For sound, I know for a fact you've got onboard nforce2 ac97 audio, and also the soundblaster which i'm guessing you've got speakers plugged in to? If so, try plugging them in to the onboard speaker slot and see if you get any sound out of that. If you do, ubuntu's set the onboard nforce2 audio to default. Plug the speakers in to whatever one you want to use as default, then get familiar with ubuntu's sound management progs... There's two in the system menu, though to get the main one you gotta right click on the system text, hit edit, and expand everything until you find a "multimedia..." config entry, tick it, then open it from the menu. Change the default sound device for everything until you find something that works (hit the test button and you'll get a beep). Try to use Alsa where available, so long as it works too (you get beeps). Also, type "sudo asoundconf list" in a terminal and it should give you a list of all your sound cards, kinda like:



Names of available sound cards:
Live
NForce2

Then run something like "sudo asoundconf set-default-card Live" to set the default card (obviously, instead of Live use whatever you want).

---

