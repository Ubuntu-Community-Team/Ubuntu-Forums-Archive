---
title: "Having issues with update"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by deadbeatofdharma on 2008-02-28
I just installed ubuntu 7.10 today out of curiosity.  Installation went great, but when I ran the update manager my computer froze and I had to reboot in the middle of the process.  Seems it corrupted a file because now it's giving me this prompt when I try to restart the update:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am brand new to Linux and have no idea how to manually run a program and fix the issue.  Any help is appreciated.

---

### Post by deadbeatofdharma on 2008-02-28
I just tried to run the command 'dpkg --configure -a' in the terminal and it tells me that I need superuser privileges to run the command, but I am the only user

---

### Post by chewearn on 2008-02-28
Add "sudo" in front of the command to run the command with root privileges.  Like this:

```
sudo dpkg --configure -a
```

It will ask you for your user's password.

---

### Post by deadbeatofdharma on 2008-02-28
Seems to have worked.  Thanks.

---

