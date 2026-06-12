---
title: "Ubuntu 9.10 help"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by jethrodaniel on 2010-02-06
I have a laptop that I have had set up to dual boot Windows Vista and Ubuntu 9.10. Something happened to Ubuntu (it stopped working) and I tried to restore Vista back to control. In the process I deleted the Ubuntu partition. When I tried to restart the GRUB menu only said 
GRUB loading.
error:unknown filesystem
grub rescue>

So I tried to reinstall Ubuntu 9.10 by Live CD completely but it keeps giving me the same text above-
GRUB loading.
error:unknown filesystem
grub rescue>
  
Any help? I just want to be able to reinstall Ubuntu completely.

---

### Post by darkod on 2010-02-06
OK, hold on. Did you only TRY to reinstall 9.10, or you DID reinstall it?
It seems sometimes grub2 on the MBR of the hdd is still looking for the old install (the partition you deleted). Don't worry, you should be able to fix this easy, we just need to know what you did.
Did you completely finish the second install of ubuntu?
If you did, boot with the ubuntu cd, Try Ubuntu option, and in terminal run:
sudo fdisk -l

copy the result here for a start.

---

### Post by jethrodaniel on 2010-02-06
nah..it wouldn't let me even run the live cd, much less install it...

---

### Post by darkod on 2010-02-06
OK, so what's the current status? You can boot vista, but you can't even start installing ubuntu?
Not even letting you boot from a cd? hmmm...

---

### Post by jethrodaniel on 2010-02-06
It wont even let me run Vista ( I booted Vista with GRUB) or a live CD

---

### Post by theozzlives on 2010-02-06
Is your CD set as the first boot device?

---

### Post by jethrodaniel on 2010-02-06
Its not set to automatically boot from CD; I manually select it each time I try to boot from CD


In addition, I would like to say that I care not about any files, OS (Vista), or information. I would only want to install a clean Ubuntu 9.10

---

### Post by theozzlives on 2010-02-07
> **jethrodaniel said:**
> Its not set to automatically boot from CD; I manually select it each time I try to boot from CD


In addition, I would like to say that I care not about any files, OS (Vista), or information. I would only want to install a clean Ubuntu 9.10

Just for giggles, why not try to change the boot order in the CMOS? It sounds like it's bypassing the CD and booting from the HDD. You might also want to make sure your CD light is blinking. If all that checks out, see if it'll boot from the Vista DVD.

---

### Post by jethrodaniel on 2010-02-07
Changed it in CMOS; same result

---

### Post by m.milway on 2010-02-07
I had an unrelated problem recently with similar symptoms. I.e. I could not boot from the Live CD. It turned out that my CD had died. Try booting from a different CD.

Regards,
Michael Milway.

---

### Post by jethrodaniel on 2010-02-07
Thanks M. Milway. It worked. Thanks to everybody else as well      :D:D:D

---

