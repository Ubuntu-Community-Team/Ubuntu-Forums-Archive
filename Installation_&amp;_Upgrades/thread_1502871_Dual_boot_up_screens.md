---
title: "Dual boot up screens"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by tuffs on 2010-06-06
After some difficulty (had to install Wubi 9.10 patch), I have finally installed 10.04 (from a CD) within Windows XP. However on boot up I get two boot up screens asking me to choose Windows XP or Ubuntu. The first screen gives you two choices (XP or Ubuntu) but only gives you one second to choose before booting into XP as the default OS. If you hit the Ubuntu button within the 1 second, it takes you to the second screen (GNU Grub). Is there any way to get rid of the first screen, or lengthen the time period to choose which OS to use. The second screen (GNU Grub) gives you 6 seconds to choose (as well as a wider range of options) so this screen is less of a problem. But why do you need two boot up screens;and can I get rid of the first screen?  Thank you in anticipation.
:confused: IT

---

### Post by davidmohammed on 2010-06-06
sounds like you've got two lots of grub interacting...

in terms of the timeout

from your first - choose ubuntu

then in the terminal

sudo nano /etc/default/grub

edit the timeout intervals GRUB_TIMEOUT to say "10"

save

then run sudo update-grub

---

