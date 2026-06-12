---
title: "Windows XP and ubuntu 7.04 help!!!"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Ryan Sullivan on 2007-06-06
Hello, i recently install ubuntu 7.04 with a dual boot with my windows XP. I follwed all the steps perfectly.
But there is one problem, after install GRUB to the MBR, when i try and boot windows, i get a BSOD witch lasts like a milisecond and then my computer restarts.

No i haven't mad any mistakes while partitioning.
But i think it has something to do with installing GRUB on the MBR.

What i would like to know is. What would happen if i didn't install GRUB at all??

Would i get booted into windows or would i get booted into ubuntu. Because i was thinking of using a supergrub disk that i have.

If anyone has any other solution to this problem, please help!!!!

Thanks.

---

### Post by Dedoimedo on 2007-06-06
Hello,
Disable auto-restart when BSOD in Windows and try to see what the error is.
Does this happen every time?
Dedoimedo

---

### Post by Ryan Sullivan on 2007-06-06
Yes, it does happen verytime that i try and login to windows XP, i don't know what is going wrong and i'm trying to figure it out but i can't.


Any ideas??

---

### Post by Dedoimedo on 2007-06-06
Hello,
Backup GRUB, reinstall MBR, see if this solves the problem?
But first, I really suggest you try to see the actual message on the BSOD.
Dedoimedo

---

### Post by Ryan Sullivan on 2007-06-06
I have already reset the MBR. I used FIXBOOT and FIXMBR and i had to get rid of the ubuntu partition so enter windows. Ill try and reinstall ubuntu but this time ill install BRUB on the first part of the boot sector. If this doesn't work and i get a BSOD ill give you the info that the BSOD gives me.

Thanks again.

Ryan Sullivan.

---

