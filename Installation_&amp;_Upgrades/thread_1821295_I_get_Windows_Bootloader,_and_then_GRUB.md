---
title: "I get Windows Bootloader, and then GRUB"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by rationalthinker1 on 2011-08-08
Hello, I installed Ubuntu and Windows 7 on my computer. I first get the Windows bootloader telling me choose between Windows or Ubuntu. If I pick Ubuntu, I then get a GRUB loader telling me to choose between different versions of Ubuntu and Windows 7. 

How do I remove GRUB and just use Windows bootloader?

Thanks :)

---

### Post by Basher101 on 2011-08-08
Wait what?? Windows' MBR doesn't recognize Linux as far as i know. How the hell did you manage to get that thing recognize linux and grub ?? Could you photograph your Monitor when using the "windows" bootloader please? Im very curious here..

---

### Post by rationalthinker1 on 2011-08-08
> **Basher101 said:**
> Wait what?? Windows' MBR doesn't recognize Linux as far as i know. How the hell did you manage to get that thing recognize linux and grub ?? Could you photograph your Monitor when using the "windows" bootloader please? Im very curious here..
I dunno lol, I just installed it like that. I'll post a clip.

---

### Post by Basher101 on 2011-08-08
Linux comes with grub because windows' bootloader doesn't recognize it. Can you also tell me what windows 7 version you installed? Home? or Ultimate?

---

### Post by garvinrick4 on 2011-08-08
Wubi install and you uninstalled and reinstalled and it now has 2 wubildr in BCD of Windows
7 possibly. In Windows cmd line:
```
bcdedit
```
There will be a entry with wubildr in it, is there possible 2 entries with wubildr in it?

---

### Post by Basher101 on 2011-08-08
Wow i did not think it could be wubi. I never used wubi, i directly hit install on the live cd lol

---

### Post by rationalthinker1 on 2011-08-08
> **Basher101 said:**
> Linux comes with grub because windows' bootloader doesn't recognize it. Can you also tell me what windows 7 version you installed? Home? or Ultimate?

Windows Ultimate,

Here's the video:
```
https://www.youtube.com/watch?v=FcDLrXZUr1Q&hd=1
```

Now, how do I remove the second GRUB screen?

---

### Post by Basher101 on 2011-08-08
You only installed wubi from what i can tell in the video. You dont get the plymouth, nor text messages that apper normally on bootup or a splash screen. You will need to download the Live CD , boot from it and install ubuntu onto its own partition. This will then fully overwrite your windows MBR because linux only works with grub.

this should fix your issue (i guess your issue is having "two" bootloaders?)

---

### Post by rationalthinker1 on 2011-08-08
> **Basher101 said:**
> You only installed wubi from what i can tell in the video. You dont get the plymouth, nor text messages that apper normally on bootup or a splash screen. You will need to download the Live CD , boot from it and install ubuntu onto its own partition. This will then fully overwrite your windows MBR because linux only works with grub.

this should fix your issue (i guess your issue is having "two" bootloaders?)


Okay, here's what I did. I installed [GRUB Customizer]("http://www.omgubuntu.co.uk/2011/05/grub-customizer/") and told it to show that menu for 0 seconds. So I don't even see it. 

I have Wubi installed but isn't that enough? Ubuntu works perfectly fine.

---

### Post by Basher101 on 2011-08-08
Well since i did never use wubi, nor install it i can't answer your question. But i read somwhere that wubi creates a **virtual** partition inside windows (i really don't know if it works like this, will google it sometime tho). This can lead to performance drops. But since you dont have any issues stick to wubi. Whatever suits you best

---

### Post by YannBuntu on 2011-08-09
**@rationalthinker1: **welcome amongst us.
As you are a new Ubuntu user, you can keep your Wubi installation (Ubuntu inside Windows) for several weeks~months, until you get accustomed with Ubuntu.

But even the developer of Wubi recognises that it is just a way to TRY Ubuntu in a short term.

So when you will be ready to install Ubuntu in a normal way (on a separate partition), first backup your data (documents/pictures..) then create a new thread on this forum to get advice.

---

