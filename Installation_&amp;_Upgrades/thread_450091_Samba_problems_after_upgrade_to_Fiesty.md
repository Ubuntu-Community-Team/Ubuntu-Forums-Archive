---
title: "Samba problems after upgrade to Fiesty"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by D10 on 2007-05-20
Well I upgraded my main desktop to Fiesty on Friday,and everything went fine or it appeared to. I don't have a high speed connection at home so I took my desktop  to work and the upgrade went great with no problems that  I could see. Until I got home and tried to connect to my desktop samba shares with my laptop. 

I have a total of 4 shares on my machine, but only 2 are still working. One is a folder in my home folder and another is an external USB drive these both work, but the other 2 shares are partitions on the drives in the machine. I have changed the permissions to 0777 but I am still unable to access those 2 shares, from any machine including the desktop itself.

Does anyone have any ideas what I could check to remedy this?

Thanks,
D10

---

### Post by D10 on 2007-05-21
It seems that it is not a Samba problem, but a permission problem. After a little more trial and error it appears I am unable to change any folder or file permissions on my system. I tried both cli and gui as my user and sudo/root, and was unable to change any permission from what it was before I upgraded to Fiesty.

Any thoughts?

Thanks,
D10

---

### Post by D10 on 2007-05-22
BUMP

Anyone have any ideas before I do a complete reload?

Thanks.

---

