---
title: "Alternate CD Install fail on Asus L3500h"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by jemdem on 2011-12-19
Hello,

i've got an old Asus L3500H (Pentium 4, 256MB shared ram) that i'd like to run Lubuntu on. I've downloaded and run the Alternate install 'mini' iso
Everything seemed to go fine, but when I reboot the PC to complete the installation, nothing happens, it freezes on a black screen before displaying anything (except for an underscore, displayed a second before screen goes to black).
I've check ubuntu's hardware compatibility page, and it says everything goes fine except from 3g Acceleration and IRDA.


Can someone help?

Thanks already

---

### Post by 2F4U on 2011-12-19
What graphics card do you have? If it is nVidia or ATI, you try adding nomodeset to the grub kernel parameters. Sometimes this helps with graphics related problems.

---

### Post by jemdem on 2011-12-20
Thanks for your answer, how do I do that?

---

### Post by jemdem on 2011-12-28
up

---

