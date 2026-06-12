---
title: "ubuntu suspends in startup"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by sodoff on 2007-03-28
Hi everyone
I have just installed the latest dist of Ubuntu on my Dell Latitude L400

I had no problems during installation, but once restarted the computer enters suspend mode just when the bootsequ finished and im supposted to enter user & pw

when i tell  the computer to start again it starts but then just ignores me and enter suspendmode again

is there anyone with a bright idea in here? OR do i have to install M$ 2000 again?

---

### Post by jrasmussen0 on 2007-03-28
Any chance you are at the regular login prompt?  You might just have a system that didn't recognize your video adapter.

Are you using the beta software feisty?

This is what the text based login screen looks like.

[INDENT]Ubuntu feisty (development branch) feisty2 tty1

feisty2 login: 
[/INDENT]

You can either login from the above login prompt, or you can use the live CD to make modifications to your system installed on your hard drive.

---

### Post by jfdarv on 2007-03-28
Boot up with acpi=off. You will be using APM instead.

---

### Post by sodoff on 2007-03-28
Thanx for the tips! i will try them tonight when i quit work

---

