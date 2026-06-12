---
title: "Security upgades installed BUT........will not boot after"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by squid69 on 2010-02-05
I've just installed the latest security updates and rebooted but could not get past the Ubuntu logo on the black screen,i was then informed that the Kernal had failed and i had to run in low graphics mode.

Now i always thought the Kernal was the holy grail of Linux and it would not work if it failed !!

I then got to the recovery screen and booted up with the .17 kernal and all is fine,But my concern is that when i shut down and reboot it will go to the .19 Kernal and i'll have to go through this again ? Or will it boot to the .17 version from know on ?

---

### Post by squid69 on 2010-02-05
And the answer is: it boots to .19 so the next question is how do i make it boot into .17 all the time ??

---

### Post by amsterdamharu on 2010-02-05
Simplest way is install startup manager and edit the startup menu/boot menu.

Under system -> administration -> synaptic package manager.

---

### Post by darkod on 2010-02-05
You could remove the -19 kernel. Open Synaptic Package Manager and in the search box type either linux-image or linux-image-2.6.31-19

The first should show you all linux-image kernels. Mark just the 2.6.31-19 for complete removal and Apply. After that run sudo update-grub in terminal for the grub menu to be adjusted.

BE CAREFUL NOT TO REMOVE ALL KERNELS!!! Just linux-image-2.6.31-19 I think is the full name. Leave -17 alone.

---

### Post by ratcheer on 2010-02-05
> **squid69 said:**
> And the answer is: it boots to .19 so the next question is how do i make it boot into .17 all the time ??

There is no need to go back to 17. You just need to set grub to boot to the 19 kernel. See this thread for complete instructions. But, briefly, you will edit /etc/default/grub to specify which kernel in the list for it to boot from. It will probably be entry 0 (zero). Then, you run "sudo update-grub" to put the change into effect.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Tim

---

### Post by darkod on 2010-02-05
> **ratcheer said:**
> There is no need to go back to 17. You just need to set grub to boot to the 19 kernel. See this thread for complete instructions. But, briefly, you will edit /etc/default/grub to specify which kernel in the list for it to boot from. It will probably be entry 0 (zero). Then, you run "sudo update-grub" to put the change into effect.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Tim

The OP is trying to do the opposite. As usual after new kernel update, 19 is booting by default and is first in the list (position 0). But it's not functioning correctly and the OP wants 17 to boot by default.

---

### Post by ratcheer on 2010-02-05
Sorry. You are correct.

Tim

---

### Post by darkod on 2010-02-05
> **ratcheer said:**
> Sorry. You are correct.

Tim

Sometimes I am, sometimes I'm not. ;)

---

