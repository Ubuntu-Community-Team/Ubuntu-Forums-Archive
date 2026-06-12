---
title: "i386 in AMD 64 system"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by dvijaydev46 on 2007-12-13
Hi please read this patiently and try to help me.

I think it's an age old question. But I didn't get any convincing answer. But I'm asking it again. Is it possible to run Ubuntu i386 version in an AMD 64 x2 processor? I've tried all 32 bit versions of Ubuntu. When I boot it says something line "timer not Synching" when I try to boot every versions of Ubuntu. Please Give me an idea why it happens. I want to switch over to the 32 bit version as I need to use some softwares like Skype which I'm not able to install (I referred toi various threads and found nothing useful). 

Fiesty 64 boots flawlessly but Gusty 64 doesn't. It seems to boot but hangs in middle. I think I tried all commands like noacpi, nolacpi etc. They only take me to command prompt after running some scripts. Why is Fiesty 64 working and not Gusty 64?

I had some problems with booting SimplyMepis from CD but after i enabled some boot option (I think it is to do with nvidia driver) it loaded. The same is true for Mandria one 2008 also. Is this Nvidia driver problem that is keeping me from booting Gusty 64? 

My system is Athlon 4200 x2 on an Asus M2N MX board and I'm using the onboard GPU - Nvidia Geforce 6100. 

Thanks for the patience. Please Help.
Thanks again.

---

### Post by logos34 on 2007-12-13
> **dvijaydev46 said:**
> Is this Nvidia driver problem that is keeping me from booting Gusty 64? 

nope.  I run x64 gutsy on nvidia 6100.

---

### Post by dvijaydev46 on 2007-12-13
So what could be the problem? Why is no one replying to this kind of a problem? I think this is one of the most unanswered questions I've ever seen in Ubuntu forums. A good answer will be very helpful to many because too many people face the same kind of problem.

---

### Post by PmDematagoda on 2007-12-13
I realise that this is not in line with the thread topic, but since the reason you want to use 32 bit is because Skype cannot be installed, I believe that this [page]("https://help.ubuntu.com/community/Skype") could help you install Skype on Ubuntu x64 and let you use Ubuntu x64 satisfactorily.

---

### Post by Keyper7 on 2007-12-13
Short answer: yes, it's possible and supposed to work.

Your problems might be *related to* but they are definitely *not caused* by the fact that it's a 32-bit version. There's probably a workaround for them. Could you give the exact error message you get when you try to install the 32-bit version? I don't think a message such as "timer not syncing" exists... Maybe you meant "kernel panic - not syncing: IO-APIC + timer doesn't work"?

Also, you said you tried kernel parameters during the 64 gutsy install, but did you try them during any of the 32-bit installs?

---

