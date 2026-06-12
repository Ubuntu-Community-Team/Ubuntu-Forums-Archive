---
title: "Upgrading and EnvyNG - a reminder!"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by zami on 2008-11-09
My upgrade to 8.10 went smoothly, it seemed, until it came time to reboot.

I rebooted, and could get no further than my monitor saying "resolution out of range".  No log in, no desktop, no nothing past the GRUB menu.

After wrestling with a bunch of fixes I'd read here in the threads involving similar problems, I remembered I'd used EnvyNG to install proprietary ATI drivers a few months ago - and that I've read from day one to disable Envy before upgrades.

Anyhow, I forgot, so I thought others may have done the same and be stuck with the dreaded monitor message, or a black screen.  Here is how I fixed my problem - 

+Restart your machine, and chose Recovery Mode from the GRUB menu
+Choose "root" (Drop to root shell prompt)
+at the prompt, run "sudo envyng -t" (minus the quotations)
+follow the prompts to remove your ATI or NVIDA drivers
+reboot

Hopefully, you'll get back to your desktop.  You might have a horrible resolution but it should be workable and you can troubleshoot from there (without jotting notes from one computer to try fixes on the other!)

For me, the restricted drivers Ubuntu offers to install work fine, though I had a hiccup while rebooting and had to reboot twice.  Now I've got a lovely resolution again.  (I'll probably still have problems with my ATI driver but that's nothing new.)

Good luck!
-zami

---

