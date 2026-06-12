---
title: "Adding video card"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by afarzin on 2011-07-01
I had a fresh install with one ATI card (5830), then added a second, but I get errors about not being able to access the card. I tried reconfiguring X with this command

> 
dpkg-reconfigure xserver-xorg
I think running that is supposed to have follow up questions but it nothing happens and the prompt comes back.
Help?

---

### Post by pawhtiobo on 2011-07-01
Hi,

After "dpkg-reconfigure xserver-xorg" there are no questions, just reboot the machine to see the results.

Are you using crossfire?

See ya....

---

### Post by afarzin on 2011-07-01
I did reset multiple times. The second card is still not functional. The ATI driver can see that it exists but it doesn't function or communicate properly.

---

### Post by pawhtiobo on 2011-07-01
Hi,

I don't have any experience in crossfire, but maybe this can help you:

[http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=3](http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=3)

See ya...

---

### Post by afarzin on 2011-07-01
Thanks for the reply. I'm not actually trying to run crossfire. Just basic parallel operation.

---

