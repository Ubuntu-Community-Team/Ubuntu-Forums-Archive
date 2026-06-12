---
title: "Dual Boot Problem."
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Abdul Jabbar on 2013-04-06
Hi hope you'll be fine......!!
Bual Boot:: 
  I have windows 8 in my laptop (Dell inspiron 5521) and i want to make it dual boot. mean i want to install ubuntu with windows 8, i try to install. i made a 50GB partition and install ubuntu in this 50GB paartition. 
But unfortunality it does not install and aslo currepted my windows 8. 
when i boot the system,system ask me which OS you want to run. but both OS showing error both are not working, and my system stuck there.!
please help me to solve this problem, i want to make it dual boot becouse i dont want to use any virtualization.
email:    (me wating please)

---

### Post by moody_mark on 2013-04-06
Looks to me like you have installed Ubuntu and its overwritten the windows MBR so neither will boot, although usually in this situation your Linux OS will boot but not the windows partition. Usually windows 8 PCs will use UEFI on newer computers. Have a look at some of these community guides and see if these can help you at all

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2013-04-06
Removed your email. You may get a lot of spam if left in as forum is scanned. We also are a forum where all users contribute to answers and need to see what else has been suggested to avoid duplication. We all are volunteers.

If your Windows was pre-installed, moody_mark links are a good start.

Post your BootInfo link, so we can see the details of where you are at.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

