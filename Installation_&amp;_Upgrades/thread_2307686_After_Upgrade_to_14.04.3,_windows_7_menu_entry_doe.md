---
title: "After Upgrade to 14.04.3, windows 7 menu entry doesn't work."
date: 2015-12-27
forum: Installation &amp; Upgrades
---

### Post by kurt16 on 2015-12-27
Hello,

i have an asus a7j (a very old laptop) and i was on ubuntu 12.02. A few days ago i upgraded to ubuntu 14.04.3 LTS and everything seems to be ok but today when i click on windows 7 menuentry i realised that this doesnt work. I can hear a bip and after that the window doesn't change the color, it keeps the same as in the menu entry selection, but nothing happens, no access to disk so i have to use control+alt+supr to reboot.

I have an boot-repair system info log:

[http://paste.ubuntu.com/14231879/](http://paste.ubuntu.com/14231879/)

I downloaded boot-repair live iso to try to repair it myself and i used the default options and now i have this log:
[http://paste.ubuntu.com/14232911/](http://paste.ubuntu.com/14232911/)

Now i have two options to windows 7 on the menuentry but both fails.

Thanks in advance and regards.

---

### Post by cyryder7 on 2015-12-27
i think you are having the same issue, i was having. 

1.boot from the windows repair cd and then chose the repair option 
2. go to cmd prompt
3. type bootrec /fixMBR
bootrec /fixBoot
bootrec /rebuildBCD

make sure there is a space between bootrec and the /

you will lose GRUB but windows 7 should load fine. im trying to figure out the next step

---

### Post by kurt16 on 2015-12-31
I couldn't find my windows 7 x32 so i tried to recover that using Hirens Boot CD. First step i did was try to boot that partition using hirens and windows 7 loaded fine and everything works so i blame ubuntu (i did'nt try the commands in the previous post). After that i download korora 22 xfce and i overrided ubuntu with it and now everything works fine. Now, when i try to boot windows menuentry, grub warns me that something wrote some info in an important place and if i am sure that i want to continue, i click yes and windows works as always did.

Summarizing, ubuntu updrade, and maybe boot-repair too, wrote something where they should'nt and i had that issue. I'm happy with korora and i will use it some time.

Thanks for help.

---

