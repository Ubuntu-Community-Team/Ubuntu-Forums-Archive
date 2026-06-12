---
title: "Can't boot 10.04 - Grub rescue problem"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by tikbjamin on 2010-03-08
I have 10.04 alpha 3 running well on my laptop so I decided to upgrade 9.10 to 10.04 on my Dell Dimension 4550 desktop.

The problem is that when prompted I tried to install grub on the boot partition of disk 1 instead of just disk 1.  Now I can't boot into ubuntu.  I get an error message 'grub_puts_' not found and a grub rescue prompt.  Don't know much about this so I just disconnected disk 2 which contains Windows.  I cannot boot Live CD either.

Would appreciate your help in getting my desktop running again.

---

### Post by tikbjamin on 2010-03-09
Can I give you some more information to help me out?

So, I followed this [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) but I am getting a file not found error at step 6.

What do I need to do?

---

### Post by kansasnoob on 2010-03-09
What happens when you try to boot the Live CD?

Ultimately we need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But you'll need to get booted to the Live Desktop first. Maybe this will give you some ideas:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by tikbjamin on 2010-03-09
I get the same message as above when I try to boot the Live CD.  Is there nothing else I can do?  Would it make sense to attach this drive to my laptop or other bootable device?

---

### Post by kansasnoob on 2010-03-10
I just don't know, so consider this a bump.

---

### Post by tikbjamin on 2010-03-12
SOLVED

Thanks for trying, man.  I had a defective CD drive.  I was able to switch it out, boot from the Live CD and reinstall 10.04 which boots fine.

Amazingly, I can now get 1024 x 768 screen resolution which I had lost for quite some time since 8.xx.  

If only I could now get sound.

---

