---
title: "Cant boot windows after upgrade"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2011-04-20
Hi, can anyone tell me how to get the boot screen back when ubuntu is booting up, I installed 11.04 like I ususally do when I upgrade but this time it does not show the kernel loading and the option to boot windows, I know windows it still there, I just need to be able to boot it. Thank you inadvance.

---

### Post by Quackers on 2011-04-20
From within Ubuntu start up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader is found. If it is reboot and you should see a grub menu with boot options.

---

### Post by wildmanne39 on 2011-04-20
Hi, thank you I think that took care of that part,but I cant tell for sure because my screen is blank for more then 10 seconds, but I also got a message input display settings are out of range, when I try to change them to the setting it told me too, it wont let me, but in my nvidia settings it will but the display settings from ubuntu is over riding it. Can you tell me how to manually change the display settings? Thank you so much.

---

### Post by Mark Phelps on 2011-04-21
Ubuntu 11.04 is still in testing.  This thread is reserved for Ubuntu versions that have already been released.

You will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion

thanks

---

### Post by wildmanne39 on 2011-05-06
Hi, I just wanted to think you for your help, sorry it took me so long to get back to you it has been kind of crazy for me lately.:D

---

