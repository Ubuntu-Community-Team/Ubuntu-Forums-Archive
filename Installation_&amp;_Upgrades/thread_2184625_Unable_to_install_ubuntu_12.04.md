---
title: "Unable to install ubuntu 12.04"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by fardinsaiyyed on 2013-10-30
I have HP dc 7800p small form factor PC
i have to install UBUNTU 12.04 but when it boot it load system and take me to the command screen and show message 
"General error mounting filesystems. 
A maintenance shell will now be started. 
CONTROL-D will terminate this shell and reboot the system 
root@(ubuntu):"



I have delete all partition having windows XP... but still its shows same massage....


PLz help......

---

### Post by Toz on 2013-10-30
*Thread moved to **Installation and Upgrades***
Edit: Also removed duplicate thread. Please do not create duplicate threads, it dilutes community effort. Thank you.

---

### Post by Bucky Ball on 2013-10-30
Is this when booting directly from the install CD? What happens when you hit CONTROL+D? Does it loop back to:

```
root@ubuntu:
```

From your post I am a bit unclear as to whether you have actually managed to install Ubuntu and this is what you get when you boot or this is what you get when you boot from the install CD ...

---

### Post by fardinsaiyyed on 2013-10-30
when i press control D system gets restart and again it start booting for ubuntu 12.04 and 

"General error mounting filesystems. 
A maintenance shell will now be started. 
CONTROL-D will terminate this shell and reboot the system 
root@(ubuntu):"
 
here it come....

---

### Post by mastablasta on 2013-10-30
boot into live session and post a picture from gparted or post result of 

```
df -h
```

---

### Post by fardinsaiyyed on 2013-10-30
problem solved.... i installed it via usb

---

### Post by mörgæs on 2013-10-30
Did you read Bucky Ball's signature?

---

### Post by Bucky Ball on 2013-10-30
> **mörgæs said:**
> Did you read Bucky Ball's signature?

... and just in case you didn't:
> 
To help others please mark threads 'Solved' using Thread Tools at top right.

---

