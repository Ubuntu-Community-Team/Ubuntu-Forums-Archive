---
title: "Cant access Synaptic Package manager and update manager broken!"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by DeadSuperHero on 2007-07-12
I click to access the synaptic package manager and I get this error message
> E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried to uninstall it though terminal, but it says it can't, because it's not installed. So i go to download it and install it, and find out that whenever I try and install a update the package manager says that the file may be corrupted, no matter what it is.
This all started when i was downloading and installing Second Life and I started playing a game.  Then the computer froze. I couldn't use ctrl+alt+backspace or even the quit  menu when I held the power button down. so i just held down that button down until it forced a shut down and rebooted.
So, I need to know, how can I fix this? What do I need to do?

---

### Post by Odrodzona-Sarmacja on 2007-07-12
> **Mr. Psychopath said:**
> I click to access the synaptic package manager and I get this error message

I tried to uninstall it though terminal, but it says it can't, because it's not installed. So i go to download it and install it, and find out that whenever I try and install a update the package manager says that the file may be corrupted, no matter what it is.
This all started when i was downloading and installing Second Life and I started playing a game.  Then the computer froze. I couldn't use ctrl+alt+backspace or even the quit  menu when I held the power button down. so i just held down that button down until it forced a shut down and rebooted.
So, I need to know, how can I fix this? What do I need to do?

My guess is your ext3 file system just got corrupted. I experienced something alike myself after a crash.

To fix synaptic try booting in recovery mode and get in it the shell. There you type:
"dpkg --configure -a"
This should fix synaptic.

---

### Post by shicks301 on 2007-08-04
I had the same error and fixed it by:

Booting to recovery mode in grub
Running dpkg --force-all -r secondlife-install
reboot

---

