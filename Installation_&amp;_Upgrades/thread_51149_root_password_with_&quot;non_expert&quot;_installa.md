---
title: "root password with &quot;non expert&quot; installation"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by bent on 2005-07-22
Hi, I have done the no-expert installation and now I cannot login as root. Root was set up automatically. Do you know what the standard password for root is?

---

### Post by DJ_Max on 2005-07-22
Ubuntu does not come with a root account. You can get root privileges by using sudo, and the password is your default account pass.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bent on 2005-07-22
Thanks!

---

### Post by neltnerb on 2005-07-22
[QUOTE=DJ_Max]Ubuntu does not come with a root account. You can get root privileges by using sudo, and the password is your default account pass.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

... or, alternatively, if you're like me and have been doing it the other way for long enough that you don't care to change...

Do the age old sudo su trick and change your root password with passwd.

---

### Post by DJ_Max on 2005-07-22
Well yea, thats on that page as well, at the bottom.

---

