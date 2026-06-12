---
title: "/etc/apt/source.list auto comment at reboot"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by vartere on 2005-04-10
Hi,
 
i have changed my /etc/apt/source.list file, but when i restart the pc, the file changes and all rows are with comment #

What's the reason? 
Help me please

vartere

---

### Post by PMO6022 on 2005-04-10
How are you editing your /etc/atp/sources.list file?  You must use sudo and save for any changes to take effect:  see [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

---

### Post by vartere on 2005-04-10
yes, i'm root when i edit the file with gedit and i'm sure i save the file.  ](*,) 

i used the ubuntu guide

 :-?

---

### Post by PMO6022 on 2005-04-10
Have you tried editing the file, and then reopening it immediatly after closing gedit? That would tell you if the problem occurs when you reboot or at some other time. 

I don't have a whole lot of ideas if it is indeed the reboot that causes the file to revert back to its original form.

---

### Post by vartere on 2005-04-10
i don't known, but i re-installed the system again and the problem disappered.

thanks a lot

---

