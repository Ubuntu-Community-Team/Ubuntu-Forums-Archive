---
title: "Installation of Lubuntu 18.10 freezes at Installing Locales."
date: 2018-11-02
forum: Installation &amp; Upgrades
---

### Post by Imerion on 2018-11-02
Hi everyone! I have been trying to install Lubuntu 18.10 on my GPD Win device ([https://en.wikipedia.org/wiki/GPD_Win](https://en.wikipedia.org/wiki/GPD_Win)). The live system works perfectly, but when installing, after choosing to use the entire disk and use automatic formatting, the installation freezes around 29% on installing locales. I have tried waiting for a long time but nothing happens and there doesn't seem to be any other information about what went wrong. Does anyone have an idea?

---

### Post by geofftf on 2018-11-05
I once had another version of Lubuntu stall during installation. I hit the <Esc> key and got a script that gave me some clues. I tried again and everything worked.

---

### Post by Imerion on 2018-11-07
Thanks for the tip! <Esc> doesn't do anything here though. I think there is another installer for 18.10, so perhaps that is why. It's always on the locale-part, but when trying again it reached 39% instead...

---

### Post by linuxinavian on 2018-11-12
During that locale part of the installation, you can use qps (lxqt's task manager) to see what is going on in the background. Then you can see the setup tries to generate every locale in the universe from A to Z. That's why it's taking so long. But the setup finishes eventually.

---

### Post by Imerion on 2018-11-12
Oh, I see. Odd, but then I'll give it another try. Thanks!

---

### Post by sudodus on 2018-11-12
I suggest that you try from an iso file with Lubuntu 18.04.1 LTS, first live, and if it looks good, try to install it.

- The LTS release is supported for three years (until April 2021), while 18.10 is only supported for nine months (until July 2019).

- The version 18.04.1 is more debugged and polished, so more likely to work well, while 18.10 is the first version with a completely new design (LXDE is replaced with LXQt and several program packages are replaced, for example the installer (ubiquity is replaced with calamares). By the time a new version with LTS (long time release) will be ready, in April 2020, I think the new design of Lubuntu will be well debugged and polished, and if you stay with 18.04.x LTS until August 2020, and 20.04.1 LTS, it should be as debugged and polished and the current 18.04.1 LTS.

- But if you have very new hardware, that is not supported by the current LTS release, it is a good idea to try the newest short-lived version (now 18.10).

See this link and links from it: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Imerion on 2018-11-17
Thanks! Those are good tips. I usually use the short term releases myself to get new features but recommend the LTS versions for others who are curious. But this time I actually tried 18.04.1 too in case it worked. Problem was I only got a black picture there, whereas the live version of 18.10 worked perfectly. I also wanted LXQt since I feel many useful usability features are getting deprected in GTK. So I'm going to give it another try now. I figure I might just as well remove the excess locales again once the system is installed. I'll report back on how it worked out. Thanks for all the help this far!

---

### Post by Imerion on 2018-11-17
Yep, that worked fine! I guess I was just a bit too impatient. ;) Thanks again!

Everything seems to work out of the box besides WiFi, for which I needed to follow the instructions here to make it work: [https://wiki.archlinux.org/index.php/GPD_Win](https://wiki.archlinux.org/index.php/GPD_Win)

---

### Post by sudodus on 2018-11-17
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

