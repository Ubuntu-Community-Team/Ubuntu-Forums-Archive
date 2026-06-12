---
title: "fix boot to a cloned ubuntu via clonezilla?"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by elim-qiu on 2014-03-21
I have a nice Ubuntu 13.10 installation on one D430 laptop and like to  copy it to a messed up D430 (Mainly about complicated typo3 requirements).

So I saved ubuntu partition img from the good one and restored to the messed up one. Seems all the directories and files are copied. But the messed one can boot to xp and SL but not ubuntu anymore.

Ubuntu was restored to partitions sda7 (/) and sda8. I'm pretty sure if I can reinstall grub into sda7, everything will be fine. But I'm not sure exactly what to do or which guide to follow.

I do have a Ubuntu Live usb and tried boot-repair but not working, I installed and run it but it just scanning the HDD for ever. So I guess that I need a manual fix with terminal....

Appreciate your help!

---

### Post by ibjsb4 on 2014-03-24
Have you found a souition?

---

### Post by u_i_we_all_buntu on 2014-03-25
Just a few questions....

Can the messed up D430 boot Ubuntu 13.10 using a bootable USB?  
If not, check if it can boot into a 12.04 USB stick.
If it can't boot using a live 12.04 bootable USB stick, 
do an feature-by-feature comparison between the two D430s.

- A good way to do so is by checking the features on the BIOS setup, 
- or by entering the unique **service tag** (on Dell label at the bottom/back of the laptop)
  into the Dell support site:  [http://www.dell.com/support]("http://www.dell.com/support") ,
  and get a listing of the original configuration of each system.

Hope this helps...

---

