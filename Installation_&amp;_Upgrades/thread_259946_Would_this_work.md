---
title: "Would this work?"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-09-18
My iMac G3 currently has Hoary installed on it because it's never had an internet connection before. However, it soon will be  connected to the internet and I would love to install Dapper (either Ubuntu or Xubuntu. I haven't decided yet).

But, the PRAM battery is dead. With a dead PRAM, if the computer becomes unplugged, the date sets back to 1903. This means it will not install new software because, according to the machine, the software in question has not been invented yet. :roll: 

I can fix this problem by setting the date with the "hwclock" command. I've tried installing from scratch before with a dead PRAM and ran into problems and had to replace the PRAM before I could use the computer again.

**Long Story Short: Is it possible to use the "hwclock -w" command to set the date from the LiveCD and install (X)Ubuntu successfully afterwards?**

I can't afford the battery at the moment and with skool starting soon, better to have an old OS than none at all.

Thank you

---

### Post by orb9220 on 2006-09-18
Well during the install it will ask for timezone and setting the time. If  you set the time there during the install then would that fit your needs?

As long as the reboot with power still attached doesn't effect your clock then I would think it would be okay. 

And then you can always setup something to fetch the time from the  internet to set your system clock.

Hope this helped.

---

### Post by DirtDawg on 2006-09-18
> **orb9220 said:**
> Well during the install it will ask for timezone and setting the time. If  you set the time there during the install then would that fit your needs?

As long as the reboot with power still attached doesn't effect your clock then I would think it would be okay. 

And then you can always setup something to fetch the time from the  internet to set your system clock.

Hope this helped.

Yeah good points. I'm just a little paranoid because it didn't work before, but that was some time ago and I'm a little longer in the tooth now. 

I guess I just wondered if the LiveCD would allow me to use a sudo command like hwclock because it usually tries to protect new users from screwing their computers up. But I think you're right, it seems like it should work just fine.

Thanks for the input.

---

