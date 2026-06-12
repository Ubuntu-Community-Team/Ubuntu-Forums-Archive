---
title: "dpkg --configure -a freezes"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by n00bupgrade on 2011-11-07
Hi
 I upgraded from 11.04 to 11.10 today. During upgrade, the system freezed when configuring/installing software center. Unfortunately I had to give it cold reboot. After that I am able to log in to new 11.10 but when I try to install anything, I get the message to run ```
sudo dpkg --configure -a
```I run that and again it hangs at configuring software-center. I do not know what to do! Browsing other posts,
I learned that using```
 sudo dpkg -D2000 --configure -a
``` will give more information. But the only message that is displayed is

```
Setting up software center (5.4.1.0) 
```I do not know how can I debug this, since when I run this command system hangs. 

Please help me fix this issue.

Thanks

---

### Post by ajgreeny on 2011-11-07
You need to run those commands with root permissions.  ```
sudo dpkg --configure -a
```

Try again and you may get it to work that way.

---

### Post by n00bupgrade on 2011-11-07
Hi ajgreeny

Thanks for your reply. Actually I ran with root permissions. Sorry my initial post is not clear. I will modify it.

---

### Post by matt_symes on 2011-11-07
Hi

Try purging and reinstalling the software center.

```
sudo apt-get remove --purge software-center
```

Reconfigure again.

```
sudo dkpg --configure -a
```

```
sudo apt-get install software-center
```Upgrades can always be problematic. Consider backing up your files and installing a fresh 11.10 .

Kind regards

---

