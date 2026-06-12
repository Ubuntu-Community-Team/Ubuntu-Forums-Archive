---
title: "Triple boot to 11.04, 12.04, 12.10. It won't boot to 11.04 anymore."
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by vincegata on 2012-11-21
Hi,

I have that triple boot but after last night I played with rsync backing up files to external drive connected over USB, my  laptop will not boot into 11.04.

Any suggestions how to fix it? 

Please do not tell me to get rid of 11.04, I just need to boot into it.

Thank you.

Edit: so when I boot into 11.04 it's only cursor blinking in the upper left corner.

---

### Post by oldfred on 2012-11-21
Just rsync should not have changed booting. Best to see what is where:

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by vincegata on 2012-11-22
I fixed it, thank you!

---

