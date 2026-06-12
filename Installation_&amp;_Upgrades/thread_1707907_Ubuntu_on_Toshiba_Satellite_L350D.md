---
title: "Ubuntu on Toshiba Satellite L350D"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by msstrend on 2011-03-15
I tried to Install Ubuntu 10.10 on Toshiba Satellite L350D using windows installer. I choose to Install Ubuntu 10.10 and restarted to login Ubuntu and Install remaining Items. It gets in properly, I get Ubuntu splash screen and then computer switches off automatically. I tried all the options in the boot menu safe mode and everything with no result. How to install Ubuntu on this laptop successfully? 

Note: This laptop processor is AMD ATHLON X2 64, video card is ATI Radeon, Had windows 7 previously.

---

### Post by mörgæs on 2011-03-16
Hi, welcome to the fora.

I am not sure that I fully understand. Are you trying to install Ubuntu in Windows using Wubi?

---

### Post by msstrend on 2011-03-16
Thanks for the responding.

Yes I installed ubuntu 10.10 in windows using wubi.

---

### Post by mörgæs on 2011-03-17
So is it solved? Then please mark it so using 'thread tools'.

---

### Post by msstrend on 2011-03-17
No, I'm answering your question. I tried installing ubuntu 10.10 in windows using Wubi. But when I login ubuntu the problem I previously mentioned. It's not fixed.

---

### Post by mörgæs on 2011-03-18
I don't know much of Wubi myself, since I stopped using Windows many years ago, but reading this thread should help:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-03-18
I don't think this is a wubi issue. 

Did you complete the actual install - i.e. you've seen the slideshow - or does it halt before that? 

If not, reinstall, hit ESC when you see the message, and select to install with ACPI workarounds. If that works then you'll need to boot with those options the next time you boot. See this [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (Post #8 talks about Wubi overrides).

If it's already installed and you didn't supply any workarounds then I'm not sure what the issue might be - hardware problem? Shutting the machine off is not a typical symptom.

Any issues in Windows?

EDIT: I think toshiba's need the **acpi=copy_dsdt** option

---

### Post by msstrend on 2011-03-20
I couldn't start the installation at all. :-( 

I even tried without wubi. I get the first splash screen, where the white dot turn orange showing the some process and thats it. after 20 secs "Power off" I did try ACPI workaround nothing is helpful. I tried fedora 14 it launched without any issues. But I need Ubuntu. 

I don't have any issues running windows. It's just that I don't like it.

---

