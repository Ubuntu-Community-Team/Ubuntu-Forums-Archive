---
title: "Installing same packages on multiple computers"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by csh on 2010-01-13
When installing same packages, or updating Ubuntu on multiple computers, if I have to download and install same packages by running Synaptic Package Manager on each computer, or running update manager on each computer to update Ubuntu, it will waste a lot of bandwidth and time.

So, is there anyway for just using ONE of the computers to download and install the packages (including the dependencies, with or without Synaptic Package Manager) / Ubuntu updates, then install the same packages / Ubuntu updates on other computers without re-download on each computer?

---

### Post by Onesimus on 2010-01-13
Follow this guide:

[http://ubuntuforums.org/showthread.php?t=564301]("http://ubuntuforums.org/showthread.php?t=564301")

I have found it works a treat - you don't even need all machines running on same version of Ubuntu !

---

### Post by konqueror7 on 2010-01-13
i usually prefer to use APTonCD...i believe its in the repos. what it does is burn or make and image of your current apt cache so that it can be shared by others, actings as a 3rd party source so to say...

---

### Post by csh on 2010-01-13
> **Onesimus said:**
> Follow this guide:

[http://ubuntuforums.org/showthread.php?t=564301]("http://ubuntuforums.org/showthread.php?t=564301")

I have found it works a treat - you don't even need all machines running on same version of Ubuntu !

Thanks for the reply. The link you provided is about updating Ubuntu right? If installing new packages, example: MPlayer, on multiple computers, does the same way work?

---

### Post by Onesimus on 2010-01-13
It works exactly the same way.  You nominate one computer (the server) to download packages.  Any computer that requires a new (or updated) package requests it from the server, the server then downloads the package (if it doesn't have it already) and the client then receives it from the server.

---

