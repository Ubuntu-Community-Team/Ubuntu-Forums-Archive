---
title: "Root authentication fails after fresh install of Lubuntu 15.04"
date: 2015-08-25
forum: Installation &amp; Upgrades
---

### Post by Alberto_Taiuti on 2015-08-25
Hello everyone,


I have installed Lubuntu 15.04 on my Dell Latitude E5450 but I have a problem:

The install completes just fine, and after rebooting the machine and start the OS I am shown the login prompt; I use the password set during installation and it logs me in okay.

_However_, when I try to obtain root access by using the same password, the authentication fails, saying the password is incorrect, but I am 100% sure I am typing it correctly as it's the same I use for the login prompt.

I have tried to re-install Lubuntu but I get the same error.

Does anybody know how to fix this?



Thanks in advance.

---

### Post by sisco311 on 2015-08-25
Hi and welcome to the forums!

There are many ways to obtain root access. How did you try to obtain it?

---

### Post by ajgreeny on 2015-08-25
> **sisco311 said:**
> Hi and welcome to the forums!

There are many ways to obtain root access. How did you try to obtain it?
^^ +1

Are you hoping that you can login to the GUI desktop as root because if so, you are going to be very disappointed.

In Ubuntu and its related versions the root account is disabled by default and as the first registered user of the OS you will be able to raise your permissions to those of root by using sudo.

See Root-Sudo in my signature for all the details.

If, however, you are trying to use the normal Ubuntu sudo and are not able to do so, then we will need to look a bit closer at everything, so come back again and tell us more.

---

### Post by Alberto_Taiuti on 2015-08-31
Hi, thanks!


It was the password I had chosen during installation.

After re-installing it, the third time it worked and now I can obtain root access normally by using the password chosen during the install.

---

