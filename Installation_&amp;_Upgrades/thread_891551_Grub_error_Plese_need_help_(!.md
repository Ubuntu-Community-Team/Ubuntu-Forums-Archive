---
title: "Grub error? Plese need help :(!"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by VengeZ on 2008-08-16
Ok heres my story, from Windows Vista, I created my linux partitions, etc..

So i put in the Live CD and INSTALL Ubuntu on the partition, everything is working FINE! grub is working fine.. so i decide ubuntu is not the thing for me, so.. I delete the partition using Windows Vista, and when i try to boot up it says "Grub error 22"..

Honestly, I'm a newb, and if I call up The tech, he'll say it's voided my warranty and Ubuntu will cost me sevierly.. :(

But hopefully you guys will help me out and get rid of this, and hopefully GRUB, so i can happily boot to vista like I always did before ubuntu.

Thanks so much to the people who help, ill do my ever best to repay you :).
.. Cheers !:)

---

### Post by VengeZ on 2008-08-16
NOTE: I do not want Ubuntu back, but simply what my computer was like, (Just VISTA and NO GRUB).

Ps. I posted this on the LIVE CD, just too clear up if theres any confussions :P.

---

### Post by Sef on 2008-08-16
Check out [Recovering the Vista Bootloader from the DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD").

---

### Post by VengeZ on 2008-08-16
So pop in my Vista recovery CD, then do those instructions, and it should work? I'm scared my VIsta partition is already deleted? or would it be? lol.

---

### Post by kflorek on 2008-08-16
> **VengeZ said:**
> So pop in my Vista recovery CD, then do those instructions, and it should work? I'm scared my VIsta partition is already deleted? or would it be? lol.

 In case you are wondering, grub needs files from the linux partition which was deleted to work completely. Your Windows partition is intact. The Vista bootloader was replaced by grub. It is a tiny program outside of Windows itself and takes about a second to put back.

 As for Microsoft being mad or vindictive. No. They will be thrilled you dumped Ubuntu!

---

