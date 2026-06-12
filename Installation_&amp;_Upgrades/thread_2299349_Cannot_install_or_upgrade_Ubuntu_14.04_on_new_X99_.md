---
title: "Cannot install or upgrade Ubuntu 14.04 on new X99 machine: machine restarts"
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by h3x4d3c1m4t0r on 2015-10-17
Hi,

I have a new machine with specs:
Asus X99-A mobo; Intel i7 5930K CPU; Nvidia GTX Titan X graphics; 32GB Corsair RAM; 500GB Samsung SSD; Corsair H80i water cooling

I had some difficulty installing Ubuntu 14.04.3 from a Live USB. The computer would often spontaneously restart during installation (at different points of the process each time).

After several attempts I was able to install and boot Ubuntu on the machine. However, now when I attempt to update (apt-get upgrade) the machine or attempt to switch the graphics drivers from Nouveau to the proprietary ones, the computer spontaneously restarts again. If I leave it running idle for a while (5 or 10 minutes), it eventually restarts.

I have checked the reported CPU temperature and it does not seem high (42 deg C).

When I press Ctrl-Alt-F1 I get a blank screen, but I can return by Ctrl-Alt-F7 (both on Live USB and after installing).

When I boot in recovery mode and then run FailsafeX, it freezes after a few seconds.

Sometimes it switches off before I get to Grub. Sometimes it displays the BIOS screen with "Overclocking failed. Press F1 to enter setup". I am not overclocking.

I have been able to access a root shell via booting in recovery mode. From here, I can do apt-get upgrade. I can also then enable the Nvidia drivers via apt-get install nvidia-current. However, after I restart, I am not able to log in to a graphical session (I enter my password and then it thinks for a second and returns to the login screen), although Ctrl-Alt-F1 has begun to work.

The BIOS version is reported as 0001, although I am somewhat anxious about upgrading the BIOS.

I have tried with an Nvidia GTX Titan Black instead and the situation was much the same.

Any ideas what the problem could be? What should I try next?

Thanks,
Jack Valmadre

---

### Post by mörgæs on 2015-10-19
Hi, there seems to be surge of questions where 14.04 is failing on new hardware. This is not surprising, it would indeed be surprising if such old software worked.

How does it behave in a fresh install of 15.10?

---

### Post by james_moore2 on 2015-10-19
Excuse me for my simple answer, but I would try deleting Ubuntu, then reinstalling it on the live disk/USB, then trying again, this fixed my problem although I used a stock Toshiba Satellite S5112-L755.

---

### Post by h3x4d3c1m4t0r on 2015-10-22
Thanks for the suggestions!

I'm sorry, it was a hardware problem!

I called the company that I bought the computer from and they advised me to remove the battery from the motherboard to cause the BIOS to reset. This fixed everything.

---

### Post by james_moore2 on 2015-10-22
Ah, sometimes the most simplest things fix the most complex problems.

---

