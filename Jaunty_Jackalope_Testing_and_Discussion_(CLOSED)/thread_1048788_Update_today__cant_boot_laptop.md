---
title: "Update today:  cant boot laptop"
date: 2009-01-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by halfsane on 2009-01-23
hey gents, 

Downloaded the updates today, restarted and, basically, when the login screen would normally appear I am greeted by a red line part way across the top of my monitor.

I am running on a Toshiba satellite, intel graphics


I can boot into the recovery console, anything I should try?

---

### Post by Slug71 on 2009-01-23
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

And cross fingers i guess.

---

### Post by halfsane on 2009-01-23
There were a few more updates to install.

I was hopefully, but still nada.

---

### Post by adult swim on 2009-01-23
in another thread 
> **tepsipakki said:**
>  you can get around it by downgrading libdrm2 & libdrm-intel1. Once the new xserver-xorg-video-intel is available on the archive you are safe to upgrade again. Unfortunately one of the amd64 build-daemons is broken at the moment, so the new mesa & -intel are not built yet.

---

### Post by gletob on 2009-01-23
I am experiencing the same problem with my laptop with intel graphics after today's update.  I believe it's Intel GMA 965

---

### Post by halfsane on 2009-01-23
how do I downgrade libdrm2 & libdrm-intel1  ?


I am pretty new to linux, glad it's a known issue.  
I assume its on launchpad, or is there no need?

---

### Post by halfsane on 2009-01-23
> **halfsane said:**
> how do I downgrade libdrm2 & libdrm-intel1  ?


giving it a shot now, found it in this thread   

[http://ubuntuforums.org/showthread.php?t=321156](http://ubuntuforums.org/showthread.php?t=321156)


EDIT:  its not working 1-1 since the solution is a bit old, but it is in the ballpark

---

