---
title: "Ubuntu + Windows 7"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by chrislynch8 on 2009-12-09
Hi,

I installed Ubuntu 9.10 on my Laptop and left a partition for a Windows 7 install. I then installed Windows 7 and now I can't boot into Ubuntu anymore, I think I should have installed Windows First and then install Ubuntu and it would have found the Windows Partition then i could just choose which one to boot to.

What do I do now. I boot into a live CD and I can see that the Ubuntu and Windows partitions are both there, But in the grubs menu.lst there is no mention of Windows, can i rebuild by which it would finis the Windows partition and allow me to choose which install at boot time.

Rgds
Chris

---

### Post by darkod on 2009-12-09
First of all, if you installed 9.10 you wouldn't have menu.lst. Are you sure you have it?
Otherwise, restoring grub2 to your MBR is easy, but not to create confusion we need to know whether you have grub1 or grub2. In terminal you can also run:
sudo grub-install -v

---

### Post by chrislynch8 on 2009-12-09
Hi,

I have menu.lst for sure I'm looking at it right now. I should have mentioned I upgraded from 8.10 to 9.10 instead of a direct install of 9.10. 

Right now I can both to Windows but not to Ubuntu, so what next. Do I run that command via my Live CD

Rgds
Chris

---

### Post by darkod on 2009-12-09
Then you should have grub1 and having menu.lst is normal. In the first post you said "I installed 9.10".
Steps to restore grub1 are here, scroll at Ubuntu version 9.04 or before:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by chrislynch8 on 2009-12-09
Hi,

Sorry, I forgot I upgraded it was only when you mentioned the grub1 , grub2 that I remembered it. 

So, I followed the instructions and I can now boot into my Ubuntu installation but not my Windows the choice isn't available to me.

Do I now have to add the Windows7 Installation to my menu.lst?

Rgds
Chris

---

### Post by darkod on 2009-12-09
Yes, sounds like it. You can also consider upgrading to grub2, then it will find all other OSs itself.

---

### Post by chrislynch8 on 2009-12-09
Perfect,

Thanks for your help. I think I'll upgrade the GRUB.

Rgds
Chris

---

