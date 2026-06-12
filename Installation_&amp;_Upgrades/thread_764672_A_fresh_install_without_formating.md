---
title: "A fresh install without formating?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by khongten on 2008-04-24
I have Ubuntu 7.10 on my system. Now I want to try Kubuntu 8.04. How can I do a fresh install without format the hard drive had Ubuntu 7.10? I mean just detete all files of Ubuntu and install Kubuntu freshly because **I don't want to format my hard drive**.

---

### Post by Tatty on 2008-04-24
Well, deleting all the files off a partition is essentially what formatting is.

Do you mean you dont want to lose your /home or something?  You can do that if you have it in a separate partition, otherwise you are going to have to back it up.

Aside from that you would just install as normal.  Unless im misunderstanding what you mean?

---

### Post by Sef on 2008-04-24
> I have Ubuntu 7.10 on my system. Now I want to try Kubuntu 8.04. How can I do a fresh install without format the hard drive had Ubuntu 7.10? I mean just detete all files of Ubuntu and install Kubuntu freshly because I don't want to format my hard drive

There is a way.  First use the update manager to update to Hardy Heron, then read psychocat's [installing Kubuntu]("http://www.psychocats.net/ubuntu/kde").

---

### Post by khongten on 2008-04-24
But sometimes format make the hard drive easy to break downn or have bad sectors. I only want to delete all files because I think it safe for the hard drive.

---

### Post by mozetti on 2008-04-24
> **khongten said:**
> But sometimes format make the hard drive easy to break downn or have bad sectors. I only want to delete all files because I think it safe for the hard drive.

That's not true. The only scenario where this would appear to happen is if the hard drive already has bad sectors (and the format will just point that out) or is already dying.

---

### Post by khongten on 2008-04-24
Really. I still worry a little bit, but may be I will format the hard drive. By the way, Ubuntu and Kubuntu are similar in supporting the drivers for hardware, aren't they?

---

### Post by dde on 2008-04-24
If you have anxiety about the reliabiliy of your hard drive, consider learning to use the tools 'badblocks' and 'smartctl'.  With these, you can find great detail about a drive's condition.

'man badblocks'

[http://en.wikipedia.org/wiki/Self-Monitoring%2C_Analysis%2C_and_Reporting_Technology]("http://en.wikipedia.org/wiki/Self-Monitoring%2C_Analysis%2C_and_Reporting_Technology")

To use 'smartctl' you need to install the package 'smartmontools'.  Then 'man smartctl'

---

### Post by ssj3strife on 2008-04-24
> **khongten said:**
> Really. I still worry a little bit, but may be I will format the hard drive. By the way, Ubuntu and Kubuntu are similar in supporting the drivers for hardware, aren't they?
Yes, Ubuntu and Kubuntu would have nearly the exact same hardware support. The only difference you might notice would be in the utilities you'd use to control them (KNetworkManager vs. Gnome's nm-applet, for example), which might have different features between KDE and Gnome.

---

### Post by khongten on 2008-04-25
Thank you all.
I have another question. What will happen to my hard drive if it is formated many times?

---

### Post by blackbeastofaarrgh on 2008-04-25
> **khongten said:**
> Thank you all.
I have another question. What will happen to my hard drive if it is formated many times?

Nothing! It'll work just fine, unless it is a genuinely bad drive to begin with.

---

