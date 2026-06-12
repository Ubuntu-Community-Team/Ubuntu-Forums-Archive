---
title: "gnome panel"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by macstevejb on 2010-03-09
Just installed the latest updates and now I cant open any programs from the menu. As soon as I do the gnome-panel disappears then reappears and fails to open any selected software.

I can open open and run progs from the terminal.

After the latest updates, something gone amiss with the gnome-panel methinks?

Anyone else having similar probs?

regards,

Steve

---

### Post by SplitterCode on 2010-03-09
Yep, same issue here.  Launching from alt+f2 works but attempting to open from gnome menu just autohides the panel for a few seconds, but opens nothing.

---

### Post by yoasif on 2010-03-09
yep, seeing the same issue -- any chance you could submit a bug report?

---

### Post by Didius Falco on 2010-03-09
I'm having the same problem.

I keep icons on the panel and desktop for my most-used programs, so there are long periods of time when I never use the menu.

After the latest update, I went to open Synaptic to check something and when I click the icon, my panel disappears and stays gone.

After further testing, I've found that nothing in the menus will launch and all attempts to do so kills the panel. I also cannot use the keyboard shortcuts.

On Edit: I can restart the panel with the command  ```
gnome-panel --replace &
```and then hitting enter, which takes me back to a normal command line, but closing the terminal kills the panel yet again...

Edit #2: I filed a bug report - [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535295](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535295)

---

### Post by paradoxni on 2010-03-09
same issue here...

syslog:

kernel: [  439.555142] gnome-panel[2496]: segfault at 3a ip 00007fbd6ef0fae4 sp 00007ffffb1571a0 error 4 in libgtk-x11-2.0.so.0.1906.0[7fbd6ee77000+461000]

---

### Post by yoasif on 2010-03-09
updated report here: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326)

---

### Post by Didius Falco on 2010-03-09
> **yoasif said:**
> updated report here: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326)

yoasif,

You may want to mark that as a duplicate. The bug I originally filed was closed, with instructions on how to refile it to give them better info to fix it.

The new bug report is here: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535327](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535327)

Regards,

Didius

---

### Post by yoasif on 2010-03-09
I think I beat you on the updated report by a minute, so I think yours may be the dupe. ;)

---

### Post by Didius Falco on 2010-03-09
So you did - I'll dupe mine then!

---

### Post by b3t0n on 2010-03-09
I updated packages and I'm also getting segmentation fault error, when launching something from menu (although it doesn't occur, when  using indicators to launch f.e. Rhythmbox). Ticked "it also affects me" on launchpad.

I would like to help, so can you tell me how can I get all the reports that Didius Falco attached to a bug report?

---

### Post by VMC on 2010-03-09
I am updated and I don't have that problem. I noticed the bug report states amd64. I wonder if anyone here that has 32bit and the error.

---

### Post by b3t0n on 2010-03-09
> **VMC said:**
> I am updated and I don't have that problem. I noticed the bug report states amd64. I wonder if anyone here that has 32bit and the error.

I use 32bit version. Looks like it affects certain menu applet (I don't use the one that shows application, places and something else on a panel, so I don't know if it is affected, but in bug reports it is stated that it's bugfree).

---

### Post by cyberkilla on 2010-03-09
> **b3t0n said:**
> I use 32bit version. Looks like it affects certain menu applet (I don't use the one that shows application, places and something else on a panel, so I don't know if it is affected, but in bug reports it is stated that it's bugfree).

I run 32bit and have this problem too.

---

### Post by lonniehenry on 2010-03-09
Menu bar is not affected, but the main gnome menu is.  Update fix is in the works according to the [email]lucid-changes@lists.ubuntu.com[/email]

---

### Post by Vanishing on 2010-03-09
> **b3t0n said:**
> I use 32bit version. Looks like it affects certain menu applet (I don't use the one that shows application, places and something else on a panel, so I don't know if it is affected, but in bug reports it is stated that it's bugfree).

bugfree<<<<<<this word shouldn't appear in this forum:lolflag:

on topic:
yup..
im not using the normal menu applet, but using another menu bar applet in the panel, but samething, nothing launches.

---

### Post by SplitterCode on 2010-03-09
Everything seems back to normal now after latest upgrade (which included gnome-panel). :KS

---

### Post by Didius Falco on 2010-03-09
I'm using 32 bit. Latest update fixed all the issues.:p

---

### Post by b3t0n on 2010-03-10
> **Vanishing said:**
> bugfree<<<<<<this word shouldn't appear in this forum:lolflag:
True, true:lol:

The update fixed the issue for me.

---

### Post by macstevejb on 2010-03-10
I can confirm that the latest updates fixed this issue :-)

regards :p

---

### Post by vredley on 2010-03-10
Can anyone with a small screen (or a lot of programs installed) confirm that scrolling does not work in sub-menus? 'System > Preferences', for example.

---

### Post by cyberkilla on 2010-03-10
Menu works for me again. Sorry, I don't have enough menu items to help you;)

---

### Post by vredley on 2010-03-10
Oh well, thanks anyway. :) I'll start a new thread tomorrow if nothing has changed by then.

---

