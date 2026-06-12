---
title: "Doubt about using unetbootin"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2015-01-24
I am using ubuntu 12.04 desktop to create a bootable usb drive to install lubuntu in a laptop. I am using unetbootin to create that bootable usb. My doubt is regarding unetbootin; there is an option: "Space usd to preserve files across reboots (Ubuntu only)" and default value is set to 0Mb. This value can be changed by the user. I do not understand its purpose and hence what value will be appropriate for me. Please advise. Thanks. (The laptop is of 500Gb HDD, 4Gb Ram and has DOS but I am willing to remove DOS completely and install lubuntu since I am facing trouble creating dual boot with DOS. Earlier I kept value 0Mb for the value I wrote about above but without knowing its purpose properly)

---

### Post by kerry_s on 2015-01-24
it's for running a live system from usb. 0mb everything you do is lost every time you shut down.
say you want certain things while your running live & you always want it there when you boot from the usb, you would add some place to save those things to.

most people leave it at 0mb.

---

### Post by arroy_0209 on 2015-01-24
Thanks. One more doubt: after unetbootin completes its work, it asks me to reboot. But I am trying to install lubuntu in another machine, not in the same machine where I am using unetbootin to create bootable usb drive. So I guess there is no need to do this reboot in my desktop where I already have ubuntu, rather I should detatch the pendrive from desktop and insert it to the new laptop where I want to install lubuntu and do the required steps. Is that correct?

---

### Post by PaulW2U on 2015-01-24
> **arroy_0209 said:**
> Thanks. One more doubt: after unetbootin completes its work, it asks me to reboot. But I am trying to install lubuntu in another machine, not in the same machine where I am using unetbootin to create bootable usb drive. So I guess there is no need to do this reboot in my desktop where I already have ubuntu, rather I should detatch the pendrive from desktop and insert it to the new laptop where I want to install lubuntu and do the required steps. Is that correct?

Yes. There's no need to reboot in your case.

---

### Post by sudodus on 2015-01-24
There is no need to reboot, but I think Unetbootin leaves the pendrive mounted. So you should ***unmount it (or eject it) before unplugging***. Otherwise writing from the buffers may not be complete, and if that is the case the pendrive will not work properly.

If the pendrive was automounted, you can see it in your file browser. Press the eject symbol and wait until that symbol has disappeared. Otherwise it is better to do it 'manually' in a terminal window.

---

