---
title: "ATI drivers - two problems"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by amyhughes on 2008-04-27
I'm installing Ubuntu for the second time. The first time I got frustrated and installed Windows over it :)

Follwing advice I read here I followed the instruction on the following page to install ATI graphics drivers for the 780G integrated graphics:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

After I did this I had two problems.

1) I have connected an analog LCD monitor with resolution 1024x768. After installation of Ubuntu but before installation of the ATI drivers, Ubuntu only allowed a screen size of 800x600 (or smaller). After installing the drivers the screen was fritzed, like it was using a resolution the monitor couldn't handle. I had to take the machine to a monitor with a DVI input, and that worked fine and auto-detected the resolution.

Question 1: How do I prevent it from doing this? I want to use the 1024x768 monitor. After installation of the ATI drivers I'd like the screen resolution to be no more than 1024x768. It can be less, and I'll work on fixing it, but I need to be able to see it.

2) A 3D application (Second Life) told me I did not have the minimum spec to run and the display strobed (flashed quickly). I suspect I did not have 3D acceleration enabled.

Question 2: How do I enable 3D acceleration once I've installed the drivers? And is there a simple way to test it?

Thank you kindly,
Amy

---

### Post by Pumalite on 2008-04-27
ATI has little support for Linux. I'd try Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by amyhughes on 2008-04-27
> **Pumalite said:**
> ATI has little support for Linux. I'd try Envy

Thank you for the suggestion. EnvyNG fails because it does not recognize my graphics hardware (780G is quite new). Manual selection only offers version 8.3 of the drivers, and this chipset requires 8.4.

---

### Post by Pumalite on 2008-04-27
Too bad.

---

### Post by amyhughes on 2008-04-28
Okay, I ignored all the precautions and extra steps in the instructions I linked and just ran ATI's installation program and it seems to have worked. In fact it probably worked last time, too. The application reports that I'm not supported, but it does run and I get a decent frame rate.

But I do still have that strobing problem. The 3D window "blinks" once per second. If you blink once per second as you look at your screen you'll know exactly what I'm talking about.

---

### Post by vanadium101 on 2008-04-28
My suggestion would be to turn Compiz off until your card is supported (System> Preferences> Appearance> Visual Effects)

---

### Post by hardyn on 2008-04-28
having a look at the ati release notes, it does not look like your graphics chip is yet supported; i did howeever only have a quick look.

---

### Post by amyhughes on 2008-04-28
I solved the blinking by turning off visual effects on my desktop.

Edit: I see Vanadium made this same suggestion. Yep, it worked! Thanks.

---

### Post by mike farad on 2008-04-28
Did you use the new ATI Catalyst™ 8.4 drivers?  I have the same 780G chip set and I'm researching how to get the IGP to work under Ubuntu.  AMD released version 8.4 on April 16.

---

### Post by amyhughes on 2008-05-11
> **mike farad said:**
> Did you use the new ATI Catalyst™ 8.4 drivers?  I have the same 780G chip set and I'm researching how to get the IGP to work under Ubuntu.  AMD released version 8.4 on April 16.

Yes, Cat 8.4. I just followed the instructions on AMD's website. Works fine for Ubuntu.

---

