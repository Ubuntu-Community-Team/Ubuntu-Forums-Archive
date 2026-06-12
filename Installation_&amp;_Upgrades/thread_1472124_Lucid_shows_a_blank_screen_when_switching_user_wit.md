---
title: "Lucid shows a blank screen when switching user with ati card &amp; desktop effects on"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by tanoloco on 2010-05-04
Hello,

just want to share my experience,  I don't know if this is the correct place to post and I cannot find a proper thread to add this info. This problem is already reported in testing threads but it seems to me that I cannot reply to them maybe because now Lucid is not in testing but it's released..

However I've installed the final release of Lucid 10.04 on my pc with:
- Motherboard -> Intel D850GB (Garibaldi)
- cpu                -> Intel Pentium 4 - 2.0 GHz
- graphic card  -> ATI Radeon 9250 128 MB DDR


**[problem]**
1. logged in as admin user
2. try to switch to any other user  by pressing "switch user" under the menu of the right icon of the top  panel next to the logged user-name
3. got a blank screen sometmes with with no pointer at all. alt+f7 no effect, ctrl+alt+f7 no  effect, ctrl+alt+f1/f2 etc sometimes got a console mode sometimes not.


**[bug report]**
I joined this issue
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/529882](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/529882)
and sent there this info


**[workaround]**
[COLOR=DarkGreen]
_case A: you don't care about desktop effects_[/COLOR]
1. turn-off your desktop effects
2. reboot
3. it might be solved
4. if not type on a terminal:
```
$ sudo chmod +w /boot/grub/grub.cfg
$ gksudo gedit /boot/grub/grub.cfg
```find a line in your desired menuentry like:
```
linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=95595d29-44d9-4b57-9b02-cbb5c5f127aa  ro   quiet splash
``` and add nomodeset at the end to obtain something like
```
linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=95595d29-44d9-4b57-9b02-cbb5c5f127aa  ro   quiet splash nomodeset
```save, close and then type in the terminal
```
$ sudo chmod -w /boot/grub/grub.cfg
```5. reboot
6. it might be solved


[COLOR=DarkGreen]_case B: you do care about desktop effects_[/COLOR]
This is more complex:
1. from a terminal install ati-drivers
```
$ sudo apt-get install xorg-driver-fglrx
```2. reboot
3. completely remove using synaptic any package with fglrx.
In my case:
> fglrx
fglrx-kernel-source
xorg-driver-fglrx
fglrx-amdcccle
fglrx-modaliases(I know that I've installed xorg-driver-fglrx just now but I need some  dependencies it install with the above command but I cannot understand  which ones .. so I first install it with all the dependencies and then I  remove it .. ok?)
4. reinstall:
> libgl1-mesa-glx
libgl1-mesa-dri
xserver-xorg-video-ati 5. reboot
6. it might be solved
7. if not (as in my case) type in a terminal:
```
$ gksudo /etc/X11/xorg.conf
```and  write inside the (blank) document:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode"       "8"
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
EndSection
```save and close.
8. turn-on your desktop effects and try to switch user and it might be  ok.


 Sometimes when closing the session I get a prompt asking me to enter  the password rather then getting the gdm gui .. on this prompt I cannot  click on the bottom buttons (something as "change user" "leave a  message" and so on ) but I can still reach them by using the alt button.

Later on I got sometimes the blank screen back when  closing the switched user session.
I solved it:
9. changing the above conf codes in xorg.conf from Option "AGPMode" "8"  to Option "AGPMode" 1"
10. completely removing the gnome-screensaver package as suggested here
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/546578](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/546578)


It seems it works now, with all desktop effects activated and switching users and closing sessions.
**The only thing I still don't know is which screensaver can I use if removing gnome-screensaver?**

Hoping this can help! Any suggestion about the screensaver would be appreciated :)
cheers

---

### Post by tanoloco on 2010-05-04
I'm sorry ... but this is not a definitive solution: the probem of the blank screen keeps going from time to time when switchg user .. so my post is not valid :(

---

