---
title: "Ubuntu 10.10 server: Cannot login after installation"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by EmilyFromFarAway on 2010-12-30
Hi,
I installed Ubuntu 10.10 AMD64 server on a dual Opteron Fujitsu Siemens Primergy RX220. After reboot the screen goes black (as if X is probing), displays garbage (short white horizontal stripes aligned such that I get 2 broken vertical stripes) and the system seems to stop (no visible reaction to keyboard input, console switching apparently not working, CTRL-ALT-BACKSPACE no visible effect, HD LED switches off and on only sporadically for very short time). This happens regardless of booting the normal or the rescue image. The last visible output from the rescue boot says something about init-bottom, but I can't see if it succeeds or not.
The installation process itself fell back to text console, which was fine for me.

I would like to get the machine booting normally, text only would be fine as the machine will run headless anyway, remote X login would be considered a bonus.

Any ideas?

---

### Post by EmilyFromFarAway on 2011-01-04
The problem was the kernel mode setting of the Radeon RV100. The machine is booting fine after I disabled KMS.

---

