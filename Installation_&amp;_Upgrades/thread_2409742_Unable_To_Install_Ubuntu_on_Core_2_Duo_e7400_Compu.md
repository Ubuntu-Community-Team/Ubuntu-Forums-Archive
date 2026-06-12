---
title: "Unable To Install Ubuntu on Core 2 Duo e7400 Computer"
date: 2019-01-06
forum: Installation &amp; Upgrades
---

### Post by yuvarajvelmurugan on 2019-01-06
I have a computer with below hardware running windows 7 operating system.

CPU: Intel® Core&#8482;2 Duo Processor E7400 (3M Cache, 2.80 GHz, 1066 MHz FSB) processor

RAM: 4 GB

I downloaded Ubuntu desktop 18.04 and used RUFUS application to create bootable USB.

When i booted the computer with usb boot mode it shows a blank screen with 2 icons at the bottom.

Then i pressed "e" key and it showed below UBUNTU boot options:


[LIST]
[*=left]Try Ubuntu without installing. 
[*=left]Install Ubuntu
[*=left]Check disc for defects
[*=left]Test memory
[*=left]Boot from first hard disk
[/LIST]

I choose "Install Ubuntu" and hit enter.

Then it showed a blank screen with cursor blinking on top left corner of the screen for a long time and nothing else.

I again rebooted the machine and this time i choose "Try Ubuntu without installing" and hit enter.

This time also it showed a blank screen with cursor blinking on top left corner of the screen for a long time and nothing else.

Could anyone suggest me a solution to resolve this problem and install ubuntu on this computer.

---

### Post by TheFu on 2019-01-06
Google for "ubuntu install {specific model of computer}"
For example, "*ubuntu install dell 1558*"

This will help you to find any work-arounds for installing onto specific, odd, hardware.  Often the issue is due to a GPU that needs a little help until proprietary drivers can be loaded post-install.  Some HP and Acer machines seem to have lots of issues, but not all of them do.  Most of the time, everything just works.

---

### Post by kurt18947 on 2019-01-06
If you're trying to install the 'normal' Ubuntu on that machine, I'd suggest one of the less resource intensive 'spins' such as Xubuntu or Lubuntu. I have a Core2duo laptop and Xubuntu works pretty well on it. Lubuntu is working on a QT version, I've created a live USB of the QB version and it and it seems to work pretty well. You may need to start with the 'nomodeset' option that can help with video problems on boot.

---

### Post by oldfred on 2019-01-06
What video card?
As kurt18947 suggests you may need nomodeset if nVidia or other video issues.
Press enter on the accessibility icons at bottom of screen then f8 to get screen to add boot parameters.

---

### Post by TheFu on 2019-01-06
Excellent advice - above by Kurt and oldfred, as usual.

After you get passed the screen issue, any of the lower-end DEs will be more responsive on that system than the normal, heavy, Ubuntu GUI.  Xubuntu (xfce4), Lubuntu (lxde/lxqt), Mate, should perform well.  Unity and Gnome3 are just too heavy, IMHO.  You can install one disto, then change the DE, or remove the DE for a lighter pure-WM experience.   

Core2 Duo systems have lots of life left in them. They were an impressive jump in capabilities for their time.

---

