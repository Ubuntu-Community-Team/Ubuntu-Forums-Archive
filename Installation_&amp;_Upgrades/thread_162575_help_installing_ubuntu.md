---
title: "help installing ubuntu"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by fizzle on 2006-04-19
ok well i got everything installed, saw all my hardware, but then it asks to reboot and take the CD out. so I took the CD out, starts booting up ubuntu via the GRUB boot loader. I get to intializing hotplug subsystem and it hangs for a second, then goes into a command line mode, and sits there. I decided to plug in my 1GB memory stick, it does some stuff but thats all. how do I get past this? its on an alienware laptop, dual booting with XP. ](*,) ](*,)  thanks in advance. oh yea one more question, can i make XP my default OS to boot? im pretty sure i have to edit the boot menu but just want to be sure.

---

### Post by jazzmuzik on 2006-04-19
You might try 'startx' to see if you can get into gui mode. If not at least it will display some errors that will give a clue as to why.

The default OS is controlled by /boot/grub/menu.lst

'default  0' means boot the first entry in the list, but also see savedefault.

---

### Post by fizzle on 2006-04-19
ok typing startx did nothing. its just sitting at starting hotplug subsystem, then i can type in stuff but pressing enter does nothing not even an error.  also how do i get into the /boot/grub/menu.lst ? once i boot into the GUI? ill worry about that once i get into it. ok trying to go into recovery mode, i get cannot find kernel and it just sits at the command line...ugh this is frustrating. should i just try a reinstall?

---

### Post by jazzmuzik on 2006-04-19
I've been using Ubuntu for about a month, so take what I say with a grain of salt, but yeah, I'd do a reinstall. Somebody suggested first running the Live version of Ubuntu where everything runs off the CD. If your computer goes into gui mode with the Live cd you should be able to use the installable version. If not, there may be some unsupported hardware on your system.

You can edit the file that controls which OS is the default from the gui interface by first pressing Alt-F2, then enter:

gksudo gedit /boot/grub/menu.lst

From the command prompt just run the same command minus the Alt-F2 step.

---

### Post by khightower on 2006-04-20
The same thing happened to me. I ran the live CD and the computer booted fine. I also made sure that all USB devices were unplugged.

After live CD success I re-installed Ubuntu, I like to delete my partitions and start clean.

---

### Post by jazzmuzik on 2006-04-20
[QUOTE=khightower]After live CD success I re-installed Ubuntu, I like to delete my partitions and start clean.[/QUOTE]

Amen to that. I've never performed an upgrade. I always do a new install while leaving my /home directory unformatted. I have to save my mySQL databases in /var and a few other things first, but it's not too much trouble.

---

### Post by bobpur on 2006-04-20
I have similar problems on an AMD 64 computer. It is a new build and when I installed v5.10 ubuntu it went fine. On first boot, it went to the same spot (Starting hotplug subsystems) as yours and sat there. Similar results with Kubuntu v5.10. The AMD 64 v5.10 wouldn't even install. If you try to boot up in Safe Mode, It will go to a repetive series of numbers with a time out message in an endless loop. I don't know what this means, but you may. I had to go away on business and didn't get to persue this. Good Luck!

---

