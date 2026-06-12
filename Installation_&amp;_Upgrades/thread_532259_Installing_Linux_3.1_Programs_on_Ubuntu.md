---
title: "Installing Linux 3.1 Programs on Ubuntu"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-22
I just discovered that the installation disk that came with my computer battery backup power surge thing can be installed on Linux 3.1. Bear in mind we bought this thing like 7 years ago. My question is, how can I install this on Ubuntu, or can I? It has a folder full of random programs and an "install" program that's a script apparently, but I don't know how I can run it. Any suggestions?

This is the webpage for this particular software: [http://www.intellipower.com/rups2k.htm](http://www.intellipower.com/rups2k.htm)

Thanks,
Dan

---

### Post by Howler9443 on 2007-08-22
I think what you may want is a daemon called "nut". Its in the repositories, you can start Synaptic and search for "nut".

Nut may or may not support your ups, I would definitely take a look at it though. Nut is a UPS daemon that monitors UPS activity. So if you lose power you can configure nut to shut the machine down or do whatever. I will be testing this package myself pretty soon on my server.

I hope this helps.

---

### Post by mocoloco on 2007-08-22
As is being suggested by Howler9443 you should forget using the old software designed for an old Kernel.  Even if you could get it working, I'm sure nut or other newer software has better features.  What brand and model is your UPS (your battery backup power surge thing :)?
My Tripp-Lite UPS plugs in via USB, and it was automatically recognized and I configure it through the "Power Management" app (under System -> Preferences).

---

### Post by dbsoundman on 2007-08-26
I really don't know the actual manufacturer of my UPS unfortunately; it's a sort of obscure offbrand apparently, but it works fine, so I can't complain. I do have some information about it's general operation though, thanks to my (failed) attempt at installing powerd, another UPS management system. Powerd ran a program that told me what the basic signal was that was sent to the computer via the serial input when the power goes out: powerd described it as "CTS LOW", which if I'm thinking correctly, is the basic message that most standard UPS units send when the power goes out.

I have now installed NUT, but what do I do now? The documentation on their site seems to assume I know something about how to write .conf files and such, but I really don't. So what do I need to do to get this thing to shut off my computer when the power goes out and the battery is low? I don't have any networked slaves or anything, so it should be pretty simple; I just don't know how to write this configuration file, and I can't do anything until it's done...

Thanks,
Dan

---

### Post by maybeway36 on 2007-08-26
I don't think there is such a thing as Linux 3.1. Last I saw, it had 2.4 and 2.6 branches.

---

