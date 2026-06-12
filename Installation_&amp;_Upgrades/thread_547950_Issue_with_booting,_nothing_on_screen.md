---
title: "Issue with booting, nothing on screen"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by reddeth on 2007-09-10
Ok, I posted here before, got a few answers but nothings worked so I'm going to try again in light of the recent results:

When the computer turns on, GRUB comes up normally, I hit "Ubuntu", the screen goes blank. Thats it, no errors, no messages, no screen, no nothing. I've tried hitting Alt+F1, and a ton of other combinations that let me enter into a CLI, but none ever let me get into a CLI. 

I can boot into recovery mode, so the OS works technically. my guess is that theres an error in there somewhere that keeps Gnome from loading, so can anyone give me a suggestion of what setting I most likely messed up, or where are the startup logs located so I can boot into recovery mode and see what error its reporting?

Thanks

---

### Post by merlinus on 2007-09-10
Try this, so you can see the loading messages:

Press e at grub menu, arrow down to the kernel line, press e and delete quiet and splash, press Enter, press b to boot.

---

### Post by Pumalite on 2007-09-10
Post the threads that you have ran in this forum and post your specs.

---

### Post by reddeth on 2007-09-11
Sorry, completely forgot to link the old thread: [http://ubuntuforums.org/showthread.php?t=533455](http://ubuntuforums.org/showthread.php?t=533455)

I had previously thought my issue was with GRUB (or Gnome) not being in the right resolution, and therefore I couldn't see any errors it was throwing back. I still think that is a part of my issue, after screwing around with the Xorg log files I found this:
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)

This is the only error shown in the log, everything else seems fine. I don't know that ACPI is my problem specifically, as I can boot from the LiveCD perfectly fine, as well as recovery mode (and once logged in on the CLI in recovery, I can type 'gdm' and Gnome starts up just fine, albeit a crappy resolution).

I know this isn't a ton of info, but I'm not sure what else to include, if you need any more info please let me know. At least I can now get into the system logs and such via recovery mode, just can't do much when I"m in there.

Thanks
-red

---

### Post by merlinus on 2007-09-11
You might try this.

Press e at grub menu, arrow down to the kernel line, press e and add 

noapic apic=off

to the end of the line, press Enter, press b to boot.

And did you follow my suggestion in a previous post so you might see where errors are occurring on regular startup?

---

### Post by reddeth on 2007-09-12
Ok, I turned off the quiet option and it did the same exact thing, a few words pop up (it doesn't seem to be much of anything, I'll try and copy it down, it comes and goes VERY fast) then blank screen.

I tried disabling ACPI (or is it APIC? At any rate I tried both), when I hit B my screen goes blank for a second then the computer restarts. Very odd. I'll keep playing around with it.

---

### Post by merlinus on 2007-09-12
You might post system specs, particularly your video card.

---

### Post by dgtldaydrmr on 2007-09-12
I started a new post about the same issue before i found this one...

[http://ubuntuforums.org/showthread.php?t=549213&highlight=video](http://ubuntuforums.org/showthread.php?t=549213&highlight=video)

I too am having the same issue though i couldn't boot from the live CD.
I did the alt install (text mode)
Also I would like to note that I can log in blindly with my user name and password and hear the login music but the screen remains off or blank.

I got a reply that helped me fix my problem in 30sec. check my post maybe you have the same issue.

---

