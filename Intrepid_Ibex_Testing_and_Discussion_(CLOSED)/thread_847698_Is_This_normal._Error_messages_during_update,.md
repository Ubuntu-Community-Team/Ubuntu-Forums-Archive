---
title: "Is This normal. Error messages during update,"
date: 2008-07-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-02
Setting up apparmor (2.3+1289-0ubuntu2) ...
ls: cannot access /sys/module/apparmor: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
$Loading AppArmor module: Failed.
invoke-rc.d: initscript apparmor, action "start" failed.
ls: cannot access /sys/module/apparmor: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
$Loading AppArmor module: Failed.
invoke-rc.d: initscript apparmor, action "reload" failed.

---

### Post by Nullack on 2008-07-02
Ive already bugged it - no kernel space module as of yet

---

### Post by cariboo on 2008-07-03
I updated apparmour this morning with no error messages. I did an clean install using the  Alpha 1 cd. Are running a clean install or an update from hardy?

---

### Post by Nullack on 2008-07-03
Are you sure apparmor is loading on boot or are you actually missing the message because you have usplash on?

---

### Post by philinux on 2008-07-03
I've change startupmanager options to not splash just text. I rebooted and no errors showed up.

Checked log no errors.

Mind you apparmor is for SELinux, I guess it's just included.

(This is a clean install. Using VBox)

---

### Post by Nullack on 2008-07-03
Not its not, apparmor is a security module for the kernel that competes with selinux.

I have synched my install to the binaries in the repos and rebooted - same old app armop boot time error about no kernel module.

Can you please re-confirm, because I am certain on my end.

I have also synched directly from Ubuntu without using a mirror and Im 100% sure Im at the latest intrepid revisions.

---

### Post by Gina on 2008-07-03
I get those errors on startup too.  Doesn't seem to stop things working so I'm carrying on and ignoring it until it's fixed - not being in a position to help find the solution, I'm afraid.

---

### Post by philinux on 2008-07-03
Did a 
sudo dpkg --configure -a

Nothing reported.

Just rebooted.

cannot access /sys/module/apparmor:
Past by in a flash on the screen or something like it, only just saw it.

Nothing in logs though.

---

### Post by Nullack on 2008-07-03
OK,so apparmor isnt fixed yet

---

### Post by philinux on 2008-07-03
How come nothing in log files?

Is it because it's before the logging daemon gets started?

---

### Post by Nullack on 2008-07-03
Yes sir it is

Hint: In my menu.lst for grub I do a vga=0x31B so that I have a high res tty1-6 which is useful for tty sessions as well as being able to see all the boot messages on the one screen in tty1

---

