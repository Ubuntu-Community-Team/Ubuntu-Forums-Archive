---
title: "alsa vs oss and sound"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-08-13
i am using dell xps laptop and when i do a lsmod, i see both alsa and oss sound drivers loaded.. 

i have force unloaded oss drivers and the sound still works.. then why load them in the first place?  

Also my headphone 1 is muted when i boot.. and sound only works if i unmute and increase the volume on this.. some applications like mediaplayer doesnt work at all.. but youtube in firefox works.. 

the sound applet doesnt work at all, i had to use the gnome alsa mixer to increase the volume.. 

please help..

---

### Post by psyke83 on 2009-08-13
Those are really ALSA kernels modules which provide OSS emulation. See: [http://alsa.opensrc.org/index.php/OssEmulation](http://alsa.opensrc.org/index.php/OssEmulation)

You can safely unload them, but OSS application will not work unless you run the OSS application with PulseAudio's "padsp" wrapper.

I recommend you research all the recent posts on PulseAudio - we're using a test version in Karmic right now. Your audio issues probably stem from PulseAudio and not ALSA itself.

---

