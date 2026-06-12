---
title: "Can't get passed the login screen"
date: 2018-03-31
forum: Installation &amp; Upgrades
---

### Post by ekevu on 2018-03-31
I have installed Ubuntu 17.10 on a computer that used 15.10 before. I used manual partitioning and replaced the system, but left the /home partition untouched. Now, after the complete reinstall, I get to the login screen and I cannot login. Neither in Wayland nor in X.org. I can switch to a terminal and get to the error message
```
xauth: timeout in locking authority file /home/USER/.Xauthority

```

I tried the first solution mentioned here ([https://unix.stackexchange.com/questions/215558/why-am-i-getting-this-message-from-xauth-timeout-in-locking-authority-file-ho#215559](https://unix.stackexchange.com/questions/215558/why-am-i-getting-this-message-from-xauth-timeout-in-locking-authority-file-ho#215559)), no success. 

If I add a new user, I can successfully start the GUI. However, I want to get access to the home directory of the user I had on this laptop.

Can anybody help?

---

### Post by ank2 on 2018-03-31
Can you use startx after logged in as user (not root)?

---

### Post by ekevu on 2018-03-31
No, I couldn't. Eventually, I implemented the backup into the new user account. That worked.

---

