---
title: "Cannot Login in newly installed Ubuntu"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by majikstreet on 2005-07-23
Hello,
I just installed Ubuntu on a secondary machine using the "server" option because it will be a server.

I have used linux before and am confortable with the command line.

My problem is I cannot login to Ubuntu! I set up an account in the installation, majikstreet, and I used a password which I use for other things so I remember it. I tried to login using majikstreet and my password and it says "Login Incorrect". 

Also, what is the default root password? If I could get in the root account, I know how to set up and delete accounts.

Thanks,
majikstreet

---

### Post by codejunkie on 2005-07-23
[QUOTE=majikstreet]Hello,
I just installed Ubuntu on a secondary machine using the "server" option because it will be a server.

I have used linux before and am confortable with the command line.

My problem is I cannot login to Ubuntu! I set up an account in the installation, majikstreet, and I used a password which I use for other things so I remember it. I tried to login using majikstreet and my password and it says "Login Incorrect". 

Also, what is the default root password? If I could get in the root account, I know how to set up and delete accounts.

Thanks,
majikstreet[/QUOTE]
ubuntu uses sudo instead of the root password exaple: ```
sudo su
```and enter your password gives root access.. but since you can't login as your main user reboot at grub choose recovery mode this will give you root access now you can add a new user or enable the root account with this ```
passwd root
``` hope this helps.

---

### Post by majikstreet on 2005-07-23
Thank you so much!

I was able to get into Ubuntu.

Thanks again,
majikstreet

---

