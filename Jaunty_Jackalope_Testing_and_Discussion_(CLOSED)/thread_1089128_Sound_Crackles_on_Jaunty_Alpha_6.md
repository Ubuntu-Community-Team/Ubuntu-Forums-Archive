---
title: "Sound Crackles on Jaunty Alpha 6"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-03-06
I currently have no real sound. It just crackles when I play songs. Pulseaudio doesn't help. What to do?

---

### Post by dzark on 2009-03-06
what flavour soundcard?

tried turning it down (run 'alsamixer')..

---

### Post by iaskedalice09 on 2009-03-06
Intel 82801H (ICH8 Family) HD Audio Controller

---

### Post by go7Ul1ai on 2009-03-06
Wait a second... Alpha 6? Do you live in the future? That's insane! Way to go man!

---

### Post by perlluver on 2009-03-06
Yes so anyway back to the topic at hand, try alsamixer in a terminal, and turn the sound down to 81 on the master and master M and PCM.  Then try to play audio again.

---

### Post by kansasnoob on 2009-03-06
Crimsun is working on it:

[http://ubuntuforums.org/showthread.php?t=1084919](http://ubuntuforums.org/showthread.php?t=1084919)

And he's polite enough to let us know!

---

### Post by vene4ka on 2009-03-06
> **perlluver said:**
> Yes so anyway back to the topic at hand, try alsamixer in a terminal, and turn the sound down to 81 on the master and master M and PCM.  Then try to play audio again.

tnx, it really helps

---

### Post by iaskedalice09 on 2009-03-07
Thanks, worked like a charm!

---

### Post by iaskedalice09 on 2009-03-07
*blushes* Wait a sec...alpha 5... just updated and looked at the March calendar out of habit.

Jaunty's login screen is hot.

---

### Post by iaskedalice09 on 2009-03-07
BTW, what happened to the Thread Solved thing in Thread Tools? It's not showing for me. :(

---

### Post by gjoellee on 2009-03-07
> **iaskedalice09 said:**
> BTW, what happened to the Thread Solved thing in Thread Tools? It's not showing for me. :(

I think they have removed it, however the forum pages has been loading a lot faster after they removed it :D

---

### Post by nevelis on 2009-03-16
> **iaskedalice09 said:**
> Jaunty's login screen is hot.

Ohhhhhhhhhhhhhh yeah =3

I had this problem too, and this thread helped.  I just busted open the volume control by the clock.  My "Front" speaker was right up but PCM was right down.  If I turned up "PCM" slowly the sound came back, and reduced front by a bit and the crackling went down.

So that's gfx fixed, sound fixed, now I just want to see the VPN working again and I'm happy with the jauntz!

Thanks everyone

Edit: On that note, VPN is going now!  WOOOOOOOHOOO!

---

### Post by markbuntu on 2009-03-16
My usb headset crackles if the pulseaudio volume control is not open. How's that for weird?

---

### Post by Halow on 2009-03-16
It's funny, but I've been getting crackles on and off since way back, but sometimes it's not reproduceable. (mostly it happens on a cold boot. rebooting makes it work just fine. and then other times, nothing I can do stops it.) Intel Integrated sound just seems to be a little crazy for me. My USB sound works great, on the other hand.

---

### Post by markbuntu on 2009-03-16
That's funny, my on-board sound (ALC883) works great and so does my pci sound card (C-Media8768) either alone or in simultaneous mode since the update last week. (simultaneous would cause pulse to get kicked off the cpu before that) but now my usb headset, which previously worked fine refuses to not crackle unless pavucontrol is running.

EDIT: Last night I got another update and all is well. OOPs, spoke too soon. usb headset sound works fine until pavucontrol is opened and then closed, then it crackles. Once opened I need to keep pavucontrol open or the usb headset crackles.

---

