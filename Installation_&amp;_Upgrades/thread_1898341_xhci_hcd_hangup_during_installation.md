---
title: "xhci_hcd hangup during installation"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by pipet on 2011-12-21
I'm a Ubuntu newbie & am trying a fresh install of Ubuntu 11.10.

I'm booting from a burned CD, and the install screen comes up. *Once it starts up, it looks like it's detecting all my hardware (I see my HDDs, etc), and then this comes up, and I am not sure what to do:

[INDENT]xhci_hcd 0000:08:00.0 WARN event TRB for slot 1 ep 0 with no TDs queued?[/INDENT]

I did some googling and it seems like this might be a USB 3 problem, but I am not sure how to bypass it (nor am I positive what the problem is).  

I made sure no unnecessary USB devices were plugged in (only mouse & keyboard plugged in to USB2).  I also tried disabling USB 3 in the bios.

I saw a suggestion to not use a USB mouse/keyboard & disable USB altogether in the bios, but that is not an option with my mobo (no ps2).

Pertinent Hardware:
mobo: ASUS P9X79Pro 

I can get by w/o USB 3 if needed.  I'd just like to get a stable install.  

Thanks in advance for help.  I really want to try out Ubuntu!

---

### Post by Ducky Freeman on 2012-01-01
I am going to bump this because I am having the exact same problem on the same mobo. I also tried to disable USB 3 with no luck. I ran the install disk on my laptop to verify that it works, and it does.

---

### Post by Ducky Freeman on 2012-01-01
Well, I still don't know what the issue was, but I fixed it. I chose to make a USB drive instead of a DVD. When the GRUB menu came up, I would click either try or install and my screen would just go black. I followed the instructions on [this](http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/) link and was able to get in. It's currently installing.

---

### Post by pipet on 2012-01-02
Thanks for the tip.  I've been too busy lately to revisit the issue but will try that out!

---

### Post by kedmond on 2012-07-03
I am having the same problem on the same motherboard. I have Ubuntu and Windows installed, but this problem is now preventing me from booting Linux. :-(

---

### Post by Bedlore on 2012-07-16
I'm experiencing this issue too, I find if I plug in an external combined USB2+USB3 hub I get these in syslog, xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?

If I leave it plugged in while restarting it will fail to boot.

Motherboard: ASUSTeK P8Z68-V PRO GEN3

Any clues on who to resolve or report the bug would be appreciated.

---

