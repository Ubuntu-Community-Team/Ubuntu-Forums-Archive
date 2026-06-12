---
title: "Missing Operating System"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by X0G on 2008-02-05
I was going to install 7.10 ubuntu.

I started it up and clicked Install, then I let the installer get to 100%, the installer went away  so I figured it was done, and restarted. Then i got the Missing Operating System message.

Ive tried to reinstall it multi times but i keep getting this message, is anything else supposed to happen after the install goes to 100 percent?

I have an Everex Stepnote va4101m laptop

---

### Post by seshomaru samma on 2008-02-05
towards the end of the installation there is a part where it asks whether you want to install GRUb to the MBR - you need to choose "yes" ,it will then install GRUB . pay attention to this stage - make sure the installer doesnt report any errors and if it does post them here

---

### Post by X0G on 2008-02-06
> **seshomaru samma said:**
> towards the end of the installation there is a part where it asks whether you want to install GRUb to the MBR - you need to choose "yes" ,it will then install GRUB . pay attention to this stage - make sure the installer doesnt report any errors and if it does post them here


I never got that part.

I click the Install and it starts installing for a bit, then at around 94 percent it just closes and nothing happens

and im getting a grub load error 15 when i try to start ubuntu up

---

### Post by manzoor on 2008-02-06
yes there is no part of where to install GRUB IN 7.10


is there any other wy

---

### Post by seshomaru samma on 2008-02-06
I would imagine this is due to faulty install media
It is important to burn at the lowest speed possible and check the CD for errors before you start installation. Also [check md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") 
About 80% of problems I had with installation were due to bad burns.

I suggest burning another copy and trying again.

---

