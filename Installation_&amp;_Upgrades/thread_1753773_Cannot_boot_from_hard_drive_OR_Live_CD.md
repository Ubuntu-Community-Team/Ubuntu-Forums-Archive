---
title: "Cannot boot from hard drive OR Live CD"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by TomasFitz on 2011-05-09
I have just finished building a new computer and it booted with no problems from the hard drive to ubuntu 10.10 (it was a hard drive from a previous computer and had ubuntu installed). After less than a minute though it froze up completely. I restarted and now cannot get ubuntu to boot. I get to GRUB with no problems but when I try to boot ubuntu I get a black screen with a blinking cursor in the top left corner and it hangs indefinitely. 

I tried to boot from a live cd to see if there was anything I could do but I get as far as the screen to choose "Try Ubuntu" or "Install" and both choices leave me on a black screen with the mouse icon. I can move the mouse but nothing else. I have tried the Ubuntu 10.10 32 bit, 11.04 64-bit, 11.04 32-bit and even Mythbuntu, which I had on a cd from a magazine. I get the same result with all of these. 

On the other hand, OpenSUSE 11.4 boots from the Live CD fine and I installed it and it boots from the hard drive. This is good news but I would much prefer Ubuntu, as I'm more used to it. Am I doing something wrong or have I any hope?

The computer specs are:
Processor: AMD phenom II X2 555
Motherboard: Asus M4A88TD V-EVO
Memory: G-Skill Ripjaws 4GB Dual channel
Hard Drive: Seagate Barracuda 200GB

Thanks in advance for any assistance:)

---

### Post by ACGilbert on 2011-05-09
Been there done that very recently -- almost gave up on Ubu even though I've been using it since Dapper.
I have the same MoBo with an AMD 4 core processor.
To boot from the live CD hit F6 and choose NoModeset and noapic.
When the install is finished and you reboot the first time press 'e' and insert noapic after the line with ro quiet splash. Assuming that works edit /etc/default/grub to make the change permanent.
Once in a while the boot process may stall, but this is the best I've come up with.
If I disable acpi, then only one processor works.
Hope this helps -- I'm a long time user, but certainly no expert.

AC

---

### Post by TomasFitz on 2011-05-09
Thanks so much, that worked fantastically! Up and running with 11.04 now for the first time! Incidentally, I didn't need to press e when rebooting, it rebooted fine without ( I know this as I was too slow to press e when it rebooted and I was waiting for it to crash)

Thanks a heap for the help!

---

### Post by mörgæs on 2011-05-09
Good, please mark the thread 'solved'.

---

