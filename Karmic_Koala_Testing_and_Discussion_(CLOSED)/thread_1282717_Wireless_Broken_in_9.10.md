---
title: "Wireless Broken in 9.10"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Freedom65 on 2009-10-04
I first like to say I love ubuntu.I downloaded the 9.10 karmic and noticed that wireless is completely broken in it.It uses the same drivers that worked in9.04.I don't think it is the drivers.I have also downloaded other major distribution betas and wireless is broken in them too.I will mess around with something a little to get it too work,but this kind of stuff should work out of the box and I hope it is fixed before the final.I think these kind of roadblocks are what keeps linux from widespread adoption and would really like to see Ubuntu used as much as windows.

---

### Post by UbFreak on 2009-10-04
Ouch. The same thing happened to me with 8.10. I wish i could help, but thanks for the info, ill look out for that

---

### Post by stephana on 2009-10-04
what kind of wireless adapter do you have??, maybe anyone can fix the behaviour.

stephana

---

### Post by Freedom65 on 2009-10-04
Linksys WUSB544v4 it worked fine in 9.04 with the same driver.I think it is in the networking itself.

---

### Post by Freedom65 on 2009-10-04
I mean Linksys WUSB54Gv4.oops.

---

### Post by vgrisham on 2009-10-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34902](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34902)

Looks like the Railink chip that that card uses has had a long record of problems in Linux.

---

### Post by Freedom65 on 2009-10-04
Can anyone suggest a wireless adapter that works well with 9.10

---

### Post by FuturePilot on 2009-10-04
> **Freedom65 said:**
> Can anyone suggest a wireless adapter that works well with 9.10

Intel and Atheros based cards are usually a safe bet. My recommendation would be to see what kind of wireless cards are available and then do some research to see if they are Linux friendly. That method has yet to fail me.

---

### Post by Freedom65 on 2009-10-04
Tried the cd in my wifes laptop and wireless works right away.I will be looking for a new adapter.

---

### Post by inportb on 2009-10-04
Indeed, Intel and Atheros work quite well in general. I've heard that Prism is good too. At any rate, FuturePilot's suggestion is sound.

---

### Post by Freedom65 on 2009-10-04
Any brand names and models?This is for a desktop computer.

---

### Post by Freedom65 on 2009-10-05
Any suggestions? Does anyone have a usb wiress adapter that works? what kind is it?

---

### Post by linux6994 on 2009-10-05
I found this its worth a try?
[http://ubuntuforums.org/archive/index.php/t-923998.html](http://ubuntuforums.org/archive/index.php/t-923998.html)

---

### Post by onerbe on 2009-10-09
Hi

I had the same problem when I updated to 9.10, and the only way to get the wireless working was set the DNS servers and search domains to manual configuration.

This is not a fix, but will help you to get wireless working until the final release.

Hope it helps!

Kind Regards

---

