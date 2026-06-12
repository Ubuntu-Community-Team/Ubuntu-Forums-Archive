---
title: "Installing packages on another computer (Solved)"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by slapout on 2006-10-23
I have two machines with Ubuntu installed. One has a high speed internet connection and the other one does not. What I'd like to do is download packages on the one with the fast connection and then transfer them and install them on the other computer. Is this possible? And if so, how would I go about it? 

Thanks

---

### Post by aysiu on 2006-10-23
All the installer files from *aptitude*/*apt-get* or Synaptic/Adept are in /var/cache/apt/archives

Copy those .deb files to your slower connection computer's desktop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by slapout on 2006-10-23
Thanks!

---

### Post by aysiu on 2006-10-23
> **slapout said:**
> Thanks!
Thank me when it works.

---

### Post by slapout on 2006-10-24
It worked. Thanks! I burned the files to a CD and copied them to the other computer.

---

