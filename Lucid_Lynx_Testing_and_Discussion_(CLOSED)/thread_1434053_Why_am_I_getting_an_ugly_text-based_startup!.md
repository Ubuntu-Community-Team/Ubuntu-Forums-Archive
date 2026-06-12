---
title: "Why am I getting an ugly text-based startup?!"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jw12321 on 2010-03-19
Hello,
Isn't there supposed to be a graphical startup on the Beta? When I turn on or shut down my computer, I see a screen with "Ubuntu 10.04" written in crude text and four dots on a purple background. I have seen screenshots of the new Ubuntu bootup with the new logo; but for some reason I do not see these on mine.

Can someone give me some assistance here? Thank you.

---

### Post by MadMan2k on 2010-03-19
because you have no kernel modesetting

---

### Post by n0dix on 2010-03-19
If not the final release, maybe in future updates fix the issue.

---

### Post by RAOF on 2010-03-19
If you're using the restricted drivers (nvidia or fglrx), or have disabled kernel modesetting for some reason, then you get the text-based VGA splash.

It's technically much more difficult to do the same level of pretty splash screens on cards without kernel modesetting, so we don't.

---

### Post by MadMan2k on 2010-03-19
> **RAOF said:**
> 
It's technically much more difficult to do the same level of pretty splash screens on cards without kernel modesetting, so we don't.
not really - we had exactly this with usplash. Its just that plymouth lacks some framebuffer fallback.
But as the text based boot is an exception, it is not worth polishing it any more...

---

### Post by recluce on 2010-03-19
> **RAOF said:**
> If you're using the restricted drivers (nvidia or fglrx), or have disabled kernel modesetting for some reason, then you get the text-based VGA splash.

It's technically much more difficult to do the same level of pretty splash screens on cards without kernel modesetting, so we don't.

I really don't understand why usplash is not provided as an alternative to plymouth. Even IF plymouth works, I see it displaying its splash for less than five seconds (YEAAAH!) before the login-screen appears.

---

### Post by keybuk on 2010-03-19
> **RAOF said:**
> If you're using the restricted drivers (nvidia or fglrx), or have disabled kernel modesetting for some reason, then you get the text-based VGA splash.

It's technically much more difficult to do the same level of pretty splash screens on cards without kernel modesetting, so we don't.

Actually we're just deliberately stress-testing the text plugin for Beta 1 - we'll test the vga16fb renderer in Beta 2 (but it's pretty boring and simple)

---

### Post by jw12321 on 2010-03-19
Thanks for telling me what's wrong--how do I fix it though?

---

### Post by keybuk on 2010-03-19
> **jw12321 said:**
> Thanks for telling me what's wrong--how do I fix it though?

You're taking part in Beta testing; we'd rather you enjoyed the text-based screen for a while, and contribute to the testing (after all, that's why you're using the Beta right?)

---

### Post by jw12321 on 2010-03-19
Yah, the text based startup is better than no startup at all!

Can't wait for the final release!
Thanks.

---

### Post by RAOF on 2010-03-19
> **keybuk said:**
> Actually we're just deliberately stress-testing the text plugin for Beta 1 - we'll test the vga16fb renderer in Beta 2 (but it's pretty boring and simple)

Aww, really?  That's disappointing.  I rather like the text based Ubuntu 10.04 boot.

Maybe I'll have to blacklist vga16fb :D

---

### Post by recluce on 2010-03-20
May I repeat one question: why does the plymouth splash appear so late in the boot process? Once it does appear, the login screen is only about 5 seconds away for me (maybe 15 to 20 seconds if ureadahead is profiling). usplash shows up right after the grub screen on jaunty.

---

### Post by FrancoNero on 2010-03-20
I know about the mode-setting thing (I have nvidia), but... for some reason, all I have is nvidia drivers. there's no nouveau option. how come? i know for a fact it's installed

---

### Post by ikt on 2010-03-26
So the ugly text boot screen will go away in beta 2?

---

### Post by RAOF on 2010-03-28
> **FrancoNero said:**
> I know about the mode-setting thing (I have nvidia), but... for some reason, all I have is nvidia drivers. there's no nouveau option. how come? i know for a fact it's installed

Nouveau is what you get when you haven't installed the nvidia binary drivers; it's there by default.  That's why you don't see it in Hardware Drivers.

---

### Post by sfreed on 2010-03-29
My big question is why is everyone so hung up on a "pretty" boot screen? It's just a boot screen. It will go away in a few seconds. Aren't there far more important issues to deal with than slowing down the boot process with useless graphics?

- and yes, I turn it all off.

--
steve.

---

