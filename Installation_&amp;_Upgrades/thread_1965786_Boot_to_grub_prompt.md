---
title: "Boot to grub prompt"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by jshoor on 2012-04-26
Hello,

I had a Mythbuntu 10.04 system that was working fine and I decided to try to upgrade it. Using the update manager, I chose to upgrade to 10.10. The upgrade generally went okay but there were a few errors along the way. When it finished and I rebooted the machine, grub failed and I ended up at the grub rescue prompt.  I then went ahead and purged and reinstalled grub 2 following the instructions pusted by drs305.  Now the machine boots to a normal grub prompt, but I dont know how to get beyond that.

Does anyone have any suggestions, before I screw things up even farther?

Thanks in advance for your help!
J

---

### Post by jshoor on 2012-04-26
After some playing around, I came to the conclusion that grub is fine and there is some problem with the kernel.  Everytime that I tried the command: linux /vmlinuz I would get a file not found, even though I could see vmlinuz in the root directory.  Anyway, I eventually figured it might be a symbolic link problem and ran
tried to load the kernel file directly:  linux /vmlinuz-2.6.35-32-generic root=/dev/sda ro 

This worked and I was able to boot, but now the boot sequence gets as far as trying to mount some directories mounting /dev on /root/dev failed, mounting /sys on /root/sys failed, etc and I end up at a busybox prompt.  

Could this be related to the fact that initramfs-tools failed during the upgrade?

Man. I can't believe I had a system that was working fine and couldnt leave it alone.  This is a mess....

Thanks
-J

---

### Post by jshoor on 2012-04-26
BTW - I think that this is related to the fact that I have a separate boot partition, but Im not sure.

/vmlinuz is on (hd0,msdos2) but /vmlinuz-2.6.32-32-generic and the other kernels are on (hd0,msdos1)

---

### Post by jshoor on 2012-04-26
Happy to report that the problem is solved. Purging and reinstalling grub worked this time. I just had to make sure that i followed the instructions more closely, especially the ones related to having a separate boot partition. Now to upgrade to 11.04. Lets see if this goes any more smoothly.

---

### Post by col48 on 2012-04-26
Fully sympathise with your post #2 and feel that you might be lonely all by yourself on this thread.

Glad you got it sorted and hope you then made/are making a good backup!

---

