---
title: "Root Password"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by Jannes on 2005-07-01
Ok folks, this is the first time I installed ubuntu. I did the normal installation. But know i wonder why i didnt had to set a root password. Is this normal? And how the hell can I no log in as root??? 

Thanks for your support...

---

### Post by Darkscot on 2005-07-01
[QUOTE=Jannes]Ok folks, this is the first time I installed ubuntu. I did the normal installation. But know i wonder why i didnt had to set a root password. Is this normal? And how the hell can I no log in as root??? 

Thanks for your support...[/QUOTE]

This perplexed me at first as my previous limted experience with Linux was with Mandrake.  Ubuntu doesnt use a root password as other distros do.  When you try to do something that would require the root password on other distros, Ubuntu asks you for your user password.  I think the philosophy behind it is that users should be able to make changes to their own PC as long as they realise the implications of what they are doing.  Asking for the user password reminds you that you are making a change to the system that could cause problems.

---

### Post by Jannes on 2005-07-01
Well I tried this  sudo passwd root to set a rootpasswd but if i do so he always says
Sorry, try again. wtf??? I didnt get!

---

### Post by PMO6022 on 2005-07-01
Jannes,  you have to first put in your user password, then put in what you want the root password to be twice.  The user password is for sudo, then you are setting the password for user "root" and confirming it.

---

### Post by rider343 on 2005-07-01
sudo passwd root
password: **(Your User Password)**

---

