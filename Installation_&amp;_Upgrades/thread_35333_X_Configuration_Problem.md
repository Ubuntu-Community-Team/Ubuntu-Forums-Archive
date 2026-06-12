---
title: "X Configuration Problem"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by dilip281 on 2005-05-18
hi, 

    i  got a free ubuntu cd shipped to me yesterday, and wanting to check out ubuntu for quite a long time, i popped in the installer cd. it managed to install everything and the installer exited cleanly. but when it restarted i got a message that there is a problem with X on my system due to some error that i have been unable to diagnose. so when i start the system, it dumps me into a shell . 

     i ran "startx" to see if i could know the exact error, but unfortunately, all i get to see are messages about skipped packages , which were probably to be used, were it not for the error. i could find nothing about the error itself on the screen. i could not scroll up to check the error, since i was in shell mode.

   i tried the command "xf86config" which i got from a book about redhat 7.2 and was able to configure my keyboard, mouse, refresh rates, resolutions etc. please note that i selected nvidia geforce as my display unit ( my manual states that my onboard gpu is geforce2 MX class ). i saved the configuration file and restarted x, but still the same result.

  this is my system configuration :

   AMD AthlonXP 1800+
   MSI model "MS-6367" motherboard
   Samsung SyncMaster 763DFX
   128 mb RAM
   40 GB Seagate HDD. (the ubuntu root partition is 10gb)
   
   i hope the  information i have given i sufficient. if anybody has any suggestions as to determining the problem or feel confident as to propose a solution or workaround, i would like to say thanks beforehand.

---

### Post by harryc on 2005-05-18
When you boot up to a console, issue the command;

```
 nano /var/log/Xorg.0.log
```

Take a look towards the end of the log for errors. Post them here if you can.

---

