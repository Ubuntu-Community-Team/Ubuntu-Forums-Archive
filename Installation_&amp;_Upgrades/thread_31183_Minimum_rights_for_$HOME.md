---
title: "Minimum rights for $HOME"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by ranarion on 2005-05-02
Hi everyone,

I installied Kubuntu (Hoary) over an older Linux installation, telling Hoary's installer to overwrite the old system and swap partitions but to keep the old /home (and mount it just at that location).

After the installation, logging into KDE failed because .kde could not be created ("no write access to $HOME"). The directory had the rights drwxrwxr-x at the time. Only by changing it to 777 (drwxrwxrwx) I could get KDE to work. 

However, I'd like to reduce the permissions so that my home is no longer world-writeable. What permissions suffice?

Thanks in advance!

(Come to think of it: Could that be an ownership problem? But I *am* user 502 in Kubuntu, am I not?)

---

### Post by Juergen on 2005-05-02
> Could that be an ownership problem? But I *am* user 502 in Kubuntu, am I not?You are probably user 1000.
Type 'id' in a xterm to find out.

And therefore, yes, it's probably an ownership problem.

---

### Post by vtechstu on 2005-06-28
Did you ever get this solved. If not let me know.

---

