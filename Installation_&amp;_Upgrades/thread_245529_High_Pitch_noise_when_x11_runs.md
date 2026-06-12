---
title: "High Pitch noise when x11 runs"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by wiz561 on 2006-08-28
Hi!

   I'm just getting started with ubuntu.  I finally got my new machine all put together and everything works fine on it.  However, when it boots up (in text mode), everything is silent.  But as soon as you startx and it loads the windows manager (I've tried gnome, kde, and rat poison), there is this extremely high pitched whine / squeal coming from the machine.  I don't know if it's the motherboard, video, or processor, but I would guess the video card.  I've also changed monitors (lcd (vga) and a tv screen (svideo) ), and this does not seem to help.  I've also tried different resolutions and the livecd, but nothing works.

   It's a new machine (AMD 64 4200+ x2) processor with a MSI k9n-sli platinum board and a nvidia geforce 4 mx4000 graphics card.  I've had this card in a different machine and it worked fine.  But on the other machine, I ran fedora core 5.  

    Now in this new machine, this whine is driving me crazy!  If anybody can help, it would be greatly appreciated!


Thanks in advance,
Mike

---

### Post by dereknet on 2006-08-28
What type of monitor do you have? LCD / CRT?

My CRT some times makes a high pitch whine when I look at things that have a lot of white, closing the window would make the noise stop. So for you, can you do anything to change the noise or will it never stop?

---

### Post by wiz561 on 2006-08-28
It's actually both of them, and neither of them make the noise.

I have a LCD flatpanel monitor, and I have also tried a CRT.  When I startx, the noise comes from the computer case and not the monitor.

My next step is to try to take the video card out and try to replace it with something else.  Before I did that though, I was going to run it past our ubuntu expert here at my work.


Thanks,
Mike

---

### Post by wiz561 on 2006-08-28
OK...  I did a little more research, and it turns out that it's not the video card but has to do with the audio.

When I disable the onboard soundcard or use "nosound" in mplayer, no whine.  As soon as I use the sound, there's a whine.

So, thank you for the help, but I think I'm going to try to take this to another topic.


Thanks!

---

