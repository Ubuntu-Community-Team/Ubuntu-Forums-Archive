---
title: "Blank screen on booting Marveric install disk"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by RayG on 2010-10-12
On attempting to install Ubuntu on the computer spec'd below, the computer access the Maverick install CD but displays only a blank screen. If I hit F1 immediately after rebooting, the Language and Keyboard dialogs display, after which the expected boot menu is shown. I choose "Try Ubuntu" and hit ENTER. The CD is accessed for a while, the monitor initialized as if X is starting, a few minutes later a blank gray screen is displayed. (Note: This is not the default X screen. There is not "weave pattern" seen before GDM displays. It's just blank and gray.) End of disk activity.

Observations:
I cannot access TTY's. CTRL-ALT-FunctionKey yields a blank screen. CTRL-ALT-F7 takes me back to the gray screen.
CTRL-ALT-BACKSPACE on the gray screen does nothing.
Disabling ACPI does changes nothing.
Adding VGA=771 to boot options changes nothing.
Increasing shared video memory changes nothing.
Choosing "Test Install Disk" results in same behavior.
CTRL-ALT-DEL reboots the computer. It is taking keyboard input.
Ubuntu 08.04 install CD boots normally.

Motherboard= AsRock K10N78
Chipset=NVIVIA-8100
Processor=AMD Phenom II, 550BE
Video=onboard video w/256MB shared memory
CD=Memorex USB DVD-RW

---

### Post by dfolk on 2010-10-12
I am having the same problem. Do not have a solution yet, but the following link is giving me a starting point for solving

[http://ubuntuforums.org/showthread.php?t=1592763&highlight=blank+screen+install](http://ubuntuforums.org/showthread.php?t=1592763&highlight=blank+screen+install)

---

### Post by RayG on 2010-10-12
Thanks Dfolk. I will give the nomodeset param a try this evening and see what happens.

---

