---
title: "Problem after install"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by someone012 on 2008-07-07
I installed ubuntu then rebooted. At the loading screen the orange bar bounced back and forth, but it didn't progress and gave me busybox after 5 minutes. help?

---

### Post by overdrank on 2008-07-07
> **someone012 said:**
> I installed ubuntu then rebooted. At the loading screen the orange bar bounced back and forth, but it didn't progress and gave me busybox after 5 minutes. help?

Hi and welcome, could you give use some system specs? Also you may try and remove the quiet splash from the kernel to see any errors, press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and then hit enter and then  b to boot. Have you tried to boot into recovery mode?

---

### Post by Gloominati on 2008-07-08
I have exactly the same problem, i did the quiet splash but it didn't change anything

---

### Post by overdrank on 2008-07-08
> **Gloominati said:**
> I have exactly the same problem, i did the quiet splash but it didn't change anything

Ok after removing the quiet splash from the kernel line did you see any errors? You can try and replace the quiet splash with noapic and see if that helps. Also your Ubuntu is installed correct.

---

