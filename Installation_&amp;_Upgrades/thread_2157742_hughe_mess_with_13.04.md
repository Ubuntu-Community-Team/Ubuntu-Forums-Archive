---
title: "hughe mess with 13.04"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by rogerdv on 2013-06-26
Im trying to install 13.04 since yesterday and propblems have gone from simply being unable to install many packages I need to totally mess my configuration. When I was trying to install catalyst 13.6 today, Unity stopped working. I simply got the desktop. Tried to fix it removing catalys, didnt worked. Reinstalled the whjole system and the problem still was there. Googled a bit and found the dconf reset solution, but it only messed the system mucho more: now the login screen has been shifted to the right and the password edit box starts on the right edge of my screen and ends in the left edge. If I log in, I just get garbage, random white and black boxes. Im thinking to go back to 12.04, but first I need to solve this disaster, any idea about how to clear the configuration?

---

### Post by cincinnatus13 on 2013-06-26
The only thing I can suggest is to get to a terminal and do sudo sh /etc/X11/Xreset
This should reset whatever X settings to normal and you can go from there after that.

---

