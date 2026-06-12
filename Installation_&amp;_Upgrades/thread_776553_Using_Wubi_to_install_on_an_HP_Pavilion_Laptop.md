---
title: "Using Wubi to install on an HP Pavilion Laptop"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by RogerDaryl on 2008-04-30
Hi,

Lastnight I decided that I was going to download 8.04 and install it on my laptop. This was my first install of Ubuntu (well linux really).

I want to set it up to dual boot with WinXP Media Center Ed on a HP Pavilion dv9089ea ([specs]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00789907&lc=en&cc=us&dlc=&product=3308960&rule=1252&lang=")).

I loaded up the ISO in daemon tools (I didn't have any blank cd's handy to burn the ISO to cd) and clicked on Install inside Windows. The Wubi installer ran fine, then told me it needed to reboot and that I must remove all cds and DVD's from the drives (obviously not an issue as I was running it from daemon, and I did make sure that there wasn't a cd/dvd in the drive). 

After the reboot it presented me with the standard menu to choose what I wanted to boot into. After I selected Ubuntu, it shows the splash, does a few other background things and then shows my the busybox initramfs command prompt (like the bit below I've copied from another website...version nums are different I think). 
```
Busybox v1.1.3(Devian 1:1.3-2ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)#
```

No error messages are given, nothing else seems to happen after this, I've tried the other options available from the install menu that you get by pressing <ESC> after selecting (except the one that boots it to the trial environment) and the same thing happens, with no error message.

Does anyone have any solutions/suggestions I can try? Have I missed something?

---

### Post by RogerDaryl on 2008-05-01
When running in verbose mode, this is the last line I normally get:
JFS: nTxBlock = 8192, nTxLock = 65536

Occasionally it goes one line further which is dealing with firewire. It doesn't go further than that.

---

### Post by DougS on 2008-05-01
I know this doesn't help but I'm getting this too and there will be others?

Can anyone point us to a thread which explains how to fix this please (or even what it means?)

Doug

---

### Post by jv13613 on 2008-11-12
I have the same problem to. I also get the firewire message acasonaly. the user ago knows a lot about wubi. i wonder if there is a way to get in touch with him.

---

