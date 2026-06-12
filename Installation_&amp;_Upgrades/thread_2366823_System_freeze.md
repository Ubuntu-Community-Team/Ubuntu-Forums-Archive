---
title: "System freeze ??"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by mac187 on 2017-07-22
Hi, im new to ubuntu and i have got a big problem..

I just installed a fresh install of Ubuntu yesterday alongside Windows 10,

After it was finished install it told me to restart the system, so i clicked "Restart now"

Then it restarted, i came to login screen, its connected to keyboard , mouse , so i wrote the login passord and push 'Enter' , but heres the problem, when i push Enter everything is gone, i just see mouse cursor, background but nothing more.. The mouse would not move, keyboard dont work.. Anyone know whats the problem?? Pliz help me out


I installed ubuntu 16.04 lts from usb live, i downloaded Ubuntu from ubuntu.com yesterday..

---

### Post by slickymaster on 2017-07-22
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by mac187 on 2017-07-22
I figure this out, when i go to Advanced options for Ubuntu i see these:


Ubuntu, with Linux 4.10.0-27-generic
Ubuntu, with Linux 4.10.0-27-generic (upstart)
Ubuntu, with Linux 4.10.0-27-generic (recovery mode)
Ubuntu, with Linux 4.8.0-36-generic
Ubuntu, with Linux 4.8.0-36-generic (upstart)
Ubuntu, with Linux 4.8.0-36-generic (recovery mode)



When i start with this:
Ubuntu, with Linux 4.10.0-27-generic

system freeze,

when i start with 

Ubuntu, with Linux 4.8.0-36-generic


its work ok, how to solve this???

---

### Post by mac187 on 2017-07-22
Solved it, i know whats the problem was..

---

### Post by slickymaster on 2017-07-22
mac187, care to share with the community the solution?

---

### Post by mac187 on 2017-07-22
Ahh sorry, still having the same problem.. Its freezeing the system and i dont know why, first i want to recovery mode, chosed "fix broken pacakges" then i restarted, i got in and then its freeze again.. I dont know.. in the kernel version [COLOR=#000000]Ubuntu, with Linux 4.8.0-36-generic i didnt have the problem, but the new one make my machine freeze, damnit.. And i dont know how to solve it[/COLOR]

---

### Post by mac187 on 2017-07-22
I got the solution now:

1. Force shutdown and reboot
2. Choose 'Advanced options for Ubuntu'
3. Choose 'Ubuntu, with Linux 4.10.0-27-generic (recovery mode)
4. Choose 'dpkg - repair broken packages'
5. Reboot to Ubuntu again, when you come to login screen, type your password
6. Go to 'Additional drivers' (in my case i choose nvidia driver)
7. Reboot again and its fixed

This made my solution, thanx

---

