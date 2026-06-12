---
title: "Password changed by system?"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by rektiphyr on 2011-12-24
Hi, I installed Ubuntu 11.10 x64 and everything went smoothly. Once I hit the desktop I installed updates and rebooted. Upon reboot I was able to login to unity, but when I try to sudo it says incorrect password attempt. I rebooted into recovery mode to change the password from the root shell, which seemed to work. While still in the root shell I was able to login as myself, and I set the passwords for both my user and the root account. But when I rebooted -- same problem again. It was as if I had done nothing. I thought maybe it was just a quirk in 11.10, and after reading about a few more 11.10 bugs I decided to just downgrade to 11.04. 

Again, same story. I installed, updated, and when I rebooted, my password allowed me to login to the desktop, but not do anything in the terminal.

I'm really at a loss here. Does anyone know what might be causing this?

---

### Post by fdrake on 2011-12-24
> **rektiphyr said:**
> Hi, I installed Ubuntu 11.10 x64 and everything went smoothly. Once I hit the desktop I installed updates and rebooted. Upon reboot I was able to login to unity, but when I try to sudo it says incorrect password attempt. I rebooted into recovery mode to change the password from the root shell, which seemed to work. While still in the root shell I was able to login as myself, and I set the passwords for both my user and the root account. But when I rebooted -- same problem again. It was as if I had done nothing. I thought maybe it was just a quirk in 11.10, and after reading about a few more 11.10 bugs I decided to just downgrade to 11.04. 

Again, same story. I installed, updated, and when I rebooted, my password allowed me to login to the desktop, but not do anything in the terminal.

I'm really at a loss here. Does anyone know what might be causing this?

with your username type in the terminal and post here :
```

groups

```

---

### Post by rektiphyr on 2011-12-24
mike@Thor:~$ groups
mike adm dialout cdrom plugdev lpadmin admin sambashare

---

### Post by fdrake on 2011-12-24
try to reinstall sudo (as root) and reboot:
Press Ctrl+Alt+f1 and login as root, type:
```

apt-get purge sudo && sudo apt-get install sudo gnome-sudo
reboot 0

```

let as know if the problem persists .. a lot of other ppl have experienced the same issue.. may I suggest you to try a 32 version next time, only for debug advantages

---

### Post by rektiphyr on 2011-12-24
Thank you for your help, I've solved the problem. Turns out it was a keyboard layout issue. While in the root shell it was using the "Canada" keyboard, but once I logged into unity it switched to "Canada English". That resulted in my password having a / where there should have been a #. 

A very silly issue, and it was probably because I selected "Canada" as the keyboard layout during installation, and later changed it from unity.

Again, thank you for your help :)

---

### Post by fdrake on 2011-12-24
glad it did not turn on to be an annoying bug :D !

---

