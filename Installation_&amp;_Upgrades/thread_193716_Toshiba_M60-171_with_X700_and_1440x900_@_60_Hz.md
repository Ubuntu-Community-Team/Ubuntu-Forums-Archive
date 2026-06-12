---
title: "Toshiba M60-171 with X700 and 1440x900 @ 60 Hz"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Bauke on 2006-06-10
Just to let you know I managed to install Ubuntu Dapper on my Toshiba M60-171. It has an ATI videocard X700 WXGA with resolution 1440 x 900 @ 60 Hz.

Here's what happened:

1. After booting the live CD I heard startup sounds but there was just a black screen.

2. To get some needed files I configured the network in terminal mode (switch with Ctrl-Alt-F2) for a static IP address with files
 ```
sudo nano -w /etc/network/interfaces
``` and ```
sudo nano -w /etc/resolv.conf
```
3. After restarting the network with ```
sudo ifup eth0
``` I could fetch some needed files, as explained in [https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)

4. With all files installed, switch back to the (black screen) GUI with Alt-F7, and restart it with Ctrl-Alt-Backspace. Now finish the installation from <System>, <Preferences>, <Install>

5. After installing rebooting is done automatically and you're again ending up in a black screen though startup sounds are there. All you have to do is following the wiki [https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25) once more. 

6. Now you should be able to boot into GUI mode


Feel free to send me any corrections and/or additions

---

### Post by Enigmatic on 2006-06-13
I tried this to get my X700 working, but what I'm not sure about is that last step of the ATI installation instruction. It says to reboot, but if I did that I would lose all my settings as they are in RAM. 

I did try the fglrxinfo, but as expected due to not rebooting it hadn't updated and showed the Mesa driver.

I tried restarting X as you had documented, and I could hear it restarting, but the GUI never came up :(

---

### Post by Enigmatic on 2006-06-14
Never mind, I got it working. Just had to use the telinit 1 and telinit 2 commands to "reboot" all the procsses instead of physically rebooting.

---

