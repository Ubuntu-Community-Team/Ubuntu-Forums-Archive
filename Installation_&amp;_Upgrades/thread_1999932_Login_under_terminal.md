---
title: "Login under terminal"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by LaJuan on 2012-06-08
Hi,

Is there a way to login terminal before the regular login? Reason, I noticed this NVIDIA driver for the Quadro FX 3400 states in the read me file that I need to shut down xorg and enter terminal to install the driver. I ran shut sudo lightdm to shut down my display and my screen goes blank. I can type all day put it's not the terminal. I also tried crtl atl F1-F6 to get terminal to pull up but, no luck. I also read that if I log into my computer at the beginning under terminal xorg will not start and then I can install the driver. I'm running 12.04 on a Dell Precision 370, 4GB RAM, two 400GB HDD.:confused::confused::confused:

---

### Post by papibe on 2012-06-08
Hi LaJuan.

Boot normaly, when you get to the graphical login screen, press Ctrl+Alt+F1

Then login in text mode and kill lightdm there.

Regards.

---

### Post by LaJuan on 2012-06-08
Thanks!!!!!!!!! I don't know if it's my wireless kyb but, it's not working. I even tried up to F6 and still got nothing. I'm going to try it from a usb kyb and see what happens!!!!

---

### Post by papibe on 2012-06-08
If that's not working, boot into recovery mode.

You'll be presented with a menu, choose boot normally. That should take you to a text mode login.

Regards

---

### Post by LaJuan on 2012-06-09
Ok,

I get in that menu and when I pick normal login, it goes back to the regular login. So I go back and pick root and then it goes to terminal screen. I type sudo login. It then goes to login:. Next I enter my user name just like it is spelled on the normal login and hit enter and then it ask for my PW and enter it but, it keeps coming up incorrect login. I think I'm missing something some where but, no idea on where the error could be.

---

