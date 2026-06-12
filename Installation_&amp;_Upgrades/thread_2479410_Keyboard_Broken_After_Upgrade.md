---
title: "Keyboard Broken After Upgrade"
date: 2022-09-23
forum: Installation &amp; Upgrades
---

### Post by ts1971 on 2022-09-23
Hi,

I am running 22.04.1 LTS and earlier today I installed whatever updates were queued up. After the required restart, I find that my keyboard is severely compromised in at least Emacs / Chrome / Firefox.  It seems to be okay in a terminal window.  Anyway, the main problem is that the backspace key isn't working.  So when I make a typo (I make a lot of typos), I can't delete it.  Sometimes the key presses will take effect if I wait long enough (30+ seconds); others they don't ever seem to register.  Sometimes I find that if a type a few additional random characters, the backspace key will start working again, though that trick only works ~40% of the time.  That's the most reliable symptom, but there are other key presses that don't register reliably either.  The 't' key especially seems to be hit or miss.  At this point my system is unusable (I am making this post from a windows box).  Anyone know what broke or how to troubleshoot it?

Thanks!

-ts1971

---

### Post by &amp;KyT$0P# on 2022-09-23
> **ts1971 said:**
> earlier today I installed whatever updates were queued up. After the required restart, I find th

Does the problem persist if you boot from the previous kernel version at the GRUB menu?

---

### Post by ts1971 on 2022-09-24
> **halogen2 said:**
> Does the problem persist if you boot from the previous kernel version at the GRUB menu?

Yes, it does.  I am currently running 5.15.0-48-generic and falling back to 5.15.0-47-generic doesn't seem to help at all.  At this point, I'm almost sure that the issue affects only the 't' and backspace keys.  All of the other keys seem to work okay.  I also think that if I wait long enough (sometimes several minutes) after a key press it will eventually register.  I'm really stuck here.  This is my daily environment and it essentially useless at this point.  It does occur to me that at least I don't have a 't' in my login password.  If I did I would be completely dead in the water.  

Any idea how to troubleshoot this?

---

### Post by ts1971 on 2022-09-24
Two more data points: (1) it appears that the 'y' key is also not working.  So it is 't', 'y', and backspace.  Also, I had failed to mention that the machine is a Lenovo Think Pad P70.  When I plug an external USB keyboard in that seems to work fine.

---

### Post by Impavidus on 2022-09-25
Try xev. It's a small tool you can start from the terminal. It will open a window and every keyboard or mouse event registered in that window will be reported in the terminal. Does it report presses of your problematic keys?

---

