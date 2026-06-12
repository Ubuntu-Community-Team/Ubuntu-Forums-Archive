---
title: "Xubuntu Dpkg problem"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by -=Viper=- on 2008-02-13
xubuntu says that i need to configure the dpkg when i tried to update so i went to the root account.  When i run the dpkg i get this output

```
root@ernesto-laptop:~# dpkg --configure -a
Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
root@ernesto-laptop:~# 


```

I don't know what to do.  If anyone else knows what to do please post!  i dont want to redo this laptop and if i do i think i will go crazy!  i have put like 8 different OS's on it and i decided xubuntu cause it ran smooth.  Don't make me go back to windows!!  I DON'T WANA GO BACK!!  hehe :lolflag:

---

### Post by CJ145 on 2008-02-13
I too am having a similar problem.  This is an x86_64 system that was just installed.  On booting I enabled the gutsy-updates repository, installed all updates, and rebooted.  On the reboot gnome no longer works (i get the orange backround and a mouse only).  I have been trying to figure this out.

One of the errors I get is when I run ldconfig.  It lists about 20 libraries as being truncated. 

Edit: GDM still works, I can get the log in window and log in, however after i type in password and hit enter i get the orange screen and mouse.

---

### Post by -=Viper=- on 2008-02-13
Bump!

Does no one have a fix?  I really dont want to make another switch but i may try deban Etch if no one knows a solution here.  Please help if you can!  im begining to hate xubuntu and ready to make the switch to either OS/2 if my dad can find his install disketts or back to windows XP  (ewwwwwwwwwwwwww  but its better then vista :lolflag:)  Help everyone please...ill be maing the switch soon if i dont get an answer

---

