---
title: "Black screen after bootup of new 12.04 install"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Ububtubobl on 2012-05-24
I tried a fresh install of 12.04 on my compac presario f700 laptop this afternoon. After boot up it went to a black screen. It took 3 tries to install 64 bit version (kept freezing up). I finally re-installed 10.04 which went fine. Any suggestions?

---

### Post by carl4926 on 2012-05-24
At the grub menu press F6 and select nomodeset
hit enter
if that gets you to the desktop
install the nvidia driver and reboot

---

### Post by raja.genupula on 2012-05-24
what kind of VGA drivers you got ? 
-- at grub menu choose recovery mode 
-- then go to failsafeX mode
-- open system settings > Additional Hardware > 

it lists required drivers for you by default , install from there and give a restart .

all the best .

---

### Post by darkod on 2012-05-25
> **raja.genupula said:**
> what kind of VGA drivers you got ? 
-- at grub menu choose recovery mode 
-- then go to failsafeX mode
-- open system settings > Additional Hardware > 

it lists required drivers for you by default , install from there and give a restart .

all the best .

This wouldn't work since the OP already reinstalled 10.04.

You should try to boot with your 12.04 cd first in live mode (Try Ubuntu) and see whether that loads fine. If it doesn't, try the nomodeset parameter as suggested above. You have more details how to do it here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Ububtubobl on 2012-05-28
I have reinstalled 12.04 but can not select "nomodeset" at f6 because no menu is presented at f6. Driver is nvidia. If I boot from a live cd it  works. I have tried the workaround at the forum  link above but "failsafex" just reloads default hardware . Thanks to everyone for their help but so far it still won't boot from the hard drive.

---

### Post by darkod on 2012-05-28
When the system is already installed there is no F6 option, if that's what you are talking about. In the grub2 menu, when the ubuntu entry is highlighted, you need to press 'e' for edit, and then add the nomodeset in the line starting with linux, towards the end before 'quiet splash'.
Press Ctrl + X to boot.

---

### Post by Ububtubobl on 2012-05-29
Thanks for the suggestion. System still booting to black screen. The forum seems to indicate nvidia cards not liking Ub 12.04. Maybe I should stay with 10.04 a little longer.

---

### Post by Dreskills on 2012-06-25
I am having the same issue. Nomodeset is not working for me.  I read something about booting in safe mode the install the Nvida drivers however I do not believe my PC will do that.
 
I refuse to let this beat me but I don't know what else to try. I am completely new to Ubuntu but I follow good directions.

---

### Post by rmason9 on 2012-06-25
I am also having this problem and have tried selecting nomodeset but it cause the system to boot to a frozen purple hashed-up screen.  I'm running a Compaq Presario V6000 which says I have a generic display adapter.  Would downloading a nVidia drive do me any good?

---

### Post by carl4926 on 2012-06-25
There is a bit of an article here
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

