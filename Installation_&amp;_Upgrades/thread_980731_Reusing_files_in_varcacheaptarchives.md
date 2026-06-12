---
title: "Reusing files in /var/cache/apt/archives/"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by owen_cook on 2008-11-13
This question must be asked all the time but not even Google has an answer

I have just installed for the second time 8.10, and for the second time collected 515 MBytes of debs in /var/cache/apt/archives/

I really would like to put those debs on a cd so next time I wipe the installation, or do it on another machine or partition, I don't have to download them all again.

Can I do this and if so how?


TIA


Owen

---

### Post by Steve1961 on 2008-11-13
Sure, just copy them to a cd or usb stick.  When you want to install them on a system just open a terminal and cd to the directory where they're saved and do a sudo dpkg -i *.deb

---

### Post by akudewan on 2008-11-13
> **Steve1961 said:**
> Sure, just copy them to a cd or usb stick.  When you want to install them on a system just open a terminal and cd to the directory where they're saved and do a sudo dpkg -i *.deb

Another alternative is to copy these .debs back to /var/cache/apt/archives/
 and then simply run apt-get install <packages>

I actually did this after I installed Ibex. My friend had all the new updates downloaded, and I took his cache over the LAN. Saved me around 250MB of download. Thats a lot, since I have a 128kbps connection :)

---

### Post by owen_cook on 2008-11-14
Thanks to both of you and will try that next time. Need to think a bit clearer!

---

