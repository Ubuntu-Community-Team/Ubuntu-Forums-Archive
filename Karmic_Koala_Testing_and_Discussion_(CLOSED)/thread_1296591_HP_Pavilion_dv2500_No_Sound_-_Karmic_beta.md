---
title: "HP Pavilion dv2500 No Sound - Karmic beta"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by prkos on 2009-10-20
This laptop came with Vista but there were various hardware problems with it, sound doesn't work after Vista update, also optical drive problems... 

I installed Karmic beta today, Internet and wireless are working (after installing drivers) but I can't get any sound. 

Here is my info
[http://www.alsa-project.org/db/?f=bd5c14240bd6c23ef5947dc5497d32fea80dbe82](http://www.alsa-project.org/db/?f=bd5c14240bd6c23ef5947dc5497d32fea80dbe82)

when I try
```
$ aplay -l
```I get:
aplay: device_list:223: no soundcards found...


No audio found in ```
lspci -v
```

It seems something very important is missing, modules all messed up?

---

### Post by prkos on 2009-10-21
Update: 

I checked the commands from last post before I went to sleep and nothing was found. 

Now after a Shutdown and maybe after it cooled down (it gets very hot) I got soundcard recognized :) I had to go to Sound Preferences and adjust the properties and now I have sound working! 

In Alsamixer Master and PCM seem ok, but there are 2 other options that are completely on 00 and I can't get them up. Is that a problem?

What does Shutdown do that you don't get in Restart?

---

### Post by prkos on 2009-10-21
This is the config when it was working
[http://www.alsa-project.org/db/?f=64acd2ad40c9fd47e4effb13a79a1c420649ba19](http://www.alsa-project.org/db/?f=64acd2ad40c9fd47e4effb13a79a1c420649ba19)

Now it's not working again
[http://www.alsa-project.org/db/?f=0b9f63812b31a3cd3ff6a272748d569ae3160a00](http://www.alsa-project.org/db/?f=0b9f63812b31a3cd3ff6a272748d569ae3160a00)

it stopped after hibernation and suspend testing. There was a crash after hibernation but not right away. The sound was tested after that and it wasn't working. 

Why do the sound modules get unloaded?

---

