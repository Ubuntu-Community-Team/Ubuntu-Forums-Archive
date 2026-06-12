---
title: "[SOLVED] Can't use Skype"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by borobudur on 2006-08-27
I just installed the debian skype. Everything works fine: I can start the software and log in into my account but I can't make a phone call. I do the same without problems under Windows and Mac. If I try calling Skype says right away: Call faild.

Anybody an idea what I should do?

---

### Post by atomkarinca on 2006-08-27
you should check the sound card preferences, whether you have full duplex or not. skype needs a full duplex card.

---

### Post by borobudur on 2006-08-27
That was the problem. Thanks! 

That's what I did:

[HOWTO: Hear multiple sounds using Both ESD & ALSA]("http://ubuntuforums.org/showthread.php?t=32063")

Thanks Gandalf and atomkarinca!

---

### Post by borobudur on 2006-09-25
well, there is still a problem. I can use skype for once, I mean I can connect to a phone or computer and use it properly. Then I hang up and I wanna use it again but I can't anymore. It says that there is a sound problem like I had at the very beginning. 
I need to close skype totally and start again. Then I can use it once again. 

That looks really strange to me. Has anyone an idea?

---

### Post by borobudur on 2007-03-28
Okay, I found out that I have to use the OSS devise and I need to make a restart to "see" the change. With ALSA the microphone doesn't work.

The problem with that OSS is that if an other application uses sound before I start Skype it doesn't work again. 

Why is ALSA not working???

---

