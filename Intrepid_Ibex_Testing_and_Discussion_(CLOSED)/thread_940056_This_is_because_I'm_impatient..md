---
title: "This is because I'm impatient."
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by napalm brain on 2008-10-06
So, I just installed the 8.10 beta. Now, my headphone jack no longer works. I checked the sound preferences, everything is a go, yet, no sound when I plug my headphones in. Does anyone know how to remedy this?

P.S. In 8.04, I recall having to go through a series of steps to fix it. So, this has been a persistent problem.. but one that I had fixed before. I just don't remember how I did. 

I guess this what I get for being impatient.
\\:D/

EDIT: This may or may not help:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by SunnyRabbiera on 2008-10-06
yeh Ibex is still a beta so expect issues, I dont know if these issues will be fixed by the final so your guess is as good as mine.

---

### Post by napalm brain on 2008-10-06
Oh, believe me, I realized this.. but like I said, I was excited. And when I get excited, I download betas and don't really know what I'm doing. I am sure I will find a fix. Or figure something out. Or maybe someone else will?

That's why I came here. :)

---

### Post by Ryadt on 2008-10-06
> **napalm brain said:**
> Oh, believe me, I realized this.. but like I said, I was excited. And when I get excited, I download betas and don't really know what I'm doing. I am sure I will find a fix. Or figure something out. Or maybe someone else will?

That's why I came here. :)
You came to the wrong forum. Beta releases is not discussed here.
Go here: [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by Flimm on 2008-10-06
Hey naplam brain, do you have a launchpad account? You might want to submit a bug report there, since you've decided to beta test Intrepid Ibex. Glad to see you helping!

---

### Post by napalm brain on 2008-10-06
> **Ryadt said:**
> You came to the wrong forum. Beta releases is not discussed here.
Go here: [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)
Eek. 
Maybe a moderator could move the thread?

**Flimm:** Why yes I do. I'll head over there. Thanks. :)

---

### Post by markbuntu on 2008-10-06
Intrepid has not changed much soundwise,alsa1.0.17 and pulseaudio 0.9.11 neither are very big changes. if your mixer does not have a switch for headphone sense or something like that, try this:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

But first, alsa seems to be using a generic hda driver, you may need something more specific, try these:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)


[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

They are for hardy, not many intrepid threads to go by yet.

---

### Post by Primefalcon on 2008-10-06
I'm prob going to stick to hardy for at least a week, maybe 2 after Ibex is released. let them smooth out the bugs a little

---

### Post by Sef on 2008-10-06
>  Maybe a moderator could move the thread?

moved to ibex forum.

---

### Post by inportb on 2008-10-06
Since Intrepid's still beta, there're new upgrades every day. If you keep installing them, you might end up with working audio. You should still submit a bug report though. Thanks for helping out.

@primefalcon: I think many people would have a good reason to wait this time, especially if the proprietary video drivers don't arrive on time.

---

### Post by napalm brain on 2008-10-06
I probably should emphasize that my audio is fine. Music sounds crisp, no crackling noises, etc. The only real problem is when I try to plug in my headphones the speakers on my laptop will not mute and no sound comes out of the ear-pieces. Other than that, everything is good.

I'm minutes away from submitting a bug report though. The *first* I've ever done. It's actually a good feeling to make one. As weird as that may sound.

@markbuntu - I tried all of those suggestions, to no avail. For the life of me, I can't remember what I did to fix it before. It would certainly make life a little easier. Thank you for help.

---

### Post by psyke83 on 2008-10-06
> **napalm brain said:**
> So, I just installed the 8.10 beta. Now, my headphone jack no longer works. I checked the sound preferences, everything is a go, yet, no sound when I plug my headphones in. Does anyone know how to remedy this?[/code]

The PulseAudio ALSA plugins are now enabled *by default* in Intrepid - this is different behaviour from Hardy. This means that you are most likely suffering from a PulseAudio issue (though we can't rule out ALSA yet). You need to use the PulseAudio tools to troubleshoot your issue properly.

See: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

(Basically: install "padevchooser", and use the PulseAudio Manager & PulseAudio Volume Control to diagnose whether your headphones are listed properly).

---

### Post by napalm brain on 2008-10-06
It appears that I have that package installed. 

Nothing is listed in this area, unfortunately.

---

