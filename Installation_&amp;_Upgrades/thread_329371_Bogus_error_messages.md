---
title: "Bogus error messages"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by Sintu on 2007-01-01
I finally got the drivers running for my Nvidia Geforce4 Mx440 under Edgy. So I decided to install some software with the Add/Remove Programs app. I began to install WINE, then for some reason decided to click cancel. Now whenever I try to install stuff using Add/Remove Programs, it gives me this error: 

"Wine Windows Emulator cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type."

What can I do? Thank you for you time!

---

### Post by adaptr on 2007-01-01
The software install did not finish in a known good state - run "sudo apt-get -f check" in a terminal to correct it.

Perhaps Synaptic also has this built in - you should probably try that first.

---

### Post by Sintu on 2007-01-01
> **adaptr said:**
> The software install did not finish in a known good state - run "sudo apt-get -f check" in a terminal to correct it.

Perhaps Synaptic also has this built in - you should probably try that first.

Thank you so much for the speedy reply! How do I know if Synaptic has it built in, and how would I run it? I don't want to mess this install up, I just reinstalled last night because I screwed up trying to install the drivers for my vid card. Thank you so much!

---

### Post by Sintu on 2007-01-01
I tried running that command in the terminal, but it didn't work. Same problem. Any other ideas?

---

### Post by Sintu on 2007-01-01
I found this thread>>>http://ubuntuforums.org/showthread.php?p=1917580<<< but it didn't help very much. Could I just get another package manager or something? Or could I reinstall the add/remove programs app? How would I do that? Thank you.

---

### Post by Sintu on 2007-01-01
And now it's working. What in the world?.... I thought I left these weird problems behind with Windows....

---

