---
title: "Installing linux on slave drive , windows on master"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by DB6150 on 2007-10-28
can i install linux 7.10 onto my slave drive , and then make it so that windows is the OS that automaticly boots after X ammount of seconds if another os is not selected? 

thanks

---

### Post by Pumalite on 2007-10-28
Sure. You just have to change a couple of things in your menu.lst at the end of the installation.

---

### Post by DB6150 on 2007-10-28
Ok thanks! 

when its done downloading and installed ill post back and tell you what happens :)

---

### Post by ratatosk13 on 2007-10-28
If you use cable select on the drives, GRUB will handle it for you. This is how I handled the dual-boot on my main system. 

I've never tried using a master/slave setup for a dual boot, so I don't know that it would necessarily cause you problems. Are you saying that you tried the install using the master/slave configuration and it didn't work?

Best of luck.

---

### Post by skompier on 2007-10-28
I dual boot with a master and slave drive. Master has XP and slave is Feisty. I default boot into Feisty. The ONLY problem I have and you MAY see it also, is that when I first turn on my PC, I get a GRUB 21 error. I've researched this for awhile and haven't tried to fix it really. All I have to do is a cntl-alt-del and then the GRUB menu shows. So if you see this...DON'T PANIC. This only happens during a cold boot.

---

### Post by DB6150 on 2007-10-28
ok its installed onto the slave drive and it is the default OS , what i am trying to accomplish is to make Windows the Default OS , and for it to load automaticly instead of XP

---

### Post by Pumalite on 2007-10-28
You have to change the 'default' line in your menu.lst from '0' to the number where windows is located minus one (Grub starts counting from 0)

---

### Post by DB6150 on 2007-10-28
> **Pumalite said:**
> You have to change the 'default' line in your menu.lst from '0' to the number where windows is located minus one (Grub starts counting from 0) 

im sorry , but i am new to ubuntu , could you please put this in simplier terms?

---

### Post by skompier on 2007-10-28
> **DB6150 said:**
> im sorry , but i am new to ubuntu , could you please put this in simplier terms?

Read this... [http://ubuntuforums.org/showthread.php?t=578647&highlight=change+boot+order](http://ubuntuforums.org/showthread.php?t=578647&highlight=change+boot+order)

---

### Post by DB6150 on 2007-10-28
Perfect thank you, it all works great:)

---

### Post by skompier on 2007-10-28
> **DB6150 said:**
> Perfect thank you, it all works great:)

Glad we were able to help. Enjoy...:)

---

### Post by DB6150 on 2007-10-29
One more question. 

does 7.10 have gparted from 7.04 or something similar so i can partition this drive and take 200 gb and give it to windows for backups?

---

### Post by Pumalite on 2007-10-29
sudo apt-get install gparted

---

