---
title: "Running in Windows - boot problem"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Doug999 on 2008-04-25
I selected the option to try out the latest Hardy Heron version using the wibu installer.

It seemed to set up correctly until the reboot. It gave the option of booting Windows Home or Ubuntu. When selecting Ubuntu, the system seemed to reboot and go back to the OS selection screen.

I changed every option that I could, installing Ubunto on my C drive, the D drive, changing the language (as I have a French version of Windows, but I run my apps in English)... nothing.

I ran chkdsk/r - no problems. I checked the ISO - no problem.

I then went into the Systems configuration within Windows to look at the boot preferences. I saw the two systems listed: Windows Home and Ubuntu. I selected Ubunto as the default to see if it would do anything.

Now I have a problem. When the system boots from the disk, I don't even get the screen where I can choose which OS to run - I just get a booting loop. I see the VAIO logo (sony), the Pentium 4 logo, and then it reboots again.

I'm running this now off the CD.

How can I fix it?

---

### Post by Doug999 on 2008-04-25
I looked at the boot.ini file on C: and saw that the timeout was set to '0' so I increased it to '15' and the OS selection menu now comes up. I can now select Windows.

Ubuntu still does not load. Any ideas of how I could find out why not?

---

