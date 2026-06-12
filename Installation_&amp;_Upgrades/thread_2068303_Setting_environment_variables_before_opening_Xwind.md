---
title: "Setting environment variables before opening Xwindows"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by Leo Simon on 2012-10-08
Hi, I'm installing 12.04 on a new machine.   I've been using 8.04.   In 8.04 I accessed my windows manager (either gnome or fvwm) from the command line, using startx.    In this setup I was able to set a number of environment variables, which were utilized in my startup script.       But 12.04 boots to a GUI, which is nice, but I can't set my environment variables.     Is there a way to disable the initial GUI, so that I login the old-fashioned way, and can execute scripts from the command line, then use startx?

Thanks, Leo

---

### Post by varunendra on 2012-10-09
You can add boot-time parameters or commands in /etc/default/grub file in the "GRUB_CMDLINE_LINUX_DEFAULT=" line (keep the commands within the double quotes there, separated by spaces).

As for a whole startup script, I think you can just copy it (or its symbolic link) to the /etc/rcS.d directory to execute it at boot time. Make sure to rename it so that its name begins with a capital 'S' (read the readme file in that directory for details).

But be warned - I have never tried the rcS.d directory for custom scripts myself, so can't say if it is the correct way to do what you want. Just try to see if it works as you wish.

Let's hope someone more knowledgeable and experienced with startup scripts notices this thread and jumps in to offer his valuable advice.

---

### Post by Leo Simon on 2012-10-09
thanks very much for the suggestion.   I'll give it a try.

---

### Post by Leo Simon on 2012-10-17
I solved this to my satisfaction, based on help from various sources


 In /etc/default/grub I replaced
  GRUB_CMDLINE_LINUX_DEFAULT="text" rather than "quiet splash"
  commented out:
        GRUB_HIDDEN_TIMEOUT=0
    then run, as root:
        update-grub
    then reboot

---

