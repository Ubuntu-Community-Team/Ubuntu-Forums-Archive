---
title: "help with video card drivers"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by pmitch82 on 2008-07-18
im new to linux and i just installed ubuntu on my machine and ive went through the update process and i need to update my video card drivers.  i have a ati x700 agp, i used the linux driver that poped up in the the updater and that made my machine screen go dark.  so i have the actuall ati driver now, and when i go to install it it starts the install process but tells me i need to a superuser.  ive looked in the superuser thing and the command is "sudo"  but how do i use that in the terminal to install the driver??
thanks

---

### Post by Pumalite on 2008-07-18
Try Envy>
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by pmitch82 on 2008-07-18
envy did not work.  same problem as before i installed the driver that envy suggested and now when i boot my machine i get the ubuntu load screen then it just goes black.
any ideas?

---

### Post by Pumalite on 2008-07-18
Maybe this will help:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by pmitch82 on 2008-07-20
that looks like alot to do(or atleast figure out) is it worth it??? i dont know how much that will help the system out.  Should i take the time to figure out or just go with the default driver that works?? im not running a very high res only 1024x768  thanks

---

### Post by Pumalite on 2008-07-20
Having an ATI card is a problem because ATI does not support Linux. Next time go with Nvidia.

---

### Post by pmitch82 on 2008-07-20
well the card that is in there is a ati x700 I also have a old nvidia 5200, should i switch them out?? i dont play much for video games on the system, just mainly for downloading and surfing and such.
thanks

---

### Post by Pumalite on 2008-07-20
You don't loose anything with trying. Even though the 5200 might have issues of its own. Just choose the right driver in the Nvidia site.

---

### Post by pmitch82 on 2008-07-20
when i go into safe mode how do i undo what envy did? and install whatever driver linux defaults to
thanks a ton

---

### Post by Pumalite on 2008-07-20
sudo envy --uninstall-all

---

### Post by upchucky on 2008-07-20
try the nvidia card, and do this exactly as it says step by step,

but watch for the legacy section for the right driver when you download the driver.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by Wazoot on 2008-07-20
ATI works fine with my Ubuntu..my old comp has an x800. got the restricted drivers for it and worked fine.

---

