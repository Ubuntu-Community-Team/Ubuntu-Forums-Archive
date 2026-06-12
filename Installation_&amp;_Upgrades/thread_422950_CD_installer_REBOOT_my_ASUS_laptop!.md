---
title: "CD installer REBOOT my ASUS laptop!"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by olgias on 2007-04-25
I've an ASUS M3452 laptop,
I boot from the Desktop CD installer,
select "Start or install Ubuntu",
and after 5 seconds it reboots!!!!

Does anyone has any idea???


Thanks.

---

### Post by The Gladiator on 2007-04-25
I have a laptop Asus M3N and I have your same problem. 

I can add more details hoping that they could help: I also tried to install Ubuntu 7.04  (Feisty Fawn) on a USB pen drive in persistent mode as explained in this document [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) :
after the splash screen with the Ubuntu logo and the two messages "loading vmlinvz" and "loading initrd.gz" my computer was restarted.

Of course I'd be more than happy to provide you additional details about my laptop if you need.

---

### Post by The Gladiator on 2007-04-26
despite my never-ending efforts I'm frozen where I was without your precious help, please..... Thanks

---

### Post by The Gladiator on 2007-04-27
Final answer to this issue: 
F6 on the starting menu
add ACPI=OFF to the parameters line

---

### Post by olgias on 2007-05-30
I CAN'T INSTALL UBUNTU ON MY ASUS NOTEBOOK!!!

That's incredibile!!!

After I select Install Ubuntu it reboots!!!!

Please HELP ME!

Thanks a lot!

---

### Post by fsando on 2007-06-01
Could you please elaborate a little?
Did you try the above advice?

---

### Post by olgias on 2007-06-03
I found the solution!

"nolapic"

---

