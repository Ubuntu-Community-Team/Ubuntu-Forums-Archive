---
title: "Configure ACPI?"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by Frihet on 2005-05-29
I've just reinstalled Warty on my IBM600X (HHH had toooo many problems). Everything is working fine except that I can't figure out where to go to turn ACPI on. When I shut down, the machine stops with a "power down" message on the display.

Thanks!

---

### Post by Frihet on 2005-05-29
Found it in an earlier post.

Try adding acpi=force to your kernel line in
/boot/grub/menu.list

---

### Post by Frihet on 2005-05-29
The correct boot file is menu.lst.  I changed it and ACPI appears to work more or less correctly.  It shuts down properly but will not do a restart.

However, now I see what's wrong with HHH as well.

With ACPI running, sound is dead, and on boot Gnome stops with the proper wallpaper up and no menu bars. The KDE desktop works fine (I've learned to install both).

Any thoughts?

---

### Post by Frihet on 2005-05-30
I'm going to consider this thread dead. After much reading, it appears that this is a Debian issue that is not likely to get fixed soon. I installed Mandrake 2005LE on the machine, and all is well. I've got sound and good ACPI. This is an old computer, so I'll not waste anymore time on it. I just have to look at starry-eyed penguins on it until it dies ;-) 

My newer boxes are fine on Kubuntu.

---

### Post by wallijonn on 2005-05-31
[QUOTE=Frihet]With ACPI running, sound is dead, and on boot Gnome stops with the proper wallpaper up and no menu bars. The KDE desktop works fine (I've learned to install both).[/QUOTE]

Since you installed without ACPI enabled, the kernel was built with only so many modules and assigned the IRQs automatically. The [COLOR=Blue]/var/log/kern.log[/COLOR] should be able to display an IRQ map (you'll have to write them down by hand). Now that you have turned it on, the ACPI controller is probably sharing an IRQ with the sound card (usually IRQ5) and is causing a conflict. 

Did you set your IRQs manually? If so, then the devices should already be mapped in the BIOS. What does the map look like?

If you didn't go through hell installing it on your laptop, and if this is a relative fresh install (less than 1 week), then it may be easier to re-install. If however it is an older install, you'll have to compare all the logs in[COLOR=Blue] /var[/COLOR] to all the old logs to find the obvious differences. 

What are your ACPI settings? Do you have a resume feature enabled? If so you will most probably want to turn it off. Then see if the reboot function works. 

What are your BIOS settings? Usually for Windows machines I turn off BIOS shadowing &caching, vga shadowing & caching, do not turn on the 1MB IO hole. etc.

I'm old school, so I assign IRQs before installing any OS. It's ignored in WXP but not in Linux (I believe).


Is there an ACPI module? In [COLOR=Blue]/etc/modutils[/COLOR] you may find apm, it has the following code: ```
alias char-major-10-134	apm
alias /[COLOR=Red]dev[/COLOR]/apm_bios		/dev/misc/apm_bios
alias /dev/misc/apm_bios	[COLOR=Red]apm[/COLOR]

```

Now, that really may not help you as it is configured for my machine. I'm just wondering if you have one just like it. 

Likewise, you may have a file called [COLOR=Blue]/etc/modprobe.d/toshiba_acpi/modprobe[/COLOR]. It's code looks like this: ```
options toshiba_acpi hotkeys_over_acpi=1
``` Is it an IBM? 

If those files are missing, then you are going to have to run the modprobe command to map ACPI, then add it to the master modprobe list [COLOR=Blue]/etc/modules[/COLOR], or recomplie the kernel (I hope that you don't have to go that far.), or re-install.

---

