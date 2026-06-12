---
title: "&quot;Newbie&quot; need to know how to install a driver"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by joecagle77 on 2008-04-09
I downloaded NVIDIA-Linux-x86-169.12-pkg1.run for my Geforce FX 5900. I dont know how to install it can someone walk me thru. I double click it and it run in the terminal but says it has to be ran as root. What does this mean>?

---

### Post by chewearn on 2008-04-09
Before you install this driver directly from nvidia, have you tried the easier/safer driver in the repositories?

System > Administration > Restricted driver manager

If this method does not work, and you insist to install the nvidia website driver, then go back to that website; the instructions in the website should be very clear on what you need to do.

---

### Post by Pumalite on 2008-04-09
Do it in a Virtual Terminal. Have your driver on the Desktop.
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
password
sudo sh /NVIDIA-Linux-xxxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx

First:
sudo aptitude install build-essential

---

### Post by joecagle77 on 2008-04-09
so, I should do a shut down put the card in and see what linux suggest?

---

### Post by chewearn on 2008-04-09
> **joecagle77 said:**
> so, I should do a shut down put the card in and see what linux suggest?

Yes, ubuntu will auto-detect the new card; most of the time, it's good enough to automatically prompt you to install nvidia driver.

---

