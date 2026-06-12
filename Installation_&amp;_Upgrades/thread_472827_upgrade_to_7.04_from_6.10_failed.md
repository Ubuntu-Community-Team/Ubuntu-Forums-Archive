---
title: "upgrade to 7.04 from 6.10 failed"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by cdewalt on 2007-06-13
I am running on Dell Dimension 8200. Been using 6.04 for about 2 years.  Decided to upgrade to Feisty.

First I tried 6.04-6.10-7.04 via update manager but ran into library problems I suspect as the install to 7.04 did not work properly.  7.04 had problems recognizing eth0 consistently and it ran slow i am pretty sure there was a library conflict.  It wasnt stable.

Next I got the 7.04 iso to CD rom.  Tried to install that directly (figured that would be easier than doing upgrade) however the install CD booted to ubuntu requiring user name/password install of the install screen i was expecting.  I could not find what the default password was anywhere on forums (tried ubunutu and no password but that didnt work).

Next i switched back to 6.10 install disk.  Worked great installed 6.10 on my 40 G hard drive and formatted it to get rid of windows XP (for good!).

Next I upgraded to 7.04 via update manager.   However this did not complete successfully. I have attached the logs.

I anyone can tell me 
a. what i need to do to upgrade 6.10 to 7.04 via update manager that would be great.
also
b. anyone know what the username password should be for the 7.04 install disc? I would like to do a clean install 7.04 next time and i must have missed it because I thought i downloaded and created the 7.04 iso properly using Nautulis.

thank you to everyone on the forums it is a great help.

---

### Post by cdewalt on 2007-06-13
here are logs

---

### Post by stchman on 2007-06-13
I always do a clean install.  I have never had any luck with the upgrade manager way.  It actually takes longer to do the upgrade manager way than the clean install way.

---

### Post by Pumalite on 2007-06-13
> **stchman said:**
> I always do a clean install.  I have never had any luck with the upgrade manager way.  It actually takes longer to do the upgrade manager way than the clean install way.

I recommend a clean install too. Make sure your install CD is OK. Do a checksum. There is no password for a 7.04 CD install that I'm aware of. Also is better to use Gparted first to prepare your partition.

---

