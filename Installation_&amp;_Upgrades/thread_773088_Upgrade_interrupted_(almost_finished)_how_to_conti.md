---
title: "Upgrade interrupted (almost finished) how to continue?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by lugburz on 2008-04-28
I was upgrading ubuntu 7.10 to 8.10. When the process was almost done, firefox (I was visiting few web pages waiting) freezed the screen. I waited for a while to try to wait that update manager had done.

When the disk and processor didn't have activity (panel applet continued to work) i rebooted the system. Now the hardy installation seems to work but I'm not sure that all the installation steps are done: i.e. system cleaning.

Have someone a suggestion how to know if some step is missing?

thanks in advance.

---

### Post by lugburz on 2008-04-28
Looking better I found a wrong beaviour: any time I restart the laptop the normal hraphical scrollbar after few seconds disappear, chainging with the old-fashion text messages composed of :

init... [done]

---

### Post by Pumalite on 2008-04-28
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade.

---

### Post by lugburz on 2008-04-28
I tryied and all seems ok. 

Looking into the /var/log/dist-upgrade/main.log the last message notices that the installer has found the obsoete packages. I removed them with "apt-get autoremove".

---

### Post by Pumalite on 2008-04-28
Congrats.

---

### Post by lugburz on 2008-04-29
Thanks, but the start issue continues and I'm thinking that this could be related with the problem I have trying to hybernate the laptop: it resumes as I had shutdown without attempting to resume anything.

---

### Post by Pumalite on 2008-04-29
Fot laptops to hibernate, /swap must be equal to RAM.

---

### Post by lugburz on 2008-04-29
This is exactly my case 1.5GB of Ram ->1.6 GB of Swap. I'm now able to suspend after removed the sonypi module, but the issue with the hyberantion seems something different.

I'm continuing to think that could be related with the boot behaviour.

---

### Post by lugburz on 2008-04-29
Solved!!!

One step was also missing: "update-initramfs", running this command graphical login and hibarnation began to work well. Suspend still have some random problem but I'm investigating.

---

