---
title: "I can not successfully install Ubuntu Ultimate 1.4"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by jamv on 2007-08-23
Hi there, I'm having trouble installing Ubuntu Ultimate 1.4. The LiveCD is working just fine (video, sound, Internet, etc) and when I install, I can never boot from the hard disk, it all ways gets past the loading bar. 

Script returned error:
X windows system 7.2.0
2.6.20-15 generic #2 SMP Sun 
(WW) &#8211; (EE) &#8211; (NI) not inplemented, (??) unknown (==) log file /var/log/xorg.0.log
(==) Using file: /etc/x11/xorg.com
Timidity is not yet configured. Enable alsa sequencer first by editing /etc/default/timity

Any help would be appreciated.
Thanks

---

### Post by bigdaddysky on 2007-08-23
Actually I had sorta the same thing happen to me. I could boot the live cd of Xubuntu, I could install it, and when it was done i would reboot and it would stay stuck at the boot screen...The bar wouldn't even move. So how I solved my problem was to get the Xubuntu Alternate Install CD. Worked like a charm.
The only thing is I don't know if the ultimate has an alternate install. Could be worth checking out.

---

### Post by erechm on 2007-08-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having the same problem with Ubuntu Ultimate 1.4 (Feisty).  The boot bar only makes it about 1/8 and then the computer shuts off.  I had the same problem with the LiveCD, but was able to get it to work by choosing Safe Graphics mode.  Now that it is intalled, I don't know how to get it to boot.

I have a new motherboard and graphics card.
ECS GeForce 6100SM-M
eVGA GeForce 7600 GT

I found this bug log that sounds like the same problem, but I don't know how to go about moving the file called  "/lib/modules/2.6.22-9-generic/kernel/drivers/char/hw_random/intel-rng.ko"  like they suggest.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892) 

Any help would be greatly appreciated!

---

### Post by rude_lee on 2007-08-30
yeah im having the same prob any fix damn im mad
help please

---

