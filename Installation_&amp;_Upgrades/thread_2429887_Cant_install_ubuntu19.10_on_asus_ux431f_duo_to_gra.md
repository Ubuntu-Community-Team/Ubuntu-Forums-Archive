---
title: "Cant install ubuntu19.10 on asus ux431f duo to graphical problem"
date: 2019-10-24
forum: Installation &amp; Upgrades
---

### Post by yotam3 on 2019-10-24
Hello everybody, just bought a new asus zenbook model ux431f with nvidia mx150.
I downloaded the new version 19.10 and try to install the system from live usb (made from another Ubuntu 18.04). I already have windows 10 and want to install Ubuntu beside
After i boot from the usb, i saw the text menu in bad resolution and quality. when i choose something, the screen freeze and nothing happened. It happend twice, ones when i tried to install and second when i tried to use the live system.
I think it might be problem with the drivers of Nvidia mx150 because the frozen screen.

The life usb works on other computers.
Thank you very much for the help.

---

### Post by mörgæs on 2019-10-25
Have you tried boot options like nomodeset?

---

### Post by yotam3 on 2019-10-25
No, actually I didn't. What is that options? I saw the sticky subject here in the forum but can't find any practical solutions. Where can i read about it? Thanks alot

---

### Post by mörgæs on 2019-10-25
For example here:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing](https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing)

---

### Post by yotam3 on 2019-10-26
i tried it now, just complete to install ubuntu after i boot with nomodeset option.
the install was ok, no problems.
but now,after the reset when i try to boot into the ubuntu, again i get black screen.
how can i fixed it? is it possible to install the nvidia drivers or something like this?
thank you for the help

---

### Post by yotam3 on 2019-10-26
have another problem now.
every time when i tried to boot windows, bitlocker ask me for key recovery and the next reboot also ask me for this key. 
in ubuntu, the nomodeset option did not work now.

---

### Post by mörgæs on 2019-10-26
Let's see more hardware info. In a live boot, with or without boot options, please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post the contents of lshw.txt in CODE tags.

---

