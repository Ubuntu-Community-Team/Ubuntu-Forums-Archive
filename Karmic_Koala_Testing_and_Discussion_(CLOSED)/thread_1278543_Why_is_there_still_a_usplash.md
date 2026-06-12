---
title: "Why is there still a usplash?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2009-09-29
Usplash is still installed and I guess its only used on shutdown.

Is there still a reason to have it around with Xsplash being released?  Is it that important to have it displayed during shutdown?

---

### Post by exploder on 2009-09-29
Usplash makes the shut down and restart process look nice. They did a nice job making the start up and shut down processes look attractive for this release, that was the plan and they really did an outstanding job.

---

### Post by Nickedynick on 2009-09-29
If we want Ubuntu to look like a professional looking OS, then simple things like usplash at shutdown make a big impact.

---

### Post by exploder on 2009-09-29
> If we want Ubuntu to look like a professional looking OS, then simple things like usplash at shutdown make a big impact.

Well put and to the point.

---

### Post by 23meg on 2009-09-29
It's also going to be needed for the fsck and encryption password prompts.

---

### Post by NCLI on 2009-09-29
Not to mention as backup if Xsplash fails for some reason.

---

### Post by MacUntu on 2009-09-29
Booting with 'quiet' and 'splash' still shows a lot of output - anyone knows when *this* will go away?

---

### Post by VMC on 2009-09-29
It does look nice. I removed xplash and "splash" from kernel stanza during the buggy period. I just recently re-installed xplash and replaced "splash". It does look more professional.

---

### Post by Compintuit on 2009-09-29
> **MacUntu said:**
> Booting with 'quiet' and 'splash' still shows a lot of output - anyone knows when *this* will go away?

No idea - but this is still an alpha :)

---

### Post by dasunst3r on 2009-09-29
From what I have seen thus far, I actually disagree with this transition to xsplash.  I see usplash as a simple solution that did what it needed to do.  Furthermore, when rebooting with my "everyday user" hat on, I have been seeing more "scary black screen with text on it," if you will.  Finally, I would've much preferred a progress bar over a throbber.

For what I see as a well-done splash screen, I suggest a look at openSUSE.  Their screen is simple, yet allows those who want more information to get it by hitting Esc.

---

### Post by anonymous_user on 2009-09-29
Does xsplash only work for startup? Its seem strange to have separate splash programs for startup and shutdown.

---

### Post by benjamimgois on 2009-09-30
> **dasunst3r said:**
> From what I have seen thus far, I actually disagree with this transition to xsplash.  I see usplash as a simple solution that did what it needed to do.  Furthermore, when rebooting with my "everyday user" hat on, I have been seeing more "scary black screen with text on it," if you will.  Finally, I would've much preferred a progress bar over a throbber.

For what I see as a well-done splash screen, I suggest a look at openSUSE.  Their screen is simple, yet allows those who want more information to get it by hitting Esc.

Remenber that Karmic still an Alpha release. We'll have some conclusions if Xplash is a good or a bad think on the final release.

---

### Post by nzjrs on 2009-09-30
> **exploder said:**
> Usplash makes the shut down and restart process look nice. They did a nice job making the start up and shut down processes look attractive for this release, that was the plan and they really did an outstanding job.

I get 10s of black text on screen before xsplash starts. The boot process looks ugly for me.

I don't see any evidence of usplash on boot at all.

---

### Post by dadedo123 on 2009-09-30
Are these texts going to stay even for the final release?

---

### Post by Nickedynick on 2009-09-30
Does the Ubuntu logo on the shutdown usplash look stretched to anyone else? I'm on a 22" (wide)screen and it looks a little odd...

---

### Post by dadedo123 on 2009-09-30
> **Nickedynick said:**
> Does the Ubuntu logo on the shutdown usplash look stretched to anyone else? I'm on a 22" (wide)screen and it looks a little odd...
Maybe you've got the wrong resolution.

---

### Post by zacbarton on 2009-09-30
Yea it looks stretched for me also. My usplash.conf has the correct settings - 1280x800.

---

### Post by Nickedynick on 2009-09-30
I haven't changed any settings, so it shouldn't be the wrong res. I'm on 1680x1050.

---

### Post by MacUntu on 2009-09-30
> **Nickedynick said:**
> Does the Ubuntu logo on the shutdown usplash look stretched to anyone else? I'm on a 22" (wide)screen and it looks a little odd...

> **zacbarton said:**
> Yea it looks stretched for me also. My usplash.conf has the correct settings - 1280x800.

That's one of the problems with Usplash and it's not (easily) fixable. Your screens show a 4:3 image which then gets stretched to the native resolution. IIRC that's caused by the native resolution not being one of the VBE modes ([http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)).

Fix a.) Maybe your monitor can be told not to stretch 4:3 output to the native resolution.

Fix b.) Download Usplash's source code and replace the logo with an already compressed one. That way the stretching will decompress the image and the logo will be a perfect circle.

Eg. my notebook's resolution is 1280*768, Usplash runs at 1024*768. 1024/1280 = 0.8, 768/768 = 1. So I would scale the logo's width with a factor of 0.8 and leave it's height alone.

---

### Post by Nickedynick on 2009-09-30
Is there a plan to replace usplash on shutdown with xsplash eventually (Lucid)?

Also, is there a way to tell usplash to resize both dimensions to the same scale? Surely that'd sort it out too.

---

