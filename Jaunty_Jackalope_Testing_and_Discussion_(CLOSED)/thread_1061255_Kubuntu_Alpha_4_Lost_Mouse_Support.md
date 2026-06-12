---
title: "Kubuntu Alpha 4: Lost Mouse Support"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-02-05
Hey:

I have tested Alpha 3 on both Kubuntu and Ubuntu versions.  The only big issue I had was that my graphics card was not properly configured yet Alpha 4 changed that (at least by testing it on Kubuntu Alpha 4). However, I now have a new issue.  My laptop mouse/trackpad doesn't seem to be working, something that did work on Alpha 3 and updates.

Any ideas? I reverted to No Effects on Desktop to see if it was a graphic card issue but it still doesn't work.

---

### Post by PRGUY85 on 2009-02-05
Anyone?

---

### Post by olskar on 2009-02-05
> **PRGUY85 said:**
> Anyone?

The only thing I can think of is this:

> The X.Org synaptics driver is absent from the liveCD, which may prevent touchpad devices from working on laptops. As a workaround, use Ctrl+Alt+F1 to switch to console, log in, run sudo apt-get install xserver-xorg-input-all to download the drivers from the network, and then return to your session with Alt+F7.

Do you have that installed?

---

### Post by PRGUY85 on 2009-02-05
Solved.  Serves me well for not reading release notes.

---

### Post by David Gerard on 2009-02-06
Ah, I got this too! Now I just need to get the network to actually connect ...

---

### Post by olskar on 2009-02-06
> **David Gerard said:**
> Ah, I got this too! Now I just need to get the network to actually connect ...

Do you have the problem with it look like it is connecting but you can not get onto the internet?

---

### Post by David Gerard on 2009-02-06
> **olskar said:**
> Do you have the problem with it look like it is connecting but you can not get onto the internet?

Not quite - I have [this one]("http://ubuntuforums.org/showthread.php?t=1060407"), where some apps can get DNS but some can't. It's so broken as to be unusable; I'm writing this from Windows, icky as it is.

---

