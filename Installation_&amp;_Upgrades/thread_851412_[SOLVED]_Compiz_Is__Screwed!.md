---
title: "[SOLVED] Compiz Is  Screwed!"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by Rich930 on 2008-07-06
hi,
ive just installed hardy and compiz wont work.
i go to system>preferences>appearences. and enable desktop effects but it wont work.

when i try to install pythongtk2 it asks for python2.5 but it says its already installed!?

btw the internet wont work because i have a linksys WMP54g card - which wont work - so ive heard - if you could help me with that please - that would be amazing.

:D

---

### Post by isaacj87 on 2008-07-06
Hey there,

1) First off, what is your video card and secondly, what did you do to install the drivers for them.

2) If it says it's already installed, I wouldn't worry about it. More than likely, the packages you're trying to install already came installed by default.

3) I found this after a little googling. See if these instructions work for you. I found 2 possible solutions...Try this one first: 

-- [http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")

If that's a no go...

-- [http://hehe2.net/linuxhowto/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/]("http://hehe2.net/linuxhowto/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/")

---

### Post by Rich930 on 2008-07-07
hey um i have an ATI Radeon X1550 Series 512mb graphics card.
ERr, no i havent installed any drivers :P i didn't think i needed to.?
thanks i will have a look at those links. :)

---

### Post by isaacj87 on 2008-07-07
Yup, you need to install the drivers for your ATI card...Ubuntu can't by default. However, it is fairly simple to get the drivers installed thanks to the Hardware Drivers Manager or Envy. I'd take a look at Envy, as it will set-up the driver automatically for you.

You can have a look at Envy's homepage:

-- [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Once you get the drivers all taken care of, you can enable Compiz. :)

Let me know if you need anything else!

---

### Post by Rich930 on 2008-07-07
hey :)
lol
your gunna hate me :P

i installed the envy thing just fine - but it still wont let me enable desktop effects.

and ive tryed probably every solution to try and fix my wireless card, but still nothing :S.

---

### Post by estyles on 2008-07-07
Both of those (wireless card) solutions seem to imply that you have to download and compile ndiswrapper on your own.  I believe it's in the repositories so you can just install it from there (I assume you can hook up an ethernet cable temporarily with the wireless not working) - I seem to recall having nothing but trouble trying to compile ndiswrapper (some dependency problems, I think).  Then get the driver you need and follow the ndiswrapper instructions on how to use it.  Don't skip any steps - I speak from experience.  If you can't find the instructions for how to do it, post again and I'll see if I can dig up the ones I used.

For the desktop effects, when you go to System->Preferences->Appearance, does it have the radio-buttons greyed out, or are you able to enable Extra effects and just don't notice any changes?

One thing that may not fix your problem, but will definitely help if you get it working - install compiz config settings manager from the repositories.  I have no idea why it isn't installed by default, but it definitely makes it easier to set up compiz, and to figure out exactly what it can do.

---

### Post by isaacj87 on 2008-07-07
> **Rich930 said:**
> hey :)
lol
your gunna hate me :P

i installed the envy thing just fine - but it still wont let me enable desktop effects.

and ive tryed probably every solution to try and fix my wireless card, but still nothing :S.

Hmm...okay, let's figure out why...

Open up terminal and run this command:

```
compiz --replace
```

It should give you some error...post that here. 

Secondly, visit this thread --> [http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

and run compiz-check and post the output...This should give us insight into why Compiz isn't working.

---

### Post by Rich930 on 2008-07-08
hey thanks.
ive got it working now.
My friend helped me install the driver and it worked. :D
many thanks.

i still have had no luck with the wireless yet though.

---

### Post by isaacj87 on 2008-07-08
> **Rich930 said:**
> hey thanks.
ive got it working now.
My friend helped me install the driver and it worked. :D
many thanks.

i still have had no luck with the wireless yet though.

Good to hear...

About your wireless card, does it have the option to enable it in the "Hardware Drivers" Manager? Goto **System->Administration->Hardware Drivers** and have a look.

---

### Post by Rich930 on 2008-07-09
ive fixed that too now. :D
i did it just after i posted my last post. but all i did was start all over again after removing everything. and i followed this guide: [Here]("http://ubuntuforums.org/showthread.php?t=588045")and it actually found my router so i connected but then it didnt work. so i restarted and it worked.

Again thankyou very much for your time and help. :D

---

