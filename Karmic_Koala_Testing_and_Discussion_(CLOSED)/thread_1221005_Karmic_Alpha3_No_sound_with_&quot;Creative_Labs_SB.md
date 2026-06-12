---
title: "Karmic Alpha3: No sound with &quot;Creative Labs SB0400 Audigy2&quot; card."
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moma on 2009-07-23
Hello,

[COLOR="Red"]EDIT:[/COLOR] The solution is here:
[http://ubuntuforums.org/showpost.php?p=7783967&postcount=7](http://ubuntuforums.org/showpost.php?p=7783967&postcount=7) 

-------------------
I just installed 64bit Karmic Alpha3 (Ubuntu 9.10). 
The problem is that there is no sound.

The audio card is
$ lspci | grep audio
04:02.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

Neither this test nor ordinary ogg files produce audio/sound. Nothing!
$ speaker-test -c 6 -D surround51 -t wav

$ alsactl init
Unknown hardware: "Audigy2" "SigmaTel STAC9750,51" "AC97a:83847650" "0x1102" "0x1001"

I can remember that in Jaunty I had to start gnome-volume-control and it had an extra [Switches] tab page. It had a checkbox with label "Audigy Analog/Digital output jack" which had to be activated. Then sound was OK.

Karmic's pulseaudio controls do not have that selection.
Maybe this Audigy2 card is simply a too old.

Can you help me to hunt down this problem?
-----

Maybe you can recommend me another good audio card. 
Does "Sound Blaster X-Fi" work in Linux?
I've turned off the mobo-internal card in BIOS. Of cource I should test it first.

---

### Post by wayne_cat on 2009-07-23
can you activate it with "alsamixer" (on/off with the m key)?

edit: sorry ... did not see this ... "Unknown hardware: "Audigy2 ...."

---

### Post by wayne_cat on 2009-07-23
my sound works ... even if i get the same error:

```
root@macbook:~# alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9221 A1" "HDA:83847680,106b0200,00103401" "0x8384" "0x7680"
Hardware is initialized using a guess method
root@macbook:~#
```so alsamixer is worth a try

---

### Post by meeples on 2009-07-23
no sound at all here, according to sound preferences, i have no output devices.

help? i really wanna play idaft haha

---

### Post by moma on 2009-07-23
Re-hi and thanks for your answers so far.

I actually found the "Audigy Analog/Digital output jack" option in Alsamixer and enabled it by pressing "m" but unfortunately it does not help in this case (as it did in Jaunty).

See picture: 
[[img]http://bildr.no/thumb/454591.jpeg[/img]](http://bildr.no/view/454591)

Other options should also be right.
[[img]http://bildr.no/thumb/454593.jpeg[/img]](http://bildr.no/view/454593)
But still no sound.

---

### Post by ranch hand on 2009-07-24
It is not the age of the card.  My Audigy1 card is working with the gnome-alsamixer just fine.

---

### Post by moma on 2009-08-14
Re-hello,

Launchpad.net gave me a solution. 

Start gnome-alsamixer or alsamixer and 
1) Uncheck the "IEC958 Optical Raw" value.
2) Activate the "Audigy Analog/Digital Output Jack" option.
Of course you will also need to unmute and rise the Master and PCM values.

Picture:
[http://launchpadlibrarian.net/30299616/Sound%20in%20Karmic%20with%20Creative%20Labs%20SB0400%20Audigy2%20card.png](http://launchpadlibrarian.net/30299616/Sound%20in%20Karmic%20with%20Creative%20Labs%20SB0400%20Audigy2%20card.png)

Related bug-report:
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/400629](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/400629)

---

### Post by malegria on 2009-10-04
This also worked for me, using gnome-alsamixer and checking off "Audigy Analog/Digital Output Jack" but will this have to be done @ every boot up?

Also, is anyone else experiencing popping sounds???

---

### Post by ranch hand on 2009-10-04
> **malegria said:**
> This also worked for me, using gnome-alsamixer and checking off "Audigy Analog/Digital Output Jack" but will this have to be done @ every boot up?

Also, is anyone else experiencing popping sounds???
I use the gnome-alsamixer and do not have to reset anything once set up.

Are you talking about "popping" during boot up?  If so this seems to be normal when the card comes on line.  It is irritating.

If you are talking about "popping" at any other time, I do not get anything like that with this old audigy1 card.  All I get is great 5.1 sound out of my Altec Lansing speaker system.

---

### Post by malegria on 2009-10-04
I do have the  popping sounds at boot and right before I am supposed to get sound from any sort of application (such as before the initial song plays on Banshee).

---

### Post by ranch hand on 2009-10-04
> **malegria said:**
> I do have the  popping sounds at boot and right before I am supposed to get sound from any sort of application (such as before the initial song plays on Banshee).
I have no idea what to do about that but it would really get on my thungas.

I think you should file a bug on that one.

---

### Post by ratdude747 on 2009-10-25
the solution posted does not work for my unit. any other ideas?

---

### Post by laszlo462 on 2009-10-25
> **malegria said:**
> I do have the  popping sounds at boot and right before I am supposed to get sound from any sort of application (such as before the initial song plays on Banshee).

I have that popping sound as well.  It's nothing to do with Ubuntu.  I believe it to be the SB hardware itself.  I get the same thing on Ubuntu, XP, 7, through speakers, through headphones, etc.  I found some guy's drivers for XP that seem to help with the popping.  Just makes it less noisy, almost fuzzy, but it's still not clean sound.  Just crappy hardware I guess, I've read about quite a few people with this problem.

---

