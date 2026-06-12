---
title: "Can't boot in Ubuntu 9.10 login screen freeze"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by jazz_air_312 on 2010-03-09
Hello! It's my first post, and i want to say from the start that i'm new to linux and trying to find my way around :P So here's my problem:

I have a dual boot configuration (WinXp and Ubuntu 9.10) on a PC (my video card is an ATI Radeon 4850), i have been configuring ubuntu for the past 5 days and everything was working fine. Today i installed Screenlets (through synaptic manager), and i was adding a screenlet when the screen froze. I could move the cursor, but couldn't click anything. I left it for about 5 minutes to see if anything changes, and since it was still frozen, i did a hard reset (restart from the button).

In the grub menu i chose the normal linux boot (not the recovery mode), it loads up the welcome splash screen (with the tribal sound and the bar moving), and then the little circle cursor appears, turns into the normal arrow cursor and it hangs. I can move the cursor, but the screen is stuck with the ubuntu splash screen.

I restarted (again from the button) and went into recovery mode, but in the recovery console i can't select any option from the keyboard (i tried hitting the cursor keys, enter, nothing happens). I hit ctrl+alt+delete and it restarted the system (so the keyborad does function). In XP i found a recommendation to restart the Xserver, so i rebooted in the Ubuntu splash screen, hit ctrl+alt+F2, logged in, typed the command i found:
sudo dpkg-reconfigure -phigh xserver-xorg
restarted (sudo reboot), and got to the splash screen, which after playing the tribal sounds, turned semi-transparent (i could see the desktop wallpaper, taskbars and a black rectangle where my cairo-dock should appear), but again it freezed, no cursor. I hit ctrl+alt+F2 to go into console mode, and uninstalled screenlets (since it was the last thing i installed before the initial freeze). Screenlets uninstalled properly (i used sudo apt-get remove screenlets) so i rebooted, but it still freezes at the ubuntu screen splash (this time it wasn't transparent, just the standard screen splash). So i tried getting into console mode again, but this time my screen displays lines in a lot of colors, randomly (probably a failure from the video adapter).

I tried to describe as accurate as i can exactly what i did, i hope someone can help me :) i would really hate it to have to reinstall ubuntu and all the programs and configurations. Please help me!

---

### Post by jazz_air_312 on 2010-03-09
Here's something i forgot to add...i saw someone complain a few moments ago about ubuntu updates, and i remembered that while i was fiddling with the screenlets, a pop-up appeared notifying me (and this is the part i don't remember very well) either about updates downloaded and ready to install or about an update installed. After the update pop-up, my screen froze as i describe above. Could it be related to my problem?

---

### Post by jazz_air_312 on 2010-03-09
After searching a bit i finally found a solution, recommended [here]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") under the title Problem: Freezes right after entering login credentials

I entered the console and made compiz non-executable by running the code mentioned on the troubleshooting page. After the reboot i managed to boot to desktop, where i made compiz executable again, and restored the visual effects from none to normal (my last setting).

Hopefully this topic might help other users that have this problem. Topic solved :)

---

