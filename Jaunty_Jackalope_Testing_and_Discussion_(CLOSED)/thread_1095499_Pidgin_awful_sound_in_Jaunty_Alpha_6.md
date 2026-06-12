---
title: "Pidgin awful sound in Jaunty Alpha 6"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pmalvr on 2009-03-13
Hi,

I started to notice an awful sound on pidgin in alpha 6 of jaunty, especially when new messages are sent or received. Thus anyone more notice this ?

Thanks

---

### Post by go7Ul1ai on 2009-03-13
Probably pulse audio issues, I get it all the time.

---

### Post by mempf on 2009-03-14
Yeah, I get the same issue.

Pulseaudio seems to hang when it happens causing full CPU usage and a lot of IO useage. It's getting very annoying.

Hopefully it will get fixed soon.

---

### Post by gjoellee on 2009-03-14
there are known sound problems in Jaunty, hopefully they will be fixed very soon!

---

### Post by fut21 on 2009-04-07
Still the same issue here with pidgin, awful sound.

---

### Post by macogw on 2009-04-07
"Awful sound" is not descriptive.  Do you mean the loud system beep?  Do you mean whatever's playing is crackling? What are you trying to say?

---

### Post by LORD_PoLvO on 2009-04-07
ive noticed sound issues with pidgin on my testing machine using pulseaudio but i seem to be geting no sound at all at certain points ? any ideas

---

### Post by Jesterday on 2009-04-07
I thought I was being electrocuted. That is the type of awful sound I am getting. If you stuck your fingers in a wall socket, it would be the type of sound I would expect. 

And it only happens with Pidgin.

---

### Post by Polygon on 2009-04-07
> **macogw said:**
> "Awful sound" is not descriptive.  Do you mean the loud system beep?  Do you mean whatever's playing is crackling? What are you trying to say?

the guy who works on pulseaudio for ubuntu says its because the frequency is unstable when a sound starts playing sometimes, so the pidgin sounds (and other sounds) sound  crackly/static-y

its a pulseaudio thing and i think it should of already been fixed...i haven't gotten it for a while

---

### Post by fut21 on 2009-04-07
Its a crackling sound, on a MSI wind.

---

### Post by fut21 on 2009-04-07
Is there any bugrepports about this?

---

### Post by talent03 on 2009-04-08
The only bug report I see is this one:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

I left a comment that I was affected. I have this exact same problem in Jaunty as of now with all the updates. I don't understand how pulsaudio can have so many problems. It is really frustrating. I have given pulseaudio a chance since Hardy but this is just getting annoying. Distributions should have not included pulseaudio if it was going to be this buggy. Pulseaudio devs still have plenty of work on their hands.

---

### Post by Kareeser on 2009-04-09
You should demand a refund, talent03.

Seriously, now, the devs aren't being paid for their work, so we should be grateful for any work that **does** get done.

You're always free to uninstall pulseaudio and fall back to ALSA.

---

### Post by Ryan_K on 2009-04-10
> **Kareeser said:**
> You should demand a refund, talent03.

Seriously, now, the devs aren't being paid for their work, so we should be grateful for any work that **does** get done.

You're always free to uninstall pulseaudio and fall back to ALSA.

And your post sends the wrong message to new users, imo. I think what talent03 was getting at is that if Pulse Aduio isn't ready for prime time, it shouldn't be made the default if wide support for common hardware isn't there, 

I personally have the same issue where sounds (only noticed it in Pidgin) are crackled. It should be noted that Jaunty is beta software, so some issues are expected, but still.. Your post sounds quite smug, at least in how I read it.

System -> Preferences -> Sound is where you can change where your default sounds get sent to ALSA or OSS which may not have the issues  described here.

---

