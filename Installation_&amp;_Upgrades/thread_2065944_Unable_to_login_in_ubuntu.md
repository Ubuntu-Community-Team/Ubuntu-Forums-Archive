---
title: "Unable to login in ubuntu"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by Kushal17 on 2012-10-03
Hi,

I have installed ubuntu 12.04 on VMWARE Workstation. Today I performed some upgrade on ubuntu to install Oracle 11g on it. After installing updates, I restarted it. Since then I am not able to login to ubuntu.

Admin user ID of ubuntu is ubuntu1204. But when I check /etc/passwd from guest login it does not show the user in that file.

While login it does not give any error message as well. 

Please help in resolving the issue.

Thanks.

---

### Post by 2F4U on 2012-10-03
So what exactly happens when you enter your username and password? You don't get an error message, so I am assuming the username and password is correct. You can verify this by pressing Ctrl-Alt-F1 (F2, etc.) to get to a virtual console and login using that username and password.
If that works, it is likely that the login fails because the desktop environment somehow crashes, probably due to something you did before the problem appears.

---

