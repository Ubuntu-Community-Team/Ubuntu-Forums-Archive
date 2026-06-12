---
title: "Help quick MBR"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by KatieCook on 2007-02-22
Hi, 

 I just did a fresh install , no looking back kinda think with ubuntu only (for now) but.. 


  After install I rebooted and it says: 
Master Boot Record has changed Press anykey to enter setup to restore the MBR

  So I press the any key and get.. 
a restart again then an option for english

  So I hit enter and get brought up to the setup utility..

Please help me from here should I set defaults and exit?
Ignore changes and exit?
Save chages and exit ( I did that and it did not seem to help any) 
Thanks soooo much for the quick help pleeease

---

### Post by Kateikyoushi on 2007-02-22
Is this a notebook ? Ubuntu installed grub in the MBR and seems the machine detected it and wants to restore the original state, if you do that you won't be able to boot ubuntu.

---

### Post by KatieCook on 2007-02-22
No, it is a desktop 
Pnt 4 1.5
512 ram
40 Gig HD


I tried the save chages option and I dont know what else to do but set as defaults , I am kinda stuck.


Some one please help..

---

### Post by Kateikyoushi on 2007-02-22
You have to restore grub to boot ubuntu. Can do it by following these steps [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by KatieCook on 2007-02-22
Hi Katie

  I did exactly what the link said and I am in the same exact spot when I boot up
:confused:

---

### Post by confused57 on 2007-02-22
If you're dual-booting with Windows, it might be your anti-virus program.   If you just have Ubuntu installed, I don't know if there are any bios that have this feature to check & repair mbr...hopefully, there's someone else in the forum  who's had this same problem & may be able to help you.

---

### Post by Kateikyoushi on 2007-02-22
Can't you enter BIOS and disable this feature ? I never heard of this before I can see how it hellps windows users but this completely disables linux.

---

### Post by X-626 on 2007-02-22
You should be able to do that.  My BIOS has that feature, but I have it disabled.  I wouldn't be able to explain how to do it, though (since each BIOS can be so different).  I would look for something in your settings about warning on MBR change.

---

### Post by KatieCook on 2007-02-23
RESOLVED!!!! I do not know how make the first thread say that but THANK YOU SO MUCH.. I read your posts and started poking around in the security settings on the BIOS and wrote down EVERY STEP I DID so if I had to undo it I could.. and I found it in security settings for MBR Security and disabled it.. PROBLEM SOLVED!!!! Thank you so very much!!!!

---

