---
title: "Install Lucid in old 800x600 monitor"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by sergiodlc on 2010-09-20
Hi:

I'd like to install Ubuntu 10.04 but unfortunately I have and old Samsung low res (800x600) monitor and when I boot with the live Lucid USB pendrive the screen goes crazy and remains there forever. Any suggestion?

Sergio

---

### Post by lukeiamyourfather on 2010-09-20
Try the alternate install disc which has a text based installer. It should do the trick.

---

### Post by sergiodlc on 2010-09-20
Thanks for your quick reply. I'm afraid this would be very hard since I'm behind a dial-up internet connection and it would take forever to download the alternate disk. Any other solution?

---

### Post by lukeiamyourfather on 2010-09-20
When booting from the disc hold shift. It will ask if you want to boot with graphics or not. Say "n" for no. Then it will bring up a menu asking what you want to do, select the option to install Ubuntu. This might work, it might not. It will still use the graphical installer. If that doesn't work then you'll probably need the alternate installer disc. Not sure how it works in Cuba, but you can order the alternate install Ubuntu discs through the mail. Or use the minimal install disc and download only the packages you need instead of the complete ISO.

---

### Post by lukeiamyourfather on 2010-09-20
Here's the minimal install disc.

[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso)

Only 13MB or 14MB and then it downloads only what you actually install during the installation.

---

### Post by sergiodlc on 2010-09-21
Thanks, I'll try this ASAP.

---

### Post by sergiodlc on 2010-09-28
This is how I get to solve my problem. First I booted from the Lucid cdrom. After loading Lucid the screen became a mess because its default screen resolution is 1024x768. I typed ALT+F2 and when the launch app window appeared I typed "gnome-display-properties" and pressed ENTER. When the new window appeared y pressed TAB (to move to the resolution combo box) and then ENTER again. I then pressed ARROW DOWN once and ENTER. Although I couldn't see anything at that time, by doing this I was selecting 800x600 as the new screen resolution. Then I pressed ALT+A to apply changes and voila! Now I could see everything properly displayed.

Thanks all for your support!

---

