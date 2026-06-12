---
title: "Upgrade problem - will not boot"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by markloudon on 2010-05-20
Have had a torrid time with upgrading to 10.4 and now regret it.

The initial workaround from [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) works for me and I can get booted, but the attempt to permanently edit that into the kernel boot parameters dos not work, and restart just returns to the original problem. How can I edit the kernel boot parameters or what am I doing wrong?
I enter the commands as given. I assume the vertical line and line break mean I hit enter in the terminal then. Do I?

I am an absolute beginner, this thread is there as well.

---

### Post by oldfred on 2010-05-20
If you can boot into your system with the one time edit of the menu, then you will want to edit the /etc/default/grub.

The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

```
gksudo gedit /etc/default/grub
```
then run:
sudo update-grub
see section on editing /etc/default/grub:
# GRUB_CMDLINE_LINUX
If it exists, this line imports any entries to the end of the 'linux' command line (Grub Legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

---

### Post by markloudon on 2010-05-20
You would think this would do it, but after I add i915 modeset=1 to the line
GRUB_CMD_LINUX_DEFAULT="quiet splash"
and run update-grub I get the message i915 not found.And a restart hits the same problem at the same ppint. But when I enter i915.modeset=1 to the grub menu at the one time start up it boots fine. I am really confused.

---

### Post by davidmohammed on 2010-05-20
... you need to include the "." i.e.

GRUB_CMD_LINUX_DEFAULT="i915.modeset=1 quiet splash"

---

### Post by markloudon on 2010-05-20
You beauty. It wasn't the full stop - I tried that both ways, but I was outside the "s. That works now, and I am in 10.4. Thank you so much for your consideration and time.

Mark

---

### Post by NUboon2Age on 2010-06-29
> **davidmohammed said:**
> ... you need to include the "." i.e.

GRUB_CMD_LINUX_DEFAULT="i915.modeset=1 quiet splash"

I think this is spelled slightly incorrectly.  At least what worked for me was:
```

GRUB_CMDLINE_LINUX_DEFAULT="<options go here>"

``` ie, '..._CMDLINE_...' not '..._CMD_...'

and for me *i tried i915.modeset=0 and it worked for my Intel display adapter, but i found it wasn't necessary.*  

**In my case the real problem was that by mistake i had installed the kernel 2.6.32-23** (i had been fine with the 2.6.32-22 kernel) from the Kubuntu experimental repository and at least in my system it seemed to clash with the Plymouth boot splash option.  The result was:

[LIST]First when booting it **came straight to the Grub2 recovery interface**.  *I fixed this by booting w/ a 10.04 liveCD and **running the grub-reinstall command** to get grub to reconfigure itself*. This was just the first layer of the problem... [/LIST]
[LIST]Secondly it would **stall on the Plymouth boot splash** (note: The 'splash' option in the above kernel option whether Plymouth is used) and never reach the Gnome Display Manager (gdm) logon screen.  I could log in however by cntl+alt+F1-F6 and use a tty to work from the command line or  the gui by doing a 'sudo service gdm restart'. I was able effect a *fix by **uninstalling the 2.6.32-23 kernel*** header and image packages via Synaptic (and then *unchecking the Kubuntu experimental repository* that I'd mistakenly installed from.[/LIST]

Note: I'm sure when the 2.6.32-23 kernel has been fully vetted and Plymouth and the other parts of Lucid have been appropriately upgraded to match it, the 2.6.32-23 kernel will work just fine with Plymouth and with my system.  I just installed it before my system was ready for it.

---

