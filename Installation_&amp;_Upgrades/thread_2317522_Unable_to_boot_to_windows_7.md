---
title: "Unable to boot to windows 7"
date: 2016-03-17
forum: Installation &amp; Upgrades
---

### Post by dbb632 on 2016-03-17
I tried to upgrade to wily werewolf and my computer froze. So I downloaded it onto a bootable flash drive and installed it that way. It gave me options to install again over the failed attempt. I chose that option thinking it would just upgrade over the last attempt without damaging windows 7. Now when I boot up it only gives me the option to boot to Ubuntu and not windows 7. There is no boot option listed. I tried to disable UEFI through boot options which only led to an HDD not found error. I then went into BIOS and changed it to legacy. Ubuntu still boots but windows 7 is not in the list of OS boots. 
  I'm not sure how to resolve this so if anyone has any ideas I would like to know

---

### Post by Edison_James on 2016-03-17
A screen shot of your partition table would be helpful, to give us an idea of what may have happened.

---

### Post by dbb632 on 2016-03-17
> **Edison_James said:**
> A screen shot of your partition table would be helpful, to give us an idea of what may have happened.


Actually it was a simple issue after all. I simply opened a terminal and ran 

sudo update-grub

That took care of the issue

---

### Post by Bucky Ball on 2016-03-17
Good news. Please see the first link in my signature below and happy travels.

---

### Post by Edison_James on 2016-03-17
> **dbb632 said:**
> Actually it was a simple issue after all. I simply opened a terminal and ran 

sudo update-grub

That took care of the issue

Glad it worked out for you.:)

---

### Post by RobGoss on 2016-03-17
Always good to see a happy ending

---

### Post by Bucky Ball on 2016-03-18
> **Bucky Ball said:**
> Good news. Please see the first link in my signature below and happy travels.

Done.

---

