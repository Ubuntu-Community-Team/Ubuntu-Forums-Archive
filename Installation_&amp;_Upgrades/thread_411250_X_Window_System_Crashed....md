---
title: "X Window System Crashed..."
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by cry0k1n3t1c on 2007-04-16
Ok, I was running Hoary Hedgehog (Old, but it was the only distro I had at the time) and decided to upgrade via apt-get distro upgrade.  Well, It downloaded all the files and gave me an error list on the installation part... something about not finding the files for Breezy on my Hoary disc.  It updated Synaptic and I thought I actually worked.  I upgraded a few games and found that they would not even run.  Confused, I just turned my computer off and went to bed.  I woke up this morning, turned on my laptop, and watched it's boot.  It goes through the checklist like normal, goes black like it is about ready to load the GUI, and goes back to command line.  Loads a few more things, and goes black again.  It repeats that process a few times and gives me an error message saying that X Windows System (I have no idea if that is even the right name... I'm still new to linux) failed to load.  Then it locked up so I could not read the errors.  I REALLY dont want to have to format all my data, because I had a lot of homework on there that I didn't get a chance to back up.  Is there any way to re-install hoary without erasing my data?

---

### Post by Shootfast on 2007-04-16
Do you get a command prompt or login screen?

---

### Post by cry0k1n3t1c on 2007-04-17
No, it just locked up.  I went into the recovery mode and it let me run commands, so I was thinking about just doing apt-get on X... but I dont know if that will work.

---

### Post by cry0k1n3t1c on 2007-04-17
ok, so I just figured out that it doesn't actually lock up.  I have to hit the D key for it to say yes.  I reconfigured X with sudo dpkg-reconfigure xserver-xorg and it didnt help.  I reinstalled it using ap-get remove xserver-xorg and apt-get xserver-xorg... still didnt work.  Any ideas?

---

