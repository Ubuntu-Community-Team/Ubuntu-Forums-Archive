---
title: "Remove Ubuntu Partition without harming Window's Partition."
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by Enlightened Shadow on 2010-04-18
Hi, I currently have both Ubuntu 9.10 and Windows XP installed on my PC. I want to remove the Ubuntu partition and leave the Windows partition. The question that I have is that when I remove it, Grub will go with it. Will that mess up my Windows partition?

What I need to do is remove Ubuntu and add the hdd space back to the other partition. I just don't want Grub's absence to keep me from being able to load Windows. I would love to keep Grub if possible.

---

### Post by cybrsaylr on 2010-04-18
I recently did this. You can delete the Ubuntu partition without effecting the Windows partition but GRUB will remain. 

I just upgraded a friends PC from Vista to Win7. The W7 install knocked out GRUB so I couldn't get back into Ubuntu. So I ended up deleting the Ubuntu partition and reinstalling Ubuntu there again to get GRUB back so he could dual boot again and all is fine again.

---

### Post by Enlightened Shadow on 2010-04-18
OK thanks, I was just worried that deleting the Ubuntu partition (which Grub is installed on) would also delete Grub. If it doesn't then that is just fine. I just don't want to use GParted to delete the partition and add that space back to the Window's partition, only to find out that I can't boot Window's up. This is my only PC at the moment so it is critical that I am able to do this smoothly.

Thanks for the reply.

---

### Post by Enlightened Shadow on 2010-04-18
> **cybrsaylr said:**
> 
I just upgraded a friends PC from Vista to Win7. The W7 install knocked out GRUB so I couldn't get back into Ubuntu. So I ended up deleting the Ubuntu partition and reinstalling Ubuntu there again to get GRUB back so he could dual boot again and all is fine again.

Also I wanted to mention that it was not necessary to delete the Ubuntu partition in your case. There are articles on how to restore Grub on the internet. Just Google "Restore Grub after Window's installation".

---

### Post by garvinrick4 on 2010-04-19
If you lose the grub no big deal if you have a Windows recovery disk or installation disk!!
Can also use Ubuntu Live CD to reinstall Windows boot but a lot more lines of code to get right. With Windows CD 2 little lines and done.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Enlightened Shadow on 2010-04-19
Thanks for all of the advice guys. I will simply try to remove the partition and see what happens.

---

