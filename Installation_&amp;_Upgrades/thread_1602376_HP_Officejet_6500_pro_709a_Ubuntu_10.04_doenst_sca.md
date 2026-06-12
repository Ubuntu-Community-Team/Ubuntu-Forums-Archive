---
title: "HP Officejet 6500 pro 709a Ubuntu 10.04 doenst scan"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by H@ncho on 2010-10-21
Hello Ubuntuprofessionals:)

I read different threads, but i am doing something wrong. I downloaded HPLIP for this printer, but gedit doesnt understand the package i downloaded. It is called hplip.3.10.6. and i ran every language but i doestn open. I hope someone wants to  help me out

Thank you for your time,

Greeetz,

H@ncho

---

### Post by P4man on 2010-10-21
Welcome windows addict :) Try to kick the windows habit of googling for a driver or app and downloading it and then doubleclicking it. 

Instead, go to applications > software center. Search for HP and you will see the very same app ready for you to install. You can even chose some addons (other scan applications).

But Im not sure you really need it. You probably just need a scan app.

---

### Post by sikander3786 on 2010-10-21
> but gedit doesnt understand the package i downloaded

If it is a .deb pacakage, you need to open it in Gdebi package manager. Does it start automatically in Gedit when you double click?

---

### Post by sgosnell on 2010-10-21
Gedit is a text editor, and it won't help for software packages.  Gdebi is the .deb package installer, and you should be able to right-click on the .deb file and select 'Open with gdebi' if the file association is for Archive Manager, which seems to be rather common.  But I agree that the best way to install it is through Synaptic package manager, or even apt-get or aptitude.  The HP software packages are in the repositories.

---

### Post by H@ncho on 2010-10-24
Hello pro's:KS

This afternoon i am going in deep and work with your suggestions. Thank you very much for now and i ll keep you posted! Sorry for my late respons

H@ncho

---

### Post by H@ncho on 2010-10-25
Thank you guys, it is all working well.

:KSRespect for this community:KS

---

