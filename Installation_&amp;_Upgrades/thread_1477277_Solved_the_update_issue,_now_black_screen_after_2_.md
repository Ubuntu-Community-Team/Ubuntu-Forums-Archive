---
title: "Solved the update issue, now black screen after 2 mins use"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Neo2 on 2010-05-08
Time for some feedback, especially to Craig who helped enormously! For all those suffering with boot up probs, this worked for me:

if 10.04 isn't showing after update, start 9.10 anyway and then hit escape to get to the menu. Select repair mode and hit enter. I had to do this some 3 times before 10.04 appeared in grub, but it eventually did. So started it and behold, the desktop arrived. I then did an immediate update on update manager and it replaced a huge number of files etc. Reboot. Now I can access 10.14!

But now I have a new problem. I use 10.04 for a few minutes (sometimes a few seconds)and it goes to black screen, frozen mouse pointer and what appears to be a frozen blinking cursor in the corner. Auto reboot after 30 seconds. This is getting really frustrating as you can imagine, so anyone have any clues as to how to progress? The first problem was solved on this forum so THANK YOU!

---

### Post by Catharsis on 2010-05-08
After a crash, please post your dmesg and xorg.0.log files.
```
cat /var/log/dmesg
cat /var/log/Xorg.0.log
```

When it crashes, does the keyboard still work? Capslock light? Can you get to a terminal through Ctrl+Alt+F1?

What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by Neo2 on 2010-05-09
Thanks. Can you tell me how to post my dmesg and xorg.0.log files? I've never heard of them!
The keyboard doesn't work and I haven't tried a terminal but will do so, although I suspect the answer is no as the keyboard is non functional. I have an nvidia graphics card but an older one (running a Dell pc Dimension 9200 with original graphics card still in it if anyone is clever enough to check what card is in it!).

---

### Post by Catharsis on 2010-05-09
While booting, try holding down Shift to get to grub. Then press 'e', and type "nomodeset" after "quiet splash". Then Ctrl+x to boot.

You can also try recovery mode again. In grub, select the recovery kernel (should be the second one). Select "boot normally". If that doesn't work, try "failsafeX".

---

### Post by Neo2 on 2010-05-10
Thanks. I can get to grub no problem, but I can't type anything into it, so not sure typing 'e' is going to help. I will try failsafeX, not done that. Question is, why would it fall over after such a short time period? any other clues as to what I'm doing wrong?

and I still don't know how to post the dmesg etc files you want to see!

---

### Post by Catharsis on 2010-05-10
Typing 'e' lets you edit the kernel parameters. Look at the bottom of the grub menu; all the commands are there.

Also, make sure your nVidia driver is installed (System->Administration->Hardware Drivers).

---

### Post by Neo2 on 2010-05-10
Thanks, will try this too. If the nVidia driver isn't installed then surely I wouldn't get any screen up to view at all? I can do this, it just crashes once up and running.

---

