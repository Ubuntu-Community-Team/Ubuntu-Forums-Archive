---
title: "Installed Ubuntu 11.10 alongside windows but dont get the option to boot windows"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by Jake123 on 2012-01-16
Hello all, let me start by saying I am not familiar with Ubuntu/Linux at all or very tech minded in general. With that said here goes.

I installed Ubuntu from cd and chose the option to install alongside windows.  Now at start up I don't get the option to boot windows, instead it goes straight to Unbuntu.  When Installing I was not asked to create a new partition.  I had 70GB of unallocated space I wanted to use for the install, but never chose that specifically.  I can access all of my files from windows through Ubuntu, I just can't boot windows.

I saw a similar post where people needed to see a boot info summary, so here it is if needed.
[http://paste.ubuntu.com/807024/](http://paste.ubuntu.com/807024/)

So my question is why do i not get the option to boot Windows at start up and can it be fixed?

---

### Post by Mark Phelps on 2012-01-17
When in Ubuntu, open a terminal and enter "sudo update-grub".  That will regenerate the default GRUB menu and add an entry for Windows.  You should see a list of the kernels and OSs that utility finds as it is running.  Then, when youn reboot, you will be presented with a new GRUB menu.

---

### Post by coffeecat on 2012-01-17
@Jake123, according to the boot script output that you pasted, your Ubuntu installation is in two logical partitions totalling approx 70GiB (75GB), so you did install into the unallocated space. Also, you *should* be already seeing a grub menu with these entries:

Ubuntu, with Linux 3.0.0-12-generic
Ubuntu, with Linux 3.0.0-12-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

(The last would take you to your Windows recovery partition, so don't choose that.)

If you are not seeing this and if Mark Phelps' update-grub command doesn't produce a visible grub menu, try holding down the shift key when you see the POST screen. If that doesn't work, try tapping the ESC key repeatedly at the POST screen. Hopefully, one of those two should reveal the grub menu. The grub menu should appear for about 10 seconds (the timeout on your grub menu is showing as ten seconds) but sometimes this fails for some reason.

---

### Post by Jake123 on 2012-01-17
I tried updating grub and using the shift/esc keys but couldn't get into the grub menu.
When I tried the shift key i got a grub loading message then went to an out of frequency message from the monitor.
I searched for this issue and found how to change the resolution for grub and got everything working now.

Thanks for the help.

This one is solved.

---

### Post by Mark Phelps on 2012-01-17
Good to hear ... so please use the Thread Tools at the top of the thread to mark this one as SOLVED.  thanks

---

### Post by coffeecat on 2012-01-17
Glad to hear you've solved it. 

By the way, thanks for posting this:

> **Jake123 said:**
> 
When I tried the shift key i got a grub loading message then went to an out of frequency message from the monitor.
I searched for this issue and found how to change the resolution for grub and got everything working now.

That's useful to know for others with a similar problem.

---

