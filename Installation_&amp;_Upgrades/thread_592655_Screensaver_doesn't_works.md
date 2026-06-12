---
title: "Screensaver doesn't works"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by mf-linux on 2007-10-26
Hello!
I have recently installed Xubuntu 7.10 (clean installation), but screensaver never works. When unnattended even during long time, my laptop always displays the desktop. However, preview of screensavers works normally.
Any idea?:confused:

---

### Post by Pumalite on 2007-10-26
Enable it.

---

### Post by TheBigBentley on 2007-10-27
> **Pumalite said:**
> Enable it.

I have the same problem. And mine is enabled. Preview works fine but when it comes time for the screensaver to come on I just get a black screen instead.

---

### Post by mf-linux on 2007-10-27
Of course, mine is also enabled, and I have tried with different time intervals. I don't get black screen but desktop always on. However, with previous releases of xubuntu, screensaver worked perfectly.

---

### Post by iamPatrick on 2007-10-31
I'm having the same problem with the screensaver never kicking in. Not a huge issue but one thats nagging me. Preview works fine but even if I set the "Regard computer idle" to a minute I get nothing, never.

Oh, and guys, the screen is supposed to turn black/blank, thats part of the power management. You can get at those options from within the Screensaver preferences control panel.

---

### Post by TheBigBentley on 2007-11-04
Well I just upgraded to 7.10 and now the screensaver comes on but the image freezes about 5 seconds in. The computer isnt locked because if I move the mouse it closes the screensaver like it should. And ive tried gl and non gl screensavers and they both do the same thing.

---

### Post by Pumalite on 2007-11-04
Try:
sudo apt-get install xscreensaver

---

### Post by TheBigBentley on 2007-11-06
confused. I already have xscreensaver installed. Im begining to think its a video driver conflict of some sort. Although the Screensaver is the only thing thats giving me video troubles.

---

### Post by Pumalite on 2007-11-06
Have you disable screensaver and ran xscreensaver at the Terminal?

---

### Post by D351 on 2007-12-11
I'm having this problem too... At first, I thought that it was just set for "blank screen" for the screensaver, as it's acting just like it would if it were set that way, but when I went to change the screensaver, it wouldn't change. Then, I tried messing with the time until idle settings and they made no difference. I think it's just going to blank screen after five minutes, as if those were the screensaver settings.

---

### Post by guarache1 on 2008-01-23
My unbuntu 7.1 is a clean install, it has been working for over 3 weeks.  The screensaver, which is the fiberlamp was working fine until today.  It goes into saver mode and the fiberlamp is shown but when I move the mouse to get the login to get back to the desktop, all I get is a black screen with a working mouse.  I have to re-boot because it won't come out of this screen.   Does anyone know what could be the problem?

---

### Post by kbless7 on 2008-01-23
> **TheBigBentley said:**
> I have the same problem. And mine is enabled. Preview works fine but when it comes time for the screensaver to come on I just get a black screen instead.

Make sure you don't have it turn the screen off before the screensaver turns on. I have a time option for each of those, so I set the "turn off screen" after the screensaver has been on for 30 minutes.

---

### Post by Pumalite on 2008-01-24
> **guarache1 said:**
> My unbuntu 7.1 is a clean install, it has been working for over 3 weeks.  The screensaver, which is the fiberlamp was working fine until today.  It goes into saver mode and the fiberlamp is shown but when I move the mouse to get the login to get back to the desktop, all I get is a black screen with a working mouse.  I have to re-boot because it won't come out of this screen.   Does anyone know what could be the problem?
screensavers come with 'Advanced Tab'>Power Management>All the way to the right>'Never'

---

### Post by slimx3m on 2008-01-25
> **Pumalite said:**
> screensavers come with 'Advanced Tab'>Power Management>All the way to the right>'Never'

i was having the same problem and i already did that, but still doesn't work.  my screen still coming on blank.  does any body knows how to change the settings from the terminal?!

---

### Post by ExecutorE on 2008-01-26
I'm running Xubuntu Gutsy, and I see no "advanced" tab. I installed clean a week ago, and all I see is a black screen instead of a screensaver. I also get nothing when I click the menu item for electricsheep. 

please help.

thanks!

EE

---

### Post by tv0571 on 2008-02-07
I'm seeing similar problems after upgrading from Feisty to Gutsy.

Half of the previews don't work.  In the ones that do (including Picture Folders which is what I want), the screen begins to fade after the appropriate time, but just as the screensaver should start up, the screensaver quits and pops back to the screen.

This worked OK before. 

On the up side, sound works better in Gutsy than it did in Feisty.  Looks like it is easier now to select a default sound card that most software will respect.

Barron

---

