---
title: "Lucid, Wine, WoW and Teamspeak. The alsa horror."
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by t.rei on 2010-04-11
Hi,

I currently dug up my old wow account and thought I might give it a shot if it runs smoothly. 

So everything installed without problems. And now the fun thing starts.

Out of the box (lucid) WoW stops playing any kind of sound if run on pulseaudio. eve-online works fine. Eve voice doesnt (I can hear, but cannot speak).

doing the chmod -x to /usr/bin/pulseaudio and killing it (effectively shutting off pulseaudio without having to uninstall anything) gives me stable sound in wow and eve, and eve-voice is working. 

Sounds good? NO. Because now I feel this urge to actually use something like teamspeak while playing any game. After all these are no singleplayer ones, and not being able to say "game crashed" or something is bad, when using ingame tools.

I tried quite a few things... aoss... pasdp... setting wine to oss, to alsa... editing the asound.conf... blacklisting modules... 

Is there any up to date, comprehensive howto... guide... faq... anything that is actually working?

I'd love to ditch windows... wow actually runs alot smoother and loads WAY faster on lucid! :D Speaking with my fellow players however kindof is the essence of the multiplayer online thingy. I even have one of these lines we all hate: "It used to work". This means: pulseaudio, soundconfiguration, alsa integration, whatever is getting WORSE *sniff*

Thanks for any hint (unless it's to one of those outdated, not working, something-else-braking quides from long long time ago. :P )

goal is:
** To have a game with sound (via wine)**
AND
** to have teamspeak with in and out (wine or native)**
working at the same time with proper quality.

t.rei

---

