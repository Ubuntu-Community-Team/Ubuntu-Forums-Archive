---
title: "M3A32MVP XUbuntu 9.10 Karmic Upgrade"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by doktorOblivion on 2010-04-26
Uggggh!  After months ignoring the upgrade message from my package
upgrader on Jaunty, I finally decided and clicked upgrade.  Much to my 
surprise the kernel would NOT boot!!!!  Normally I do NOT suffer frustration 
at the hands of Linux, but today is my day.

I received an error message upon reboot essentially saying my ACPI
_PSS for powernow-k8 was not supported!  I upgraded my BIOS to no
avail.  However, I am still of the opinion there is something I 
could perhaps tweek to get his to work?  Any ideas?

I have fooled around somewhat with the BIOS ACPI settings and got 
far enough for XUbuntu to show the mouse screen during boot, but 
then it hangs...

I am now at BIOS version 1903 from ASUS and have all ACPI features enabled.

Any help appreciated.

---

### Post by gothams.protector on 2010-04-26
I did the very same thing today and hate myself.  I to suspected apci.  I added the following options to the end of the kernel entry in my menu.lst:
[INDENT]noapci nolapci acip=off

[/INDENT]It seems to be working now.  It hasn't caught on fire yet.

Good luck,

---

### Post by gothams.protector on 2010-04-26
Scratch that.  I'm booting fine and GNOME is locking up after the first five minutes or so.  I'm losing mouse and keyboard input.

---

### Post by doktorOblivion on 2010-04-27
Yes, I saw this, but at the moment don't have an additional Linux install on that machine to mount the f/s to update the menu.lst with those opts.  In the meantime my hope was to find some ACPI enable/disable combo in my BIOS, which I upgraded to 1903, that would work.  It got further but then hung up with little ubuntu mouse appearing then disappearing on the screen.  Guess I will have to try disabling it.

This stuff ought to work out-of-the-box.  :confused:

---

### Post by andrewthomas on 2010-04-27
I have the same board and am experiencing no problems, although I do have BIOS version: 2003 (12/08/2009) installed.  Disabling ACPI APIC support through BIOS settings will lead to a kernel-oops when trying to install some distributions, but they all run fine with it either enabled or disabled once installed.

---

### Post by doktorOblivion on 2010-04-27
ahhh, I was wondering about upgrading to 2003 BIOS version, but it said BETA, so I went to the most recent stable version.  I will give this a try first.  Let you know if it works.  Crossing my thumbs.

---

### Post by doktorOblivion on 2010-04-28
So, I got past the ACPI problem only to learn the upgrade installer hosed up my menu.lst and is pointing to the wrong kernel now.  Can anyone tell me what kernel ought to be used when you first upgrade to Karmic?  31-20?

---

### Post by gothams.protector on 2010-04-28
Here are the final boot options that worked for me and the kernel I got with the upgrade:

kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=xxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro quiet splash noapci nolapci acip=off nohz nohz=off nofb

---

### Post by doktorOblivion on 2010-04-30
Ok, I think I discovered the real problem after I upgraded my BIOS and got around the APCI problem.  It appears the synaptic update to Karmic hosed up my MBR, actually really bad.  Since I had windows on another partition I eventually lost that too.  I found some really cool tools though before I went into windows reinstall hell.  In any case, I am not sure Karmic works well on M3A32MVP mobos, at least from what I have seen.  The upgrade does not complain of anything but I think in the conversion (which I surmise is going on) from straight /dev to LVM devices hosed things up.  I could be wrong, but I looked at my MBRs and they didn't not look well at all.
Oh well, live and learn.
I have downloaded and installed Lucid on my machine now, that works much better.  Hope Karmic was a one off...we'll see.

---

