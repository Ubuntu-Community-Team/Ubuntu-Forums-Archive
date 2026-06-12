---
title: "Splash screen."
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chrispche on 2010-04-24
I don't seem to be able to get any kind of splash screen at start up. Now I have installed start up manager, that doesn't seem to have made a difference. I have one of those annoying nomodeset cards. Is this anything to do with it?

Cheers.

---

### Post by gastly on 2010-04-24
Have you checked if grub is passing the 'splash' option to the kernel on boot?
You can check this in the file **/etc/default/grub**
It should contain something like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

---

### Post by chrispche on 2010-04-24
Here is my grub file.

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset"
GRUB_CMDLINE_LINUX=" vga=792"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by chrispche on 2010-04-24
On this line:

GRUB_CMDLINE_LINUX=" vga=792"

What's the code to specify what res you want? I remember this is something you changed in Fedora when you wanted to change the res of the splash screen.

---

### Post by chrispche on 2010-04-24
I have solved this problem with [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2157775.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2157775.html) so just letting others know.

---

### Post by garvinrick4 on 2010-04-24
I am under the impression that at times I do not get a plymouth splash because graphic drivers do not load in time and the file system is already mounted so we just go to X.
We screamed for speed and it seems as if some graphic drivers are not up to the task.
Mine is Intel and I get there some times and other times I do not. Have 2 lucids installed
and fresh at Beta2 and they both do the same exact thing. One will go on to maverick and the the other will be my LTS and I have all the confidence that any plymouth issues will be ironed out. Will most likely boot before you can put your glasses on and blow the cookie
crumbs out of your keyboard.

---

