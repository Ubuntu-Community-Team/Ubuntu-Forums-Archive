---
title: "Problem with 2.6.35-28"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by carkaci on 2011-03-18
I have recently update my kernel from 2.6.35-27-generic to 2.6.35-28-generic by using Update Manager.
After restarting, my screen flashed two or more times, than failed to start XWin mode. It started in tty1 console mode. But, I have still worked with the previous kernel successfully. 

Extras: IMac i7 (64 bit Ubuntu is used).

Best regards.

---

### Post by crunchytheory on 2011-03-18
> **carkaci said:**
> I have recently update my kernel from 2.6.35-27-generic to 2.6.35-28-generic by using Update Manager.
After restarting, my screen flashed two or more times, than failed to start XWin mode. It started in tty1 console mode. But, I have still worked with the previous kernel successfully. 

Extras: IMac i7 (64 bit Ubuntu is used).

Best regards.
Seeing the same issue (on my mid-2008 24" iMac), although going back to kernel -27 did not fix the problem.

I had to use recovery -28 kernel and reset the graphics to default settings to fix it. I think it is nvidia graphics-related. The problem comes back when I try to enable my second external monitor as a separate x screen.

---

### Post by z80 on 2011-03-19
having issues too! my dell all the sudden doesnt want to recognize the onboard ethernet.  rebooted into earlier kernel and now im back online. backing up all essentials and will do clean install in a week or two.  I have been fooling with calibre and ushare alot recently and trying to get my 1000mb/s out of the onboard ethernet, but i dont think these affected it because the earlier kernel works just fine...

---

### Post by szemy on 2011-03-28
My lenovo doesn't even boot... It hangs with this kernel:( Just updated it. Guess will hold out until the next update, because the 27 kernel works flawless. If there is anything I can do to help debug the problem please tell me what I should do.

---

### Post by Dans564 on 2011-04-09
I have the same issue with 2.6.35-28.  the previous kernel (i'm on mint 10) 2.6.35-22 boots without any issues.  I as well believe this to be an issue with the nvidia driver.  Im using nvidia driver 260.19.06 on a pair of GTX 460's.

---

### Post by Dans564 on 2011-04-09
bump...

---

### Post by szemy on 2011-04-10
Do you absoultly need the new kernel?
Why don't you use the older and wait until there is a new?
If the problem stays you should file a bug report.
Mine is working fine with 28, seemed a one off problem.

---

### Post by Dans564 on 2011-04-12
i can just stay where i am but the kernel should work.  Also, saying its "one off" is flawed because there 5 people in this thread with what seems to be the same problem

---

