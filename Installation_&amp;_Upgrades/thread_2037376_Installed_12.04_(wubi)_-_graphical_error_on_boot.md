---
title: "Installed 12.04 (wubi) - graphical error on boot"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by bootproblem on 2012-08-04
[http://i.imgur.com/BWrGH.jpg]("http://i.imgur.com/BWrGH.jpg")

This is what I get when I boot into Ubuntu. Is there anything I can do to fix it?

2x nVidia GTX 570 on SLI
Intel Core i7-2600k
16Gt RAM

---

### Post by ranger1021994 on 2012-08-04
100% graphics card problem.
You have Nvidia or ATI ?
Press Ctrl+Alt+F1 and login
If NVIDIA
type : > sudo apt-get install nvidia-current
If ATI
type :> sudo apt-get install fglrx

---

### Post by bootproblem on 2012-08-04
2x nVidia GTX 570 on SLI.
When I press Ctrl+Alt+F1, the quality doesn't get any better. The screen switches to text mode, but I can't read any of the text.

---

### Post by bootproblem on 2012-08-04
I gave it a try using USB installation - however, it freezes the whole computer while trying to boot.

---

### Post by bcbc on 2012-08-05
Use nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bootproblem on 2012-08-05
Thanks, I got it installed. Now I'll need to figure out how to enable SLI..

Edit. Apparently SLI is already enabled, it's just that the second display won't work. If I try to 'Detect Displays' on nvidia-settings, it says: ERROR: Failed to probe for display devices on GPU-1 'GeForce GTX 570'.

---

### Post by bcbc on 2012-08-05
See if this helps... [http://askubuntu.com/questions/137232/12-04-dual-monitors-nvidia-settings-problem](http://askubuntu.com/questions/137232/12-04-dual-monitors-nvidia-settings-problem)

---

