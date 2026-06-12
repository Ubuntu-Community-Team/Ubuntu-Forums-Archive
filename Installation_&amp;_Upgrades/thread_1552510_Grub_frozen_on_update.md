---
title: "Grub frozen on update"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Zanven on 2010-08-13
So I was installing updates as suggested and some were for the kernal (which I had problems with last kernal update so I thought this might fix that) and it went frozen on installing grub.

I thought this issue was addressed before but I searched and found nothing.

I don't know what to do at all and help would be appreciated because I can't shutdown until its resolved. screenshot attached

---

### Post by lemming465 on 2010-08-15
Try opening a terminal window and running *sudo update-grub*.  Does that work, or do you get some error messages?  (I can't quite read the error message in your screenshot, sorry.)

---

### Post by Zanven on 2010-08-17
There is no error message. It says its updating it is just frozen on that.

it says all the regular stuff before hand and is on "Running postrm hook script /usr/sbin/update-grup."

typing sudo update-grub in terminal has it ask for my password obviously and doesn't return to the  "_blank_:~$" state for input but puts the blinking green block under it forever.

Here is just the window screenshot attached so you can see better.

Thanks for paying attention to this post. I can't really shut-down until I get this resolved and its been on since my last post. I'm busy and away alot and having my computer on while I'm away scares me a little.

---

### Post by lemming465 on 2010-08-17
Actually, shutting down shouldn't be a problem.  You might not have access to your new kernel, but the old ones should still be there and should still boot fine.  You can check what will be available by looking at the grub menu (/boot/grub/menu.lst for grub1, /boot/grub/grub.cfg for grub2). 

It might be interesting to run "sudo strace update-grub" after rebooting, as that could pin down where it is getting stuck, but it will generate a LOT of output.

---

### Post by Zanven on 2010-08-20
Shutting down was okay. I had a problem before with it freazing on grub but that was updating to lucid and there was no graphical interface and a lot of problems on reboot so I had to do a clean re-install of karmic.

No problems this time but I ran that command and I copied the output to a pdf which I attached.

Should I mark this as solved since its no longer stuck where it was or wait until I get to the bottom of the problem first?

---

### Post by strider3700 on 2010-09-14
I have the exact same issue.  It's been 20 hours or so of sitting at "Running postrm hook script /usr/sbin/update-grub"

I've previously gotten stuck here and killed the process then rebooted and everything is fine until I try to do updates.  It hangs every time it tries to update the kernel.

Any suggestions?

---

