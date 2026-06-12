---
title: "My swap partition disappeared"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by Hex_Mandos on 2007-07-31
I noticed my computer was giving me bad performance today, so I checked the system monitor. Upon opening it, I realized I wasn't swapping, and my available swap space showed as being 0 bytes. I did create a swap partition when I installed Ubuntu, but i'm thinking that installing other OSes in other partitions might have made Ubuntu to stop recognizing it (I'm 100% sure I didn't delete my swap).

How do I make Ubuntu use my swap partition again?

---

### Post by kidders on 2007-08-01
Hi there,

I would recommend the following:[LIST=1]
[*]Identify your swap partition(s), and make sure no other OS is configured to use them. Sharing the same swap space between multiple operating systems is a bad idea.
[*]Alter your /etc/fstab to refer to your swap by /dev path, rather than UUID. This will cause it to break again if the /dev node names of your disk partitions change for some reason, but will make your swap immune to a range of other common gotchas.
[*]Reformat your swap space.
[*]Execute one (or more) "swapon" commands to activate your virtual memory, or reboot your system.[/LIST]That *should* sort you out. Your swap may have been reformatted (thus changing its UUID), damaged, or perhaps used to store a "hibernate" image, by another OS at some point.

**Edit:** If you *had* deleted your swap partition, it'd still be no major issue. You can add swap (ie "swapon") to a Linux system at will, without having to do anything special. Caution is advised when *removing* (ie "swapoff") it though ... your OS must have enough spare memory to be able to free it.

---

