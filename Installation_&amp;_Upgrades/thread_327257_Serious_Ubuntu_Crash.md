---
title: "Serious Ubuntu Crash"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2006-12-28
A while ago I posted [this thread]("http://ubuntuforums.org/showthread.php?t=326865") and someone told me to move to this forum category. 

Now, I am just running the Ubuntu live cd because a while ago, after booting my laptop, I saw a serious error and the whole screen looks like the terminal. It is my first time to have Ubuntu behave like this.

I'm not sure what caused this problem but I think it is because I uninstalled the vesa driver the last time I logged in because I saw in the screen the term "VGA."

This is what is written on the "terminal-like" screen: 
Starting up ...
[17179570.548000] PCI: Cannot allocate resource region of device 0000:00:06.0
Calliing INT 0x1A (F000:FE6E)
 EAX is 0xB108
Calliing INT 0x1A (F000:FE6E)
 EAX is 0xB108
Calliing INT 0x1A (F000:FE6E)
 EAX is 0xB108

How can I fix this?

---

### Post by dcstar on 2006-12-28
> **wersdaluv said:**
> A while ago I posted [this thread]("http://ubuntuforums.org/showthread.php?t=326865") and someone told me to move to this forum category. 

Now, I am just running the Ubuntu live cd because a while ago, after booting my laptop, I saw a serious error and the whole screen looks like the terminal. It is my first time to have Ubuntu behave like this.

I'm not sure what caused this problem but I think it is because I uninstalled the vesa driver the last time I logged in because I saw in the screen the term "VGA."

This is what is written on the "terminal-like" screen: 
Starting up ...
[17179570.548000] PCI: Cannot allocate resource region of device 0000:00:06.0
Calliing INT 0x1A (F000:FE6E)
 EAX is 0xB108
Calliing INT 0x1A (F000:FE6E)
 EAX is 0xB108
Calliing INT 0x1A (F000:FE6E)
 EAX is 0xB108

How can I fix this?

Try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wersdaluv on 2006-12-28
Thank you... and I am to reboot and try that. :)

---

### Post by ishtiaq on 2006-12-28
I have received similar messages, but during installation. It is explained in [this thread]("http://ubuntuforums.org/showthread.php?t=327213").

---

### Post by wersdaluv on 2006-12-28
> **dcstar said:**
> Try:
```
sudo dpkg-reconfigure xserver-xorg
```

okay... after trying that, I got:
xserver-xorg is broken or not fully installed.

What do I do now?

---

### Post by riven0 on 2006-12-28
> **wersdaluv said:**
> okay... after trying that, I got:
xserver-xorg is broken or not fully installed.

What do I do now?

Hmm, try reinstalling the xserver:

> sudo apt-get install --reinstall xserver-xorg

Hopefully, that'll fix it.

---

### Post by wersdaluv on 2006-12-28
> **riven0 said:**
> Hmm, try reinstalling the xserver:



Hopefully, that'll fix it.

THANK YOU VERY MUCH! IT WORKED! YOU SAVED ME ANOTHER REFORMATTING! WOW! :)

---

### Post by riven0 on 2006-12-28
> **wersdaluv said:**
> THANK YOU VERY MUCH! IT WORKED! YOU SAVED ME ANOTHER REFORMATTING! WOW! :)

Glad to help! :KS

---

