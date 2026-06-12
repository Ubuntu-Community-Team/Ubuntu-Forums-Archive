---
title: "natty monospace font not monospace"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2011-05-01
I did a new install of 11.04 on a desktop PC. My problem is that selecting "monospace" font in any application (e.g. terminal preferences) does not result in a monospace font. If I choose a specific monospace font such as Liberation mono, it works fine. But some apps specify something like "monospace 10" and expect this to be mapped to a monospace font. This worked OK in Ubuntu 10.10 and previous, but apparently not in 11.04. Selecting a specific monospace font in the appearances utility also makes no difference. So what is wrong and how can I fix this? Where is the mapping of "monospace" to a specific font being done?

---

### Post by kornelix on 2011-05-02
This is related to the message "Fontconfig error: Cannot load default config file" which is output when many programs are started, e.g. the command "gedit" or "firefox" from a terminal window will output this error. 

I reinstalled "ubuntu-desktop" and rebooted to make sure I had not removed something necessary. No change. This smells like a real problem in Natty.

---

### Post by dkrig on 2011-05-03
Same problem here, but with italic - [http://is.gd/cHHmHC](http://is.gd/cHHmHC)
Appeared after update to 11.04.

---

### Post by kornelix on 2011-05-18
I did a complete re-install and the problem went away. I don't know why, but presumably I made a mistake.

---

