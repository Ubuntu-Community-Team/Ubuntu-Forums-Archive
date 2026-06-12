---
title: "Ubuntu Graphics wont start"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by jamj90 on 2012-01-31
Hi all, 

I am having a problem after installing some upgrades that I am hoping someone can help me with. After installing some updates when I turn on my computer instead of going to my login screen I just see a black screen a bunch of commands that seem to be starting up the system with one [fail] listed next to :stopping automatic crash report generation". The computer stays at this point until I manually press the power button or ctrl alt delete. I can log in using ctl alt f2 but from there "startx" and " sudo gdm" both fail for different reasons. startx for fatal error "no screens found" while "sudo gdm" displays maximum number of X display failures reached: check x server log for details. They do seem to be similar but I wanted to get the exact wording out there. 
Thank you very much any help is greatly appreciated.

---

### Post by gordintoronto on 2012-01-31
What video card and what monitor?

Can you run OK from a LiveCD or LiveUSB drive? If not, you probably have a hardware problem.

---

### Post by jamj90 on 2012-01-31
> **gordintoronto said:**
> What video card and what monitor?

Can you run OK from a LiveCD or LiveUSB drive? If not, you probably have a hardware problem.

The problematic computer is a laptop, the screen is attached to the computer and the video card is a Nvidia geforce.

Yes I can run ok from a live cd as well as liveUsb. In addition this particular computer has been running ubuntu for years with few issues and none that can be resolved. This problem originated from a routine update a couple of days ago

---

### Post by UltimateCat on 2012-01-31
I recently lost all of my graphics after I installed updates.

It was such a mess that I had to go to Linux for help.

I was told that " you appear to have  fglrx installed but not config to use it."

Try running 
```
 <thenameofyourcard> config --initial

```

As an example mine was:
ati config --initial

Reboot and see if the Catalyst Control Center will start. ( Which is found in SYSTEM> PREFERENCES>

If you get this message:
NO ATI driver is installed or ATI driver is not functioning properly then

There is something about the:
 /etc/X111/xorg.conf file that you have to get help with configuring it. Or placing that file inside of another file xorg.conf.backup-xxxxxxxxxxxx(everyone's file #'s are different.

This file needing  configuration may not be your solution but it was in my case.  I have shared my experience with you in the hope that it can be a  help to you.

There are members much more skilled than I in this forum that can help you as well.
I have faith in them as they have helped me a great deal and I wish you the best.

---

### Post by jamj90 on 2012-02-01
> **UltimateCat said:**
> I recently lost all of my graphics after I installed updates.

It was such a mess that I had to go to Linux for help.

I was told that " you appear to have  fglrx installed but not config to use it."

Try running 
```
 <thenameofyourcard> config --initial

```

As an example mine was:
ati config --initial

Reboot and see if the Catalyst Control Center will start. ( Which is found in SYSTEM> PREFERENCES>

If you get this message:
NO ATI driver is installed or ATI driver is not functioning properly then

There is something about the:
 /etc/X111/xorg.conf file that you have to get help with configuring it. Or placing that file inside of another file xorg.conf.backup-xxxxxxxxxxxx(everyone's file #'s are different.

This file needing  configuration may not be your solution but it was in my case.  I have shared my experience with you in the hope that it can be a  help to you.

There are members much more skilled than I in this forum that can help you as well.
I have faith in them as they have helped me a great deal and I wish you the best.
It doesn't seem to recognize my command. I am going to try backing everything up if I can and then do a fresh install. Thank you for your help and well wishes.

---

