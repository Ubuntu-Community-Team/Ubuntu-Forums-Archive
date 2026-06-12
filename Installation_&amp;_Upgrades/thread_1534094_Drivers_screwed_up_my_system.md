---
title: "Drivers screwed up my system?"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Hero_Lief on 2010-07-19
So, I wanted to update my NVIDIA Drivers from the default to 256 (or whatever the latest is on their site). After the upgrade from their site and installing it through a command line, I've had trouble. For some reason, whenever I boot, I get the Kubuntu boot screen, even though I run plain Ubuntu. Also, after I boot it defaults to low graphics mode, and I have to hit "restart X" to make it run normal. Even then, visual effects won't enable, and games won't run, because apparently the "hardware device cannot be found". My attempts to revert back to old drivers have been unsuccessful; It says it's running the recommended right now, but I still have all these problems. Any ideas?

---

### Post by Hero_Lief on 2010-07-19
Bump

---

### Post by Hero_Lief on 2010-07-19
Nevermind, I fixed this. For future reference to others, I did the following steps.

1. Downloaded an archived driver set of driver version 195.36.24 from NVIDIA's website
2. Copied the driver to my desktop, and wrote down the name of the driver file
3. Went into commandline mode by hitting Ctrl+Alt+F1
4. Logged in and ran "sudo /etc/init.d/gdm stop", ignoring the response saying to use "service gdm stop" because that command does not work
5. Gave the command "cd ~/Desktop"
6. Began installing the driver by saying "sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run" (or whatever the driver file is that you wrote down)
7. Accepted the Terms of use, service, what have you
8. Ignored the precompile error by saying OK
9. Said yes to uninstalling the current driver version
10. Waited for the finished install
11. Said yes to updating the X config file (this fixed default low graphics mode boot)
12. Finished install, and upon reentrance into the commandline, said "sudo reboot" in order to reboot.

I still get the Kubuntu boot screen (which I'm fine with, it's HD and badass-looking, plus I never had a boot screen before, it screwed up with flickering pixels... still loaded though), but that's it. After the reboot, I fixed the arrangement of icons on my top panel (for some reason, that always gets screwed up after a driver change) and tried opening Warcraft 3 and WoW in WINE, and both ran fine! I also reenabled visual effects, and they're working fine now.

---

