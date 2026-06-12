---
title: "Install ubuntu on a vista partition?"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by ADZ91 on 2010-02-16
hi, i currently have windows 7 and windows vista with windows 7 being the primary operating system. How can i install ubuntu on the vista partition and have a dual boot of windows 7 and ubuntu? thanks. 
So i will be getting rid of vista

---

### Post by darkod on 2010-02-16
If win7 is primary you should be able to boot it after you delete vista. Copy any data you might need from the vista partition. Then boot 7 and delete the vista parition. Leave the space as unallocated. Boot win7 few times to make sure it's OK.
Then boot with the ubuntu cd, Install Ubuntu option, and in step 4 just tell it to Use Largest Available Free space. It will install into the unallocated space and configure grub to boot both ubuntu and 7.

---

### Post by ADZ91 on 2010-02-16
> **darkod said:**
> If win7 is primary you should be able to boot it after you delete vista. Copy any data you might need from the vista partition. Then boot 7 and delete the vista parition. Leave the space as unallocated. Boot win7 few times to make sure it's OK.
Then boot with the ubuntu cd, Install Ubuntu option, and in step 4 just tell it to Use Largest Available Free space. It will install into the unallocated space and configure grub to boot both ubuntu and 7.
 
ok thanks, i'll give that ago. i'll report back;)

EDIT: all working good, using it now, did what you said and now have win7 and ubuntu. 1 question, how do i get the boot manager to display the windows OS first? because i have to tap down on the down arrow on the keyboard 3 times to go to windows?

---

### Post by x33a on 2010-02-16
If you want windows to boot first/automatically, then you'll have to change the default os entry in grub.cfg.

take a look here to learn more about grub2 (assuming you are using ubuntu 9.10).

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

