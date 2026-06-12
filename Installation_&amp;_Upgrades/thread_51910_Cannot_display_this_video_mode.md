---
title: "Cannot display this video mode"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by gmalac on 2005-07-25
Hi!
I installed an integrated KVM 2-Port Switch from Linksys in order to drive two pc with only one set of keyboard, mouse and video display (my home desk is too small for two screens).
One PC is a Windows machine and the second Ubuntu 5.04. My problem is that the Ubuntu PC stops after trying to start GDM with the error message "cannot display this video mode".
Is there a way out of this? Could I re-run the config/setup somehow? (before using this LCD flat screen my Ubuntu PC had a CRT Dell monitor).
Thanks for any help

Guy

---

### Post by damonw5 on 2005-07-25
[QUOTE=gmalac]Hi!
I installed an integrated KVM 2-Port Switch from Linksys in order to drive two pc with only one set of keyboard, mouse and video display (my home desk is too small for two screens).
One PC is a Windows machine and the second Ubuntu 5.04. My problem is that the Ubuntu PC stops after trying to start GDM with the error message "cannot display this video mode".
Is there a way out of this? Could I re-run the config/setup somehow? (before using this LCD flat screen my Ubuntu PC had a CRT Dell monitor).
Thanks for any help

Guy[/QUOTE]
 The error is probably coming from your monitor, not Ubuntu.

Boot your Ubuntu machine in "recovery mode" (it's one of the options in the boot menu).
You will be brought (eventually) to a root terminal. Type "sudo dpkg-reconfigure xserver-xorg" and follow the prompts. If you aren't sure about a question, choose the default answer by pressing enter.

Let us know if this helps.

---

### Post by gmalac on 2005-07-26
Indeed it helped a lot thanks!

Actually I was not able to manage this "recovery mode". What I did was CTRL-ALT-F1 when the monitor displayed the error message, which brought me back to the console. From there, I could do "sudo dpkg-reconfigure xserver-xorg"

Thanks again, it works now and I am very happy!

Guy

---

### Post by CK0ne on 2005-08-10
I had the same problem when I installed Ubuntu while using a different monitor recently.  Try this link to this forum. . .it solved my problem: [COLOR=Blue][Cannot Display This Video Mode](http://ubuntuforums.org/showthread.php?t=51910&highlight=cannot+display+this+video+mode) [/COLOR] 

-CK-

---

