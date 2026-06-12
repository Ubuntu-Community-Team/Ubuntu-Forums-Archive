---
title: "Lucid won't boot after today's updates"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Anthem on 2010-02-15
Anybody else having this problem?  Running the Lucid beta, and the system hangs during boot.  Right after grub initiates, I should see the silver ubuntu logo (which looks great, btw), I just get a mouse cursor in the center of the screen and a blinking text cursor in the top left.  Hitting CTRL-ALT-DEL, ESC, ALT-F4, CTRL-C, etc just results in on-screen gibberish.  

My only solution is to cold boot the computer, which then ends up with the same problem.

Anyone else experiencing this?

---

### Post by ranch hand on 2010-02-15
This sounds like a problem that is going around, has been for some time.  Why you are only getting it now seems strange.

Try booting through recovery.  You should just try the "return to normal boot" option.  Login (text login) and then, at the prompt, type "startx".  This will probably get you into your system.

---

### Post by zika on 2010-02-15
I would try the following:
Boot into recovery. Go to root console. Remove plymouth (aptitude purge plymouth). Exit, reboot...
But, that's only me...

---

### Post by scradock on 2010-02-15
> **Anthem said:**
> Anybody else having this problem?  Running the Lucid beta, and the system hangs during boot.  Right after grub initiates, I should see the silver ubuntu logo (which looks great, btw), I just get a mouse cursor in the center of the screen and a blinking text cursor in the top left.  Hitting CTRL-ALT-DEL, ESC, ALT-F4, CTRL-C, etc just results in on-screen gibberish.  

My only solution is to cold boot the computer, which then ends up with the same problem.

Anyone else experiencing this?
Where did you get the beta? Most of us are still running alpha2 ......

---

### Post by avb on 2010-02-15
i made dist-update karmic->lucid and having same problem. Installing/removing plymouth or  booting with nomodeset, or booting in a resque prompt doesnt change anything. 

Startup hangs somewhere before spawning getty and gdm. Something is clearing screen and i see only blinking cursor. Thats seems kms which is executed for a second time. 

Any ideas how to debug upstart?

---

### Post by avb on 2010-02-15
i made dist-update karmic->lucid and having same problem. Installing/removing plymouth or  booting with nomodeset, or booting in a resque prompt doesnt change anything. 

Startup hangs somewhere before spawning getty and gdm. Something is clearing screen and i see only blinking cursor. Thats seems kms which is executed for a second time. 

Any ideas how to debug upstart?

---

### Post by VMC on 2010-02-15
> **Anthem said:**
> Anybody else having this problem?  Running the Lucid beta, and the system hangs during boot.  Right after grub initiates, I should see the silver ubuntu logo (which looks great, btw), I just get a mouse cursor in the center of the screen and a blinking text cursor in the top left.  Hitting CTRL-ALT-DEL, ESC, ALT-F4, CTRL-C, etc just results in on-screen gibberish.  

My only solution is to cold boot the computer, which then ends up with the same problem.

Anyone else experiencing this?

Sound like a video issue. What video card do you have? nVidia, ATi?

Also when its in that state try "Alt+SysRq+k" (SysRq=print screen) Hold down all three at the same time and see if you have a gui login prompt. Are you using automatic or gdm login?

---

### Post by ratcheer on 2010-02-15
> **Anthem said:**
> Anybody else having this problem?  Running the Lucid beta, and the system hangs during boot.  Right after grub initiates, I should see the silver ubuntu logo (which looks great, btw), I just get a mouse cursor in the center of the screen and a blinking text cursor in the top left.  Hitting CTRL-ALT-DEL, ESC, ALT-F4, CTRL-C, etc just results in on-screen gibberish.  

My only solution is to cold boot the computer, which then ends up with the same problem.

Anyone else experiencing this?

 You are doing better than I. I have never been able to get Lucid to boot more than once after a successful installation.  Tim

---

### Post by trommas2 on 2010-02-16
> **VMC said:**
> 
Also when its in that state try "Alt+SysRq+k"

Thanks! That saved me from a reinstall :)

Push the three (actually 4, counting "Fn") a couple got me to gdm login, I usualy have automatic login.

---

### Post by Hacknslash on 2010-03-08
I too have this error with the blinking cursor in the top left corner of the screen. 
My workaround is simply to press [Enter], and the system boots normally and everything works fine.

If you need any hardware or system logs just mail me, I'll be happy to oblige.

---

