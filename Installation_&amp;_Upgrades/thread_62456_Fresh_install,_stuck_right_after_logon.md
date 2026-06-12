---
title: "Fresh install, stuck right after logon"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by Tsurabisu on 2005-09-04
I just installed it,  ( correctly I believe ) and after I log on I get some kind of DOS like interface. heres what I get:
> 
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
You have new mail.
travis@ubuntu:~$
 

Is there a command to get into the auctual OS?
Thanks in advanced.

---

### Post by ZaherM on 2005-09-04
Try:
```
sudo startx
``` 

Or (If you are running Ubuntu/GNOME)
```
sudo gdm
```

---

### Post by Tsurabisu on 2005-09-05
Ok, i tried sudo startx but then it brings me to this smaller OS like thing that shrinks to less that 1/4th of the screen.

---

### Post by ZaherM on 2005-09-05
[QUOTE=Tsurabisu]Ok, i tried sudo startx but then it brings me to this smaller OS like thing that shrinks to less that 1/4th of the screen.[/QUOTE]
 Have you tried the second option?
```

sudo gdm

```

---

### Post by Zoom8112 on 2005-09-06
I too have just encoutered this problem.  The only difference is, is that I am installing Kubuntu 5.04.

I get to the command prompt.  When I type "sudo startX" I get the quarter screen with another command prompt.  When I type "sudo kdm" I get a login screen.  I proceed to login, and I am greeted with the quarter screen and the command prompt again.

How do I get into the actual OS?  I dont know if this is worth noting, but I am attempting a dual boot with XP on seperate physical hard drives.  

Thank you for the advice in advance.

---

### Post by Zoom8112 on 2005-09-06
[http://ubuntuforums.org/showthread.php?t=58123](http://ubuntuforums.org/showthread.php?t=58123)

I scoured the installation help forum, and I did run across this thread.  I will go and attempt configure my video card if it is in actuality a problem.

Anyone have hints here?  I have a Radeon 9700 pro.

---

