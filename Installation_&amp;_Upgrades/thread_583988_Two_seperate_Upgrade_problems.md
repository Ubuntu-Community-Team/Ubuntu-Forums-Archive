---
title: "Two seperate Upgrade problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Bogus83 on 2007-10-20
Hi all,

I'm hoping you all might be able to help me a bit.  Last night I tried to upgrade from Feisty to Gutsy on both my laptop and my desktop, and neither worked as planned.  Here are the respective problems:

1)On my laptop, I ran the upgrade manager, made sure I was fully up to date, then hit the button to upgrade to 7.10.  It downloaded the upgrade tool, fetched all the files, downloaded everything, installed the upgrades, and prompted me to reboot.  I rebooted, and upon starting up I got the message "Failed to Initialize HAL".  Everything seems to work except for my wireless connection.  I'm using an Inet 3945ABG Wireless internal adapter, in a Dell Latitude D520.  Any ideas on how to get HAL to initialize and get my wireless working again?  I don't have wired access, so I'm kind of dead in the water.

2)My desktop situation is a bit worse.  I upgraded exactly the same way as I did with the laptop, rebooted, and get nothing but a GRUB prompt telling me I have "minimal BASH-like" interface.  I can't even boot into Ubuntu at all, and I'm not sure what to do.  I really don't want to lose all of my music and files, so I'm hoping there's some way to fix GRUB and get back in.

I'd really appreciate any advice I can get.

Thanks!

---

### Post by Temujin_12 on 2007-10-20
> 2)My desktop situation is a bit worse. I upgraded exactly the same way as I did with the laptop, rebooted, and get nothing but a GRUB prompt telling me I have "minimal BASH-like" interface. I can't even boot into Ubuntu at all, and I'm not sure what to do. I really don't want to lose all of my music and files, so I'm hoping there's some way to fix GRUB and get back in.

Can you provide more information about what exactly you're seeing when you say a "minimal BASH-like" interface?

I'm having boot problems after upgrading, but it is only with the newly installed 2.6.22 kernel.  While your computer is booting up, look for when GRUB starts and quickly press ESC.  Arrow down to an earlier kernel (if you're upgrading you should have multiple different kernels) and press enter.  For me, my 2.6.20 kernel works but the new 2.6.22 doesn't.

Additionally, when you have a kernel highlighted from the GRUB list you can press 'e' to edit it's options for this boot.  It will take you to a list of boot instructions for this kernel.  Highlight different entries here until you see one that ends in "quiet" and "splash".  Delete these two words (and only those two words), press Enter to save, then press 'b' to boot with these options.  This will turn off the boot graphic and display boot up details on the screen.  The last several lines before you are dumped to the "minimal BASH-like" interface will usually give you information about what happened.  Try posting those lines here.

---

