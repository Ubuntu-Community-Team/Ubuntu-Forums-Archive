---
title: "Burg boot loader blank screen"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by Matt D on 2012-06-15
I installed burg and it was all working fine. I wanted to remove some of the boot options so installed the super boot manager. This all worked fine. However after a few reboots of my system istead of seeing the burg boot loader there was just a blank screen that would then boot into Ubuntu after about 10 seconds the Ubuntu splash screen was also missing. I uninstalled burg and set grub back up. I then removed anything to do with burg and super boot manager from using the synaptic package manager. 

I tried to then reinstall burg but I am still getting a blank screen. Does anyone know what is causing this to happen and how to solve it.

I am using ubuntu 12.04

---

### Post by drs305 on 2012-06-15
What do you want to happen? 

The blank screen for 10 seconds could be the result of the GRUB equivalent of GRUB_HIDDEN_TIMEOUT= of /etc/default/grub. It could also be that the 10 seconds is an automatic boot and BURG is transferring control almost immediately and the 10 seconds is being used by the system once it gains control of the boot.

If you hold down the SHIFT key during boot does the BURG screen appear?

You could also try removing "quiet splash" from the BURG settings so that you can see the system messages during boot. This would at least let you know if it's pausing at the BURG menu or during boot.

---

### Post by Matt D on 2012-06-15
Holding down shift doesn't seem to be doing anything.
After I removed the quiet splash it looks like it is just booting right into linux.

---

### Post by drs305 on 2012-06-15
I don't know enough about BURG to know if the boot info script works on BURG or not. 
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
It might be helpful to see the contents of RESULTS.txt

For now, once you boot you could edit your burg.cfg file and change all "timeout=" values to -1
That should force the menu to display until you make a selection. Of course, if you run update-burg it's going to wipe out those changes.

I don't think BURG is supported by it's creator any longer. If you don't have a specific need for BURG you might consider reverting back to GRUB - more of us are familiar with GRUB troubleshooting.

---

### Post by Matt D on 2012-06-15
I will probably just switch back to grub. The only reason I was using burg is because it looks cool.

Thanks for your help.

---

### Post by drs305 on 2012-06-15
Although detailed themes are still not advanced in GRUB, adding backgrounds are really easy these days. GRUB 2.0 (the real 2.0 coming soon) is supposed to advance theming compared to the current version (1.99).

The GRUB2 link in my signature line can take you to the Grub display community documentation.

---

