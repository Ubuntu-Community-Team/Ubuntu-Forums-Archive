---
title: "Screen went black after upgrading to 10.10"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by vilandraa on 2010-12-27
Hello,

I have upgraded my system from 10.04 to 10.10 and know after rebooting the screen is just blank. It does not respond to anything. I have tried to boot with a live cd or windows cd but all I see is a blank screen. However, the computer is working fine, hard disk light is on, i can hear the log in sound also but the screen is just black. can anyone help me about this?

---

### Post by garvinrick4 on 2010-12-27
> **vilandraa said:**
> Hello,

I have upgraded my system from 10.04 to 10.10 and know after rebooting the screen is just blank. It does not respond to anything. I have tried to boot with a live cd or windows cd but all I see is a blank screen. However, the computer is working fine, hard disk light is on, i can hear the log in sound also but the screen is just black. can anyone help me about this? If it is a WUBI install, installed as a folder inside of Windows put the title WUBI
in your Title line. You will get Wubi users to help you then.

---

### Post by vilandraa on 2010-12-27
It is not a wubi install, i have dual boot. Ubuntu and windows are in different partitions. The problem started after I upgraded to 10.10. Now I can not do anything, I can not even re-format cause the screen is just blank but the monitor light is also on.

---

### Post by karthick87 on 2010-12-27
On booting hold down the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset"  without the quotes - then press **CTRL + X** to reboot.

---

### Post by vilandraa on 2010-12-27
To make sure monitor is working properly, I connected it to my laptop but again I could not see anything. Ubuntu somehow messed up with my monitor. Then I did the simplest thing I can do: unplug and plug the monitor, which turn out to solve the problem for now. I am not sure if this going to happen again so I will get rid 10.10 and install 10.04. This issue might be related to the shutdown and reboot problem that I read in some threads here.

---

### Post by vilandraa on 2010-12-27
karthick87 thanks for your answer, if this happens again I will try what you wrote.

---

### Post by karthick87 on 2010-12-27
You are welcome :)

---

### Post by sikander3786 on 2010-12-27
@**Vilandraa**:

Which graphics card is there? If any proprietary drivers were installed previously on 10.04, removing and re-installing might help.

Or, just reconfiguring the graphics might also solve the issue here. 10.10 should work if you want to use it ;-)
Applications > Accessories > Terminal:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

If there was an older xorg.conf, that might be causing the problems here. So rename it and reconfigure your graphics. Just follow the 3 commands above.

---

### Post by Marky Mark on 2010-12-27
I had the same problem, I found the previous kernels were ok.  If you press the esc key when the grub screen pops up (be quick, mine only stays on for 3seconds) you can select which kernel to use, I then deleted the newer ones using System>Administration>Synaptics Package Manager .

Good luck.

MyM

[http://ubuntuforums.org/showthread.php?t=1650737&highlight=kerrnel](http://ubuntuforums.org/showthread.php?t=1650737&highlight=kerrnel)

---

