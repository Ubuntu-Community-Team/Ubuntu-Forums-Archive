---
title: "Mixing Grub1 and Grub2 on multiple linux distros"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-08-08
How is this supposed to work out? I noticed some distros are really good about recognizing your other linux distros and some not. They keep recognizing windows, but not other linux distros.


Also, I have run into a few problems when my operating systems were on different hard drives. I have my operating systems running from a small 250gb laptop hard drive with special mounting and am using my TB hard drive for internal storage /data. However, my last attempt at installing a linux partition on the TB hard drive with Windows and another linux partition on the laptop hard drive didnt work out so well. Updating grub via the command line didnt sort this out.

Anyone have experience with this?

Sudo su root
Apt-get update grub (or grub update) or whatever didnt work before when I tried it.

---

### Post by dino99 on 2010-08-08
you might consider grub2 (grub-pc) only as it does the job with all the distro, but have issue if it find menu.lst from grub1

---

### Post by Nick_Jinn on 2010-08-08
I dont usually install grub myself. I just do auto-install, maybe get as far as partitioning home/root/swap, and grub just appears magically.

How do I 'just use grub2'?

---

### Post by phillw on 2010-08-08
> **Nick_Jinn said:**
> ....
How do I 'just use grub2'?

If you have grub2 installed, new installs should ask for permission to install the boot loader (grub legacy or grub 2), simply say "No". Once they're installed, boot to your 'primary' system (That which holds your GRUB 2), drop to terminal and issue ```
sudo update-grub
``` that will cause grub2 to go look for operating systems, you should then see the new operating system listed at boot time.

Regards,

Phill.

---

### Post by Nick_Jinn on 2010-08-08
Awesome. Thank you for breaking that down. I was running that command in the new partition and it wasnt working out.

Now, are there any special considerations for when you are dealing with multiple hard drives? If I have Windows and Ubuntu on one, can I put Knoppix and OZOS on the other hard drive where my /data partition is?

---

