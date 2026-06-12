---
title: "Flash sound not working in Ibex beta"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2008-10-04
Hi there if this issue has been addressed before please direct me there.

I just installed Ibex beta on my Acer TravelMate 6292. All seems to be running fine. I installed Macromedia Flash from repo's. I can play flash animations in youtube for example, but no sound from the videos.

My sound card is a Intel . BTW: Rythmbox pays radio sound quite well.
Any suggestions? I am sure it has to do with PulseAudio thingy??

---

### Post by Ripfox on 2008-10-04
There is a fix for this...I believe it's flash 10

---

### Post by shuttleworthwannabe on 2008-10-04
> **Ripfox said:**
> There is a fix for this...I believe it's flash 10
ok thanks, how do i get it and how to install it?
edit: i have v10 installed and still not work----
File name:  libflashplayer.so Shockwave Flash 10.0.0 d525

---

### Post by Muflon on 2008-10-04
I confirm that I also have this issue in the Beta.

Sound works in Rythmbox Music Player but not in Firefox/Flash.  Not working in youtube or BBC iplayer.

I have a Dell 1525.

Muflon

---

### Post by Lorenz on 2008-10-04
Works fine for me, but then I didn't do a clean install but upgraded from Hardy.

---

### Post by psyke83 on 2008-10-04
> **shuttleworthwannabe said:**
> Hi there if this issue has been addressed before please direct me there.

I just installed Ibex beta on my Acer TravelMate 6292. All seems to be running fine. I installed Macromedia Flash from repo's. I can play flash animations in youtube for example, but no sound from the videos.

My sound card is a Intel . BTW: Rythmbox pays radio sound quite well.
Any suggestions? I am sure it has to do with PulseAudio thingy??

Yes, it's been asked and answered many times. It's PulseAudio.

1. Make sure you delete any custom PulseAudio configuration.
2. If you're on a 32 bit system, Flash should work with sound (albeit slowly, as the beta version you're using has severe performance problems).
3. If you're on a 64 bit system, Flash won't work at all.

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by bpl07 on 2008-10-04
Here's one of the [bug reports]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/277175") describing one issue with flash 10 rc2 on 64-bit (from [psyke83's ppa]("https://launchpad.net/~psyke83/+archive")).

Chances are you have the flash from the intrepid repository though (flash 10 beta 2), which is not affected by that bug.  If you're a 64-bit user, I mentioned a temporary fix towards the end of [psyke83's pulseaudio thread]("http://ubuntuforums.org/showthread.php?t=866965").  It has to do with 32-bit applications not using the correct alsa-libs.  The fix works, but I'd wait for the fix to come through updates rather than adding the .conf files manually.

---

### Post by shuttleworthwannabe on 2008-10-04
thanks all, I will wait.

---

