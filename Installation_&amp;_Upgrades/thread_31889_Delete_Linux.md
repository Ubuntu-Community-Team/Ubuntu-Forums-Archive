---
title: "Delete Linux"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by ashokmani on 2005-05-05
Hi, i am newbie. Please help me.

This is just a precautionary measure which i need to know before trying linux. 

i currently have Win XP and i have two partitions. Please tell me what i have to do , if i have to delete linux from the 2nd partition and make the space available for windows ie as NTFS.  ](*,) 


Thanks in advance. 

Note : has anyone tried installing ubuntu in a compaq v2000 series notebook?


Regards,
Ashok

---

### Post by Leif on 2005-05-05
Under XP, you can use the disk management tool to wipe the linux partition and make an NTFS partition instead. You will also probably want to remove grub, the bootloader. For that, you boot XP into recovery mode and use fixmbr. So there's no risk about trying linux out at all.

---

