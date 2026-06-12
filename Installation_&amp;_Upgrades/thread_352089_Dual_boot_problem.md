---
title: "Dual boot problem"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by mikef on 2007-02-02
I installed a dual boot system on a single 300 gig hdd, and everything seemed to install correctly. When I boot up, Grub comes up, but it doesn't recognize my wireless keyboard, even though it works in both Ubuntu and Windows without any problems. Any ideas on this? Thanks in advance.

---

### Post by neverett on 2007-02-02
> **mikef said:**
> I installed a dual boot system on a single 300 gig hdd, and everything seemed to install correctly. When I boot up, Grub comes up, but it doesn't recognize my wireless keyboard, even though it works in both Ubuntu and Windows without any problems. Any ideas on this? Thanks in advance.

Do you have the base plugged into a usb slot?  It's a long shot, but if you have an adapter from usb to the ps/2, try using that and plugging it in the ps/2 slot.  Just a thought.

---

### Post by mikewhatever on 2007-02-02
Sounds like bluetooth driver (assuming it is bluetooth) is loaded after the choice in grub is made. How do you select which OS to boot then?

---

### Post by mikef on 2007-02-02
I can't, that's the problem. It automatically goes into Ubuntu because it's the primary.

---

### Post by mikewhatever on 2007-02-02
Having done a google search ```
wireless keyboard ubuntu
``` I found [ something that might help ](http://ubuntuforums.org/showthread.php?t=276)

I hope mods will edit the topic of your post, because it is rather vague.

---

