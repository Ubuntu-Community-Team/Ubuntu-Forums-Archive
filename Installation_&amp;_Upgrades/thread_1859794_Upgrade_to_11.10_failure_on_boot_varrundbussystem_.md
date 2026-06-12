---
title: "Upgrade to 11.10 failure on boot /var/run/dbus/system_bus_socket"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by chiefgeek157 on 2011-10-14
I just upgraded to 11.10 from 11.04 Desktop overnight.

The main problems were that on reboot, I would get the following:

[LIST]
[*]Black screen after the Ubuntu graphical progress screen
[*]Failed to connect to socket /var/run/dbus/system_bus_soscket: Connection refused
[*]Waiting for Network... (and for another 60 seconds)
[*]On booting to the recovery menu, blank screen
[*]On figuring out to change the vga mode on the recovery boot command, and finally getting to the Recovery Menu, my USB keyboard did not work, so I could not navigate the Recovery Menu
[/LIST]

My top priority was to at least be able to log in.

Here are the steps I had to take.  Maybe they will help some of you.  The list includes every step, even some that might be obvious to experienced users.

[LIST]
[*]Hold down SHIFT on boot to enter the GRUB menu.
[*]Highlight the entry labeled "recovery".
[*]Press 'e' to edit the boot commands.
[*]Find the line starting with linux...
[*]Edit that line to change "recovery" to "single" (this boots directly to single user mode as root, rather than the no-keyboard Recovery Menu.
[*]Edit that line to change the vga parameter to match your screen's resolution (mine is 1400x900, so 867 [see Wikipedia "VESA BIOS Extensions, Linux video mode numbers]).
[*]Press F10 to boot.  This brought me (finally!) to the root prompt.
[*]cd /var/run/dbus
[*]rm pid (assuming you had the dbus error message).
[*]Reboot.
[/LIST]

After all this, I was able to log in to the graphical desktop of 11.10.

So the root cause was the leftover pid file, but getting to a prompt to be able to remove it was a CHORE.

I may still have some other clean up to do, but at least the scary can't-boot problem seems to be resolved

---

### Post by elyobelyob on 2011-10-14
Thanks for this. Got me in ... !

---

### Post by uwe lars on 2011-10-14
I've the same problem, alas it reoccurs every time:

- quite a long period until the decision by system to boot without
  full network configuration: then, the system hangs with dark screen
- then, press alt-ctrl-F2 to login into a shell, then, remove
  the pid file and call reboot (both operations as superuser).

PS: I just found the solution from [http://ubuntuforums.org/showthread.php?t=1859432](http://ubuntuforums.org/showthread.php?t=1859432) works fine.

---

### Post by chiefgeek157 on 2011-10-14
Yes, the trick with /var/run, /run, /var/lock and /run/lock seems to have permanently solved the dbus pid problem for me as well, and also the "Waiting on Network..." issue.  Thanks for posting that information.

Still so much to learn...

---

### Post by tonywcm on 2011-10-17
exactly same problem
Thanks

---

### Post by rarendes on 2011-11-18
The only "correct" thing seems to be:

rm -rf /var/run
ln -s /run /var/run

It looks like the run directory has been moved to the root fs with 11.10, so if you're upgrading there are problems because daemons mixing up both dirs and things go bad..

Symlinking the old place to the new one "should" be the best way to obtain maximum compatibility after migrating an old system.

PS: I was suffering from the same problem, dead dbus->no network. But removing the pid file only helped once, the next boot was bad again. 

(I wrote this out of memory, I did this 3-4 weeks ago)

---

### Post by jomimube on 2011-12-26
> **rarendes said:**
> The only "correct" thing seems to be:

rm -rf /var/run
ln -s /run /var/run

It looks like the run directory has been moved to the root fs with 11.10, so if you're upgrading there are problems because daemons mixing up both dirs and things go bad..

Symlinking the old place to the new one "should" be the best way to obtain maximum compatibility after migrating an old system.

PS: I was suffering from the same problem, dead dbus->no network. But removing the pid file only helped once, the next boot was bad again. 

(I wrote this out of memory, I did this 3-4 weeks ago)

Thank you.
 
Update my OCS-Inventory NG / GLPI and generated this error, your solution fixed the problem.
 
Thanks again

---

### Post by deadtom on 2012-08-08
Had the exact same problem. This solution worked for me as well.

Thanks!

---

