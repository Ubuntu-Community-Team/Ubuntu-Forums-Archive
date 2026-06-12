---
title: "How do I not get a Grub menu on the install media flash drive?"
date: 2021-06-17
forum: Installation &amp; Upgrades
---

### Post by halfbeing on 2021-06-17
I installed Ubuntu alongside Windows on an SSD. However I got something wrong (must have mistyped my password during the install process) and so I need to boot back into the installer flash drive to fix it. However the flash drive now has a GRUB menu on it that sends me back to the SSD and doesn't have booting into the flash drive as an option. How can I prevent the installer adding the GRUB menu to the install media?

---

### Post by MAFoElffen on 2021-06-17
At boot, just at the end of the BIOS Post, hold down the Left-Shift key.

If that doesn't work, reboot and as it is booting, just just start hitting that Left-Shift key repeatedly.

*** Edit: I misunderstood you.

---

### Post by tea for one on 2021-06-18
> **halfbeing said:**
> I installed Ubuntu alongside Windows on an SSD. However I got something wrong (must have mistyped my password during the install process) and so I need to boot back into the installer flash drive to fix it. However the flash drive now has a GRUB menu on it that sends me back to the SSD and doesn't have booting into the flash drive as an option. How can I prevent the installer adding the GRUB menu to the install media?

The installer does not add the Grub menu to the install media because the install media already contains Grub.
Neither does Grub on the install media change during the installation process.

Do you not have a dedicated key on your PC that takes you to Boot Options (e.g. F10 or Esc) so that you can choose your USB drive?

---

### Post by grahammechanical on 2021-06-18
It seems to me that your problem actually is that you mistyped the password during installation and now cannot login because you do not know the spelling of the mistyped password. I find this strange because we have to put in the password twice and the installer checks that we are spelling it the same. So, you mistyped the password twice? Strange indeed.

I was going to post a link to a how to on changing a password that has been forgotten. I have now decided not to do that.

---

### Post by ajgreeny on 2021-06-18
I may be a bit confused already but at the risk of my misunderstanding of your post, are you saying that you do not get a grub menu when you boot the computer from which you can choose either Ubuntu or Windows?

If you see grub you should be able to boot to Recovery mode of Ubuntu by choosing the Advanced options in grub, and from there you can restore a forgotten or unknown password easily by following the instructions at [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)
I have never needed nor used this so personally I can  not claim any experience of its success or failure.

Apologies if I missed the point of your post and got the wrong problem.

---

