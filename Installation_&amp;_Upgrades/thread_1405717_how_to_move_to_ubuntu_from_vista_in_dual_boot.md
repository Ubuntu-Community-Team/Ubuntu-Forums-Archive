---
title: "how to move to ubuntu from vista in dual boot"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by prakashsairam on 2010-02-13
hi,
i installed ubuntu 9.10 in my hp laptop with windows vista (not genuine) as dual boot.at present both are working fine.my question is my windows needs activation  and i am not going to activate it what happens after 120 days trail period ,will this dual boot work or windows will crash which will inturn affect ubuntu?.is there anyway to now have only ubuntu and uninstall vista ?or this dual boot work well even after 120 days trial period my concern is my ubuntu working fine now will it work like that forever?.help needed guys.
thanks.

---

### Post by lenoirrichelieu on 2010-02-13
1. After trial period Windows will not let you "use" it without activation. This will be related to Windows not to Ubuntu or whatever Linux distribution you will use.
 
2. Ubuntu will not crash as it is not depended on a valid/legit/working Windows.
 
Grub just let you boot in different operating systems but it doesn't care if one of them is working or legit.
 
Of course is possible to have only Ubuntu. Just format the partition where Windows exists then run in terminal *sudo update-grub. *So Windows is gone and Grub wil find no other OS and updates the menu list.

---

### Post by prakashsairam on 2010-02-13
thanks lenoirr for your reply.i am worried for some time about this now i am happy to know that my ubuntu will be safe and i need not worry about windows activation.once again thanks .

---

### Post by lenoirrichelieu on 2010-02-15
If you decide wo wipe Windows beware not to wipe the partition where Grub is installed. If this is the case then format the partiotion from ubuntu and reinstall Grub before leaving Ubuntu's world.
:D

---

### Post by prakashsairam on 2010-02-15
dear leinorr,
as i am not sure how to partision using Gpart package ,i boot into vista then restart using live cd then clean install it(wiped out windows vista) from there.now i have moved to full ubuntu system.thank you .

---

### Post by recluce on 2010-02-15
I am not sure about Vista, but on Windows 7 (not the RC) all that happens after 120 days is that you get a black desktop background and a nag screen on boot-up. But since you may also not get security patches any longer, this cannot be recommended.

---

