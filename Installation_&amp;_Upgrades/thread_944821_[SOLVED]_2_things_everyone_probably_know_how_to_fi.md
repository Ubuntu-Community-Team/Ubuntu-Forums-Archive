---
title: "[SOLVED] 2 things everyone probably know how to fix but me"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by cardioanomaly on 2008-10-11
Trying to use the package installer and each time i do i get the error that says, "only one software management tool is allowed to run at the same time, please close the other application e.g. update manager, aptitude, or synaptic."

And now the second one regarding the update manager. I try to install the new updates and get this error, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"
So i open the terminal and does what is says and i get,"dpkg:requested operation requires superuser privilege"
I thought I was the the only user.  
Please tell me if i'm screwed and should just install ubuntu all over again.

---

### Post by AlexBellisBrown on 2008-10-11
> **cardioanomaly said:**
> dpkg --configure -a' to correct the problem. 

Superuser? You need to Sudo it!

Sudo dpkg --configure -a

And put your password when prompted.

---

### Post by AlexBellisBrown on 2008-10-11
> **cardioanomaly said:**
> Trying to use the package installer and each time i do i get the error that says, "only one software management tool is allowed to run at the same time, please close the other application e.g. update manager, aptitude, or synaptic."


Forgot about your first question. You can only use one software management tool at a time, so close the other and only run one at once. You must have had 2 open at once. :popcorn:

---

### Post by oldos2er on 2008-10-11
"Sudo dpkg --configure -a" won't work. Use "sudo dpkg --configure -a" instead.

---

### Post by AlexBellisBrown on 2008-10-11
Ah, sorry, yep, silly me and my capital letters!! sudo, not Sudo!

---

### Post by cardioanomaly on 2008-10-11
*prepares to insert own head through nearest wall* Thanks for helping a lost soul for many hours.

---

### Post by Sef on 2008-10-11
> *prepares to insert own head through nearest wall* Thanks for helping a lost soul for many hours.


Much safer to break Windows.  :)

---

