---
title: "[SOLVED] Upgrade Failed"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by mavuashire on 2007-12-22
I was trying to upgrade to version 7.10 from 7.4 but towards the end I got a message saying the Upgrade cannot go on. It had earlier complained about a few packages including ubuntu-minimal. It said the system maybe left in an unstable mode.

Then when I tried to reboot, I got a Kernel panic message. I tried restoring but nothing helped. I used the earlier version but they show up as version 7.10 and in a degraded state. In addition to this my sound is very low I have to play music with speakers on full blast to hear something.

Thanks for your help in advance

---

### Post by PmDematagoda on 2007-12-22
Could you please help me in understanding what you are trying to do?

Your upgrade did not succeed so you rebooted the PC. When you tried to boot the new kernel (2.6.22) it gave an error "Kernel Panic", but you were able to boot Ubuntu using the older kernel (2.6.20) but even that is messed up. 

Is that right?

---

### Post by mavuashire on 2008-01-05
Forgive me for taking a long time to update you. I was away.

Yes, it is true what you said. Now to make matters worse, because the older one was also messed, I tried to change the screen resolution. Now the screen is showing as 3 small windows overlapping each other and have a very poor resolution you cannot even read a thing.

I tried to reinstall the drivers but they wouldn't install. It fails saying it did not find a file it was looking for but found the one for openGL. "expected /usr/lib/libGL.so.1 but found /usr/local/lib/libGL.so.1." I tried moving the file to the other directory but that did not help. By the way I am using NVIDIA.

---

### Post by PmDematagoda on 2008-01-05
Boot Ubuntu in Recovery Mode, execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
after reconfiguration do:-
```
sudo startx
```
If the GUI works fine, post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by mavuashire on 2008-01-06
I tried to reconfigure but it says

"package 'xserver-xorg' is not installed and no info is available

it then gives infomation on how to examine the file and ti list contents

---

### Post by mavuashire on 2008-01-06
When I try to install something or upgrade it gives the following error:

dpkg: error processing ubuntu-keyring (--configure) subprocess post intalation script returned exit status 127
dpkg: dependency problems configuration of ubuntu-minimal: ubuntu-minimal depends ubuntu-keyring;   however: Package ubuntu-keyring is not configured yet;

---

### Post by mavuashire on 2008-01-06
I managed to reconfigure xserver-xorg and the GUI screen is back though it still has a wrong resolution. I think I can deal with that.

 Now the problem that remain is the keyring and minimal

---

### Post by Partyboi2 on 2008-01-06
try
```
sudo dpkg --configure -a
```

---

### Post by mavuashire on 2008-01-07
when i run  'sudo dpkg --configure -a,' I get the following message

Setting up ubuntu-keyring (2007.06.11) ...
gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: BC
gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: BC
dpkg: error processing ubuntu-keyring (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ubuntu-keyring

---

### Post by Partyboi2 on 2008-01-07
what happens if you try removing ubuntu-keyring and ubuntu-minimal then installing them again?

---

### Post by mavuashire on 2008-01-07
I removed the other file it was complaining about: libreadline.so.5. I did the update and upgrade which i think fixed the problem of keyring. I can install other packages as well now. I've just finished installing minimal and will see what the result will be.

Thanks for your help, but i think there is still more that i need to do.

---

### Post by Diabolis on 2008-04-06
I had the very same problem, so I deleted libreadline.so.5 too and for now seems like everything is fine.

---

### Post by ProxyGUTSY on 2008-06-21
To fix it type:

sudo rm /usr/local/lib/libreadline.*
sudo ldconfig


Hope this help:guitar::guitar:

---

