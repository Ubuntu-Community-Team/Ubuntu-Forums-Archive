---
title: "Black screen after installation, what to do?"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by Jan_Fiskestang on 2010-10-06
I've got a big(?) problem. I installed the Ubuntu  10.04 yesterday on my Acer Aspire One, it worked flawlessly thru the  installation process and at the end it restarted (as normal I guess?).  Anyway, when it started again the screen was completely black. Even if I  try connecting a secondary screen I get the same result. In other  words, after instalation I've never been able to use my computer... 

Info: It was installed from a usb stick, because of the lack of a cd drive. I used the program "*unetbootin"* to tansfer/instal the .iso I dwonloaded from the ubuntu download site. I can see now that I maby downloaded the wrong version because it's called "ubuntu-10.04.1-desktop-i386". But I hope there is some way to fix it, or delete it and install the right version?


Have  anyone a solution for my problem? 

Regards Sindre (Jan_Fiskestang)

EDIT: I forgot to mention, if you did not get it, that not even the first screen shot appeared, the one where you press f12 to enter boot selection and f2 to enter bios... Thats why I do not know how to delete it/try re-innstalling the proper version (if I messed up and installed the wrong one)

---

### Post by mafutha1 on 2010-10-06
Hi this happened to me about a week ago, found the solution here;

[http://lowendguru.com/2010/02/how-to-fix-the-acer-aspire-one-black-screen/](http://lowendguru.com/2010/02/how-to-fix-the-acer-aspire-one-black-screen/)

This fix worked for me!

Good luck!

---

### Post by sikander3786 on 2010-10-06
Instead of flashing the Bios as mentioned in the above post, I'll recommend to  edit your Grub menu entry and replace "quiet & splash" with "nomodeset". See here for details.

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

If the boot is successful, install the proprietary drives and you'll be fine. Otherwise post back.

---

### Post by Jan_Fiskestang on 2010-10-06
You are my hero! It worked like a charm:)

I've got another question for you tought: Do you have a fix for the wireless internet connection as well? Mine did not work proper with the pre-installed windows xp (it almost never worked), and now, Ubuntu can't even find the wireless connection (the light that indicates it's turned i powered (on the computer) do not work at all)... I know there is a new version of the wifi's firmware or something, but I have no idea how to fix it, especially not in Linux.. 

Sorry for beeing such a noob, but it's my first time using Linux ever...

---

### Post by Jan_Fiskestang on 2010-10-06
> **sikander3786 said:**
> Instead of flashing the Bios as mentioned in the above post, I'll recommend to  edit your Grub menu entry and replace "quiet & splash" with "nomodeset". See here for details.

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

If the boot is successful, install the proprietary drives and you'll be fine. Otherwise post back.

I tried the Bios flash method, and as it turned out, it worked beautifully! But thank you for your answer anyway!

---

### Post by mafutha1 on 2010-10-06
> **sikander3786 said:**
> Instead of flashing the Bios as mentioned in the above post, I'll recommend to  edit your Grub menu entry and replace "quiet & splash" with "nomodeset". See here for details.

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

If the boot is successful, install the proprietary drives and you'll be fine. Otherwise post back.

This is a known BIOS issue with the Aspire One, editing Grub would not have helped in this instance, as the bios does not start at all, but for a ''normal'' blank screen your's would be the better fix.

---

### Post by sikander3786 on 2010-10-07
Hmmmmm. Got it. Actually I mis-understood this part of the post

> when it started again the screen was completely black

Anyways, mufutha1 was experienced with it and guided you home.

Happy Ubuntu-ing!

---

