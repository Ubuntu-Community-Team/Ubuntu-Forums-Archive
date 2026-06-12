---
title: "proper ubuntu linux partitioning scheme.  am i doing things right ?"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by kraymore on 2007-05-23
I use ubuntu as a deskop.  i have a about 12GB for / and 4GB for swap (low on memory) and 30 on /home.  is this kosher ?  

danke

:-\"
i'm using using reiserfs for / and ext3 for /home.  any other suggestions ?

---

### Post by aysiu on 2007-05-23
Yes, it's kosher.

I'm not sure about mixing and matching Ext3 and Reiserfs, though.

---

### Post by 4nDr3s on 2007-05-23
As far as i know... maximum swap size is 2GB otherwise it wont be used...

---

### Post by Wim Sturkenboom on 2007-05-23
Reduce your swap to 2x memory size with a max of 1GB. More is overkill in my opinion, others even state that 512MB is sufficient.

---

### Post by kraymore on 2007-05-23
i tried a text based install of ubuntu feisty and when i was going the partitioning i specified 2GB, the same size as my memory in my computer due to lack of slots.  well, the installation did not proceed and as far as i know the other two partitions were created just fine but it halted i couldn't find my way out and it trashed my windows installation -- fixboot and fixmbr would not work and neither would ubuntu.   maybe i didn't make / and /home logical paritions.

---

### Post by rillip on 2007-05-23
You didn't mention that you had other partitions on the drive... remember that you're limited to four partition per drive unless logical.  Ideally you would not want your home and root on the same real partition, but it may not be avoidable.  Unless your Windows partition was overwritten, I don't see a reason you shouldn't be able to get Windows working again. After you fixed the MBR, what happens?

---

