---
title: "fingerprint, multitouch and touchscreen in karmic"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by janmyszkier on 2009-09-08
Does anyone knows how is karmic ubuntu going to work with these technologies Out-of-the-box? 

I'm asking because there was going to be a tool for jaunty to calibrate stylus and touchscreen but it was postponed cause of lack of workforce, 

Touchscreen was going to be detected with HAL from jaunty as well, but didn't in most cases.

Usually I dont have time to sit over my laptop few hours (that's how much time it usually takes to install touchscreen and calirate it, and I need to find and read manuals over and over) trying to install some hardware everytime I update my kernel.

and to say more: 
"Windows XP Tablet PC Edition &#8211; The original version released in November 2002" - says wikipedia. 7 years passed, and ubuntu users still don't have system to work with their hardware out-of-box. 

Windows Vista - november 2006 - integrated fingerprint system authentication. It was 3 years ago. Ubuntu still doesn't have it included in any kind of release.

Hence the questions. 
1. Will multitouch work?
2. Will touchscreen be finally working by default? 
3. Will fingerprint authentication be integrated to system login by default? (Vista does it already, and you're going to fight for notebooks with windows 7 when karmic is released). Think about windows users say: "We have it working since previous release! How about you?"

---

### Post by internalkernel on 2009-09-09
I'll bump this thread - would love to know also... looking at many touchscreen models and trying to make sense of the confusion of what is supported and what isnt... 

Maybe I'll just to go Best Buy with a LiveCD? ;P

---

### Post by Matthias Kersten on 2009-09-20
Well, I'm testing Karmic and there's still a lot of work to be done.

Fingerprint (at least as of now) does not work out of the box.  Some models are supported with the fprint driver, but my Lenovo x200t fingerprint reader has not been reverse-engineered yet.

Multitouch - I don't think it's supported yet.

Touch screen working out of the box - Well, my x200 touch screen works, but is definitely not calibrated.  I have just been looking for several hours how to calibrate it, and I haven't found anything.  The only easy tool in synaptic is evtouch related, and gives me an error when I try to run it.  I don't know why my tablet pen was calibrated out of the box and my touch screen wasn't.

To developers: It would be really nice to have a touch screen calibration method that actually works!  Everytime I use windows, I think about how convenient it is to use the touch screen.  Linux in general seems to be a work in progress.

---

