---
title: "Fix black screen in tty 1 to 6?"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2017-03-09
When I access linux via command line mode using <Ctrl><Alt><F1> to <F6>, I am get a black screen that obstructs me from accessing command line.
Meaning I can't see any text on the screen, eg. can't see login line..
I am using NVidia graphic driver installed using [COLOR=#333333][FONT=DINWebPro]NVIDIA-Linux-x86_64-375.39.run[/FONT][/COLOR] on Ubuntu 16.04 with kernel [COLOR=#000000]4.4.0-64-generic.[/COLOR] 

Any solution to fix this?

This issue happened after recovering from a purple screen that had resulted from repository updating my kernel to [COLOR=#000000]4.4.0-66-generic. 
Details of recovery procedures can be found in [h]("https://ubuntuforums.org/showthread.php?t=2354955")[/COLOR][ere]("https://ubuntuforums.org/showthread.php?t=2354955").

---

### Post by sunbear-c22 on 2017-03-10
A clarification on the description of my tty screens. 
It is mostly black but it also has a horizontal purple strip (less than 1cm thickness) appearing at the top of the screen.  

Managed to find a similar incident reported dated [2012 by SeanO]("http://askubuntu.com/questions/162535/why-does-switching-to-the-tty-give-me-a-blank-screen#"). 
I have tried using the command below but it did not work.
> # Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
There is one notable difference, the color of the tty screens are completely black in colour. Horizontal purple strip is gone. 

In addition, I have tried using nomodeset  as shown below but it did not work either. 
I had used *sudo update-grub* each time I amended  the grub file "*/etc/default/grub*" and rebooted my system for each try. Nothing worked so far.
> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT_STYLE=menu
#Possible options are [menu|countdown|hidden]
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

A good explanation on the meaning of nomodeset and how to use it is mentioned [here]("https://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997") by P4man. 

Does these findings rule out my issue to be unrelated to grub2 but with X-window?

---

### Post by ubfan1 on 2017-03-11
Not X windows, but systemd.  Not sure what's happening, but the ctrl-alt-fn sequence shouild start a process (agetty) on that ttyn.  If that's not happening,
try starting one yourself from the X windows gnome terminal:
$ /sbin/agetty --noclear tty6 linux &
and quickly trying the ctrl-alt-F6 to switch to a real tty.  If you don't do it fast enough, the virtual term will let the process die.

---

### Post by sunbear-c22 on 2017-03-11
After much testing, I am quite certain the horizontal purple strip in the tty1 to 6 is actually the splash that is configured in grub2.
Reason for this conclusion: When I changed the splash with  GRUB_BACKGROUND=".....", the color of the horizontal strip changed to the color of the splash.
Meaning,  when I press for example <Ctrl><Alt><F1>, the screen does switch to tty1. However, it is obstructed by a misaligned/out-of-place black screen. 

So I would like to know which program/package is responsible for creating the black screen? 
Is is Xorg, Xserver, Nvidia or grub2? 
I think it is quite unlikely to be grub2. 
I am leaning more towards the other 3 candidates. Anyone knows?

---

### Post by bbuckb on 2017-04-18
I am having similar issues, can't get ctrl-alt-F1-6 to work at all. I've installed several versions and have been scouring the internet looking for an answer.

This is a T450 with Intel 5500 card and nothing has worked to give me a console, but when I hit ctrl-alt-f1 nothing happens. 

I've also tried adding the nomodeset to grub and restarting, this results in a black screen with a mouse cursor, nothing else.

---

### Post by bbuckb on 2017-04-18
well never ceases to amaze me sfter 20 years in IT the simplest thing...

CTRL+ALT+FN+F1 

I guess with at least the Lenovo I have this is how you switch to tty console. Hope it saves someone else some time.

---

### Post by ubfan1 on 2017-04-18
Check your BIOS/UEFI settings for something to change what Fn does.  It's not necessary on my Lenovo W520 to switch to a tty.

---

