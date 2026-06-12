---
title: "Upgrade from 22.04 to 24.04 boots to command line - dependencies/held-back packages"
date: 2024-08-30
forum: Installation &amp; Upgrades
---

### Post by JustSomeCanuck on 2024-08-30
Hello everyone,

I was upgrading a laptop from 22.04 to 24.04, now that the direct upgrade is available. The first issue that I ran into was the graphical updater froze and I had to complete the upgrades using the terminal. I'm not sure if that is important for what follows, but it might be.

After the upgrade was completed, I restarted the computer, and now it only boots to the command line. I tried the suggested answer at the following link, since that screenshot was exactly what I saw: [https://askubuntu.com/questions/1511718/ubuntu-24-04-lts-booting-gui-missing](https://askubuntu.com/questions/1511718/ubuntu-24-04-lts-booting-gui-missing)

When I ran that command, the text in the attached picture appeared.

How do I fix this? I should note that the GUI does briefly appear when I turn the computer on before it switches to the command line, and also when I turn it off or reboot from the command line (using sudo poweroff or sudo reboot).

---

### Post by JustSomeCanuck on 2024-08-30
Well, this is embarrassing and uplifting at the same time - I was able to fix it myself! Yay for me \\:D/

In case anyone else has the same problem, I just ran [FONT=Courier New]sudo apt-get install[/FONT] to get the specific version numbers of the packages that the terminal displayed. Easy peasy - just like Ubuntu should be!

---

