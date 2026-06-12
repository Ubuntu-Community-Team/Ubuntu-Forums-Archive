---
title: "System freeze after Try or Install wellcome screen in HP Pavillion x360"
date: 2024-06-23
forum: Installation &amp; Upgrades
---

### Post by fvroig on 2024-06-23
I have an HP Pavillion x360 notebook in which I installed a brand new empty SSD, and trying to install Ubuntu from a USB stick. I tried with 20.04 and 22.04 versions, booting in safe graphics mode. In both cases, the Welcome screen appears, but when I click on Try Ubuntu or on Install Ubuntu, the system freezes and nothing happens (although I can move the mouse pointer). The only option left is a hard reset (turn off the computer). I also tried to install 24.04, but in this case it freezes after loading plymouthd. Detail: I had Ubuntu 20.04 installed alongside with Windows in the original HDD, and it worked fine. Any ideas?

---

### Post by currentshaft on 2024-06-23
Are you able to switch virtual consoles when this happens?

Control+Alt+F3 or Control+Alt+F4 for instance

---

### Post by fvroig on 2024-06-26
[SIZE=3][FONT=arial][COLOR=#0C0D0E]After several days of trial an error, I finnaly found the solution, thanks to [this article]("https://itsfoss.com/pcie-bus-error-severity-corrected/") The freezing during installation occurs because the Linux kernel appears to have issues with HP hardware, and stays reporting lots of PCI Bus errors. The solution is to boot the kernel with the option **pci=noaer** and after that the instllation runs smoothly.
[/COLOR]
[COLOR=#0C0D0E]To do this, I booted from the Live CD and at the GURB screen, I press the key "e" to edit the options of the 'Try or Install Ubuntu' menu. I added the **pci=noaer** option after the **quiet splash** options, and press Ctrl-x to save and proceed to boot.[/COLOR]
[COLOR=#0C0D0E]
Of course after the installation, it is necessary to include the same kernel option in the installed GRUB. To modify the installed GRUB from the Live CD, I followed [this recipe]("https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd")[/COLOR][/FONT][/SIZE]

---

### Post by currentshaft on 2024-06-26
Thanks for the detailed explanation. If you could mark the thread as "Solved" (from the "thread tools" menu in the top-right), that would be helpful to the community.

---

