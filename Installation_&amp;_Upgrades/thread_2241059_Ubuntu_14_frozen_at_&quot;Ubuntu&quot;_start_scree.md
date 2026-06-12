---
title: "Ubuntu 14 frozen at &quot;Ubuntu&quot; start screen"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by carlos-5 on 2014-08-23
On an IMB thinkpad that was running Ubuntu 12, I updated to 14 and installation seem to go fine.  When it was finally time to reboot into 14 (yeaaa new toy to play with) it stays at the Ubuntu splash screen with the 5 progess dots and just endlessly cycles over the dots, thats as far as it gets.  If I hit delete it takes me to the text screen with everything OK.

Any suggestions??

---

### Post by lah7 on 2014-08-24
Welcome to the forums. This sounds like an issue with the graphics. Could you please tell us what the last few lines are prior to when it hangs?

To clarify if this is a graphics issue, press **CTRL+ALT+F1** to switch to the terminal when it 'hangs' and type
```
sudo service lightdm restart
```
and/or
```
startx
```
to see if the graphical interface appears. If it does not, this is bound to be an issue with X.org (the display server) or lightdm (the display manager) and presumably a problem with the graphics drivers. Was any proprietary drivers used prior to the upgrade?

---

