---
title: "Laptop keyboard not recognised on upgrade 9 to 10"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by doktoravalanche on 2010-05-16
I tried to use the automatic upgrade to version 10 last night on my Acer Aspire 8930G. Everything seemed to work fine until I got to the reboot.

At the reboot it tells me that it is running in low resolution mode because the nvidia drivers have been removed. That is fine except I cannot hit the enter button to accept the message either using the laptop keyboard or by restarting and using a USB keyboard.

I have a dual boot with windows and I'm averse to just reinstalling ubuntu because there is some data which would be annoying to lose.

Can anyone help get my keyboard up and running so I can move on with the upgrade please.

---

### Post by Catharsis on 2010-05-16
Can you boot into recovery mode? Just hold down Shift while booting to enter grub, and then select the recovery mode kernel.

---

### Post by doktoravalanche on 2010-05-16
No, I cannot. I can use the keyboard to select from Ubuntu or Windozy and can boot to windozy fine.

But shift does not get me into the safe mode.

I can use a Live CD to boot into v10 and obviously v9 worked fine. Is there a way I can fix the upgrade, or use the Live CD to fix the "broken" install on my hard drive without having to re-install the whole OS?

---

### Post by techbrainless on 2010-05-16
Me too having the same issue and i have post  a question to the forum
[http://ubuntuforums.org/showthread.php?t=1484716](http://ubuntuforums.org/showthread.php?t=1484716)

am going to try the recovery option and reply you

---

### Post by doktoravalanche on 2010-05-16
Did you try a live CD like me. The live CD worked fine. I could use the keyboard and mouse. (but I did not check the laptop trackpad which has never been recognised).

---

### Post by techbrainless on 2010-05-16
frankly i did not try live cd   ( currently I am away from my laptop) , but i ll try and reply you back as soon as possible.

---

### Post by techbrainless on 2010-05-16
Hi I have tried Live CD , Everything went fine with me , keyboard and mouse are working properly .........
so what the suggestion to fix such issue ............

---

### Post by techbrainless on 2010-05-16
Hi Catharsis,

I have boot using recovery mode (off course it is CLI), the keyboard is working for me in this mode  , but what is the next step i have to do to fix this issue.............

---

### Post by Catharsis on 2010-05-16
> **techbrainless said:**
> Hi Catharsis,

I have boot using recovery mode (off course it is CLI), the keyboard is working for me in this mode  , but what is the next step i have to do to fix this issue.............

Interesting. What happens when you type "startx"?

It'd be a good idea to upgrade your system while you're there and see if that does anything.
```
sudo apt-get update && sudo apt-get upgrade
```

You can also try adding some boot parameters:
1) Hold down Shift while booting to enter the grub menu.
2) Press 'e' to edit. Remove "quiet splash". Ctrl+x to boot.

Also replace "quiet splash" with "nomodeset" or "noacpi" or "xforcevesa noapic noapci nosplash irqpoll".

Honestly, I think you might need to do a clean install. If this happens, you can backup all your stuff from the LiveCD if you need to.

---

### Post by techbrainless on 2010-05-17
> **Catharsis said:**
> Interesting. What happens when you type "startx"?


when i type startx , i will be logging to ubuntu GUI without authentication (not asked to provide username and password) but the same problem is happening (keyboard and mouse are not recognized) ?????????

---

### Post by techbrainless on 2010-05-20
Any suggestion...............

---

### Post by Catharsis on 2010-05-20
Did you try the rest of my suggestions??

---

### Post by filipe.matias on 2010-05-21
A Solution:
 
Step 1: Hold the "shift" button while booting, until the "GNU GRUB" appears;
 
Step 2: Select ubuntu in recovery mode, and press enter. Wait until the Recovery 
Menu appears;
 
Step 3: Select "root" and press enter. A comand prompt will appear right below the blue screen. Something like this: " root@ubuntu:~# ";
 
Step 4: Write "startx" and press enter. Ubuntu will enter the root session;
 
Step 5: Now go to System->Preferences->Keyboard. A screen  called Keyboard Preferences will appear;
 
Step 6: Go to "Layouts" tab;
 
Step 7: Select you keyboard;
 
Step 8: Click "Apply System-Wide...";
 
Step 9: Restart ubuntu and that's it!;)
 
Viva Portugal!:D

---

### Post by techbrainless on 2010-05-27
> **filipe.matias said:**
> A Solution:
 
Step 1: Hold the "shift" button while booting, until the "GNU GRUB" appears;
 
Step 2: Select ubuntu in recovery mode, and press enter. Wait until the Recovery 
Menu appears;
 
Step 3: Select "root" and press enter. A comand prompt will appear right below the blue screen. Something like this: " root@ubuntu:~# ";
 
Step 4: Write "startx" and press enter. Ubuntu will enter the root session;
 
Step 5: Now go to System->Preferences->Keyboard. A screen  called Keyboard Preferences will appear;
 
Step 6: Go to "Layouts" tab;
 
Step 7: Select you keyboard;
 
Step 8: Click "Apply System-Wide...";
 
Step 9: Restart ubuntu and that's it!;)
 
Viva Portugal!:D

I have exactly followed the above steps but still the same problem exists............

> **filipe.matias said:**
> 

Step 7: Select you keyboard;

By the way I have Toshiba laptop ,  Model Type : Qosmio .

I have selected satellite model , because Qosmio model is not in the list under Toshiba vendor.......

Do you think this causes the problem ........... and if so , what is the solution for this ....

---

### Post by techbrainless on 2010-05-29
Any suggestion................

---

### Post by techbrainless on 2010-05-30
Any  suggestion................

---

### Post by techbrainless on 2010-05-31
Hi All , 

I have decided to format my laptop and make fresh installation instead of upgrade (because i have stuck in the upgrade issue for long time) ...


So No Problem I am facing now , laptop keyboard and mouse are recognized and they are working properly....................

---

