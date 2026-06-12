---
title: "Which drivers for Nvidia-geforce video card?"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by G.R. on 2010-10-23
p { margin-bottom: 0.08in; }  *I had problems installing 10.04 and 10.10 with my nvidia card, (blinking cursor when running livecd so had to use nomodeset, but couldn't figure out what to do after 10.10 was installed as I single boot and couldn't get Grub to come up to choose nomodeset again upon first boot) * 
 

 *So what I have done is I have installed 9.10 with the plan to update to 10.10. However, before doing this I need to install the Nvidia drivers for my video card – Nvidia geforce 210 MD512 (512 MB) because not doing this results in the same initial problem after upgrading. I think it has to do with the fact that 10.04 uses a new version of xorg. I saw on the thread below that there were drivers for 256.xx stable and 195.xx stable Open GL3.3. Which drivers should I install? * 
 

 *[http://ubuntuforums.org/showthread.php?t=990978&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=install+nvidia)*
 

 *Thanks!*

---

### Post by ronparent on 2010-10-23
Hold the left shift key while boot through bios to bring up a grub boot menu. After continuing the boot with the nomodeset uption, use the menu header System>Administration>Additional Drivers to install the drivers you need. It probably won't be the same as 9.10.

---

### Post by G.R. on 2010-10-24
Thanx for your reply. I installed 10.10 and reboot I hold shift. Then I enter Grub boot menu, but now I don't know how to continue in normalset mode? 
Thanx again

---

### Post by ronparent on 2010-10-24
Hit 'e' for edit and add nomodeset to the kernel boot line (the line beginning with vmlinuz....etc). When edited boot with <ctrl>x.

---

### Post by G.R. on 2010-10-24
Hi, 

I solved the problem.  I added nomodeset to the kernel boot line, and I deleted quiet splash.
Thanks for your help!

---

### Post by ronparent on 2010-10-24
You are not done yet. You need to install the driver (System> Administration > Additional drivers). Then you will be done because the nomodeset was tempoary only for that boot.

---

