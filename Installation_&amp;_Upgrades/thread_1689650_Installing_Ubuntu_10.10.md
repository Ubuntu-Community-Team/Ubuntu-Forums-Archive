---
title: "Installing Ubuntu 10.10"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by makinasvp on 2011-02-17
Hello all, I have a quick question because I don't want to make a very dumb mistake lol
Anyways, I have 2 HDDs installed on my computer. Both of them are 500GBs. Now one of them I am using with Windows 7. That's what my computer is currently running. Now my other one I'm not really using for anything except for storage, but I got an external HDD for that now and would like to install Ubuntu on it.
Now, will it mess up my Windows 7? As in if I install Ubuntu 10.10 on this HDD, will it still let me go to my Windows 7 operating system so that I can play my games? Or will it not let me use Windows 7 anymore? What should I do...? Somebody please help me

---

### Post by makinasvp on 2011-02-17
oh and which one do I need to pick if I can do this? 

-Install alongside other operating system
-Erase and use the entire disk
-Specify partitions manually (advanced)

---

### Post by YesWeCan on 2011-02-17
Yes, you can have both without messing up Windows.
First, I would disconnect you Windows disk before you try installing Ubuntu. That way you are guaranteed not to mess it up.
Install Ubuntu on your spare disk. Choose erase and use entire disk.
Once Ubuntu is working, shut down and reconnect your Windows disk. Configure the bios to boot first from the Ubunu disk. Restart and once in Ubuntu type this in a console 'sudo update-grub'
The next time you boot you will get a menu that gives you a choice of Ubuntu or Windows.

---

### Post by makinasvp on 2011-02-17
> **YesWeCan said:**
> Yes, you can have both without messing up Windows.
First, I would disconnect you Windows disk before you try installing Ubuntu. That way you are guaranteed not to mess it up.
Install Ubuntu on your spare disk. Choose erase and use entire disk.
Once Ubuntu is working, shut down and reconnect your Windows disk. Configure the bios to boot first from the Ubunu disk. Restart and once in Ubuntu type this in a console 'sudo update-grub'
The next time you boot you will get a menu that gives you a choice of Ubuntu or Windows.

Thank you so much!

---

