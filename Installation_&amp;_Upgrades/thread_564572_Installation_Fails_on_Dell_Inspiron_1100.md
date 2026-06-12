---
title: "Installation Fails on Dell Inspiron 1100"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by TheKen on 2007-10-01
Hello Everyone,

I am a new linux user and i wanted to install Ubuntu on a Dell Inpsiron 1100 Laptop. Its specs are:

>2.0GHz celeron processor
1Gb ram
100Gb 5400 RPM hard drive
bios is A32 version

I tried to install Ubuntu Version 6.06 LTS using the Alternate Installl CD. It goes all the way throught the installation process with no problems until the very end. The screen goes blank except for 2 white blocks (like the old IBM cursor). The hard drive activity light goes for a while but nothing else happens. I am forced to use the power button to shut the computer off. When I turn it back on again, it will not boot up.

I do not think this is a hardware problem because after I tried Ubuntu, I installed PCLinuxOS 2007 with no problems and it runs great. But I really would rather have Ubuntu because of its ease of use, software support, and community support.

Does anyone have any idea what could be causing this and what I can do about it? Please remember I am an extreme newbie. So please be gentle.

Thanks in advance,
Ken

---

### Post by veloce on 2007-10-01
Could be a screen resolution issue.  Without adjustment to xorg.conf you cannot get anything about 800x600 out of the intel graphics adapter on the 1100.   If you set x to use higher resolutions in your installation then this could be the cause.  Try eliminating everything but 640x480 and see if it will install.  If that works, add the following lines to /etc/X11/xorg.conf in the "monitor" section:

```

HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
 
```

---

### Post by TheKen on 2007-10-01
I am using the text base installation cd. Can I adjust the monitor resolution from the beginning menu on the cd? I understand what you are saying, but I am not sure how to try it. I am very new to Linux and am not sure what to do. Can you please give me a step by step? Thank you for your reply and any other help you can give.

thanks,
ken

---

### Post by veloce on 2007-10-02
> **TheKen said:**
> I am using the text base installation cd. Can I adjust the monitor resolution from the beginning menu on the cd? I understand what you are saying, but I am not sure how to try it. I am very new to Linux and am not sure what to do. Can you please give me a step by step? Thank you for your reply and any other help you can give.

thanks,
ken

At one point in the install, you are asked what resolutions to use for X.  From memory there is a virtical list with check boxes beside each resolution from highest to lowest - sound familiar? The default will include 1024x768 which doesn't work on the 1100 without modification.

Just a thought before you try re-installing.  Can you boot ubuntu in "safe mode"?  If so, you can get to a command line and fix the xorg.conf without re-installing.

---

### Post by TheKen on 2007-10-02
I don't recall it asking for a screen resolution. could it be because i am using the text based installation?

---

