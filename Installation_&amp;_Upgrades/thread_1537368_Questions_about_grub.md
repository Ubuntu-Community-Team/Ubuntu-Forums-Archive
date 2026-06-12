---
title: "Questions about grub"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by headbuster on 2010-07-23
Hello
I installed ubuntu via wubi. When I restart a boot loader appears which I think its windows' ( it looks the same when the "Start Windows Normaly" msg appears)
I choose Ubuntu and this appears:
"Try (hd 0,0): NTFS5: No wubildr"
Then I wait 30 seconds or so and grub appears and I can choose ubuntu and it loads.
It takes like 2 minutes to boot ubuntu...
Can I make grub load at the beginning like normal.
Thanks

---

### Post by oldfred on 2010-07-23
Wubi has to boot thru the windows boot loader. If you want you can change timeouts and defaults in both windows & grub (even hide menu), but you have to boot thru both.

---

### Post by headbuster on 2010-07-24
So I can decrease the time that I wait for "Try (hd 0,0): NTFS5: No wubildr" to disappear?
How can I do that?

---

### Post by bcbc on 2010-07-24
This is another thread with the same issue [http://ubuntuforums.org/showthread.php?t=1469460](http://ubuntuforums.org/showthread.php?t=1469460) that was solved.

By the way, which version of windows do you have and what version of ubuntu?

---

### Post by headbuster on 2010-07-24
Windows 7 (original, not cracked) and the latest ubuntu. the LTS.
I will make a video (record the boot process with my camera) so you can see what I am talking about.

---

### Post by headbuster on 2010-07-24
I am all OK now. The link you provided helped.
Thank you. :popcorn:

---

### Post by bcbc on 2010-07-24
> **headbuster said:**
> Windows 7 (original, not cracked) and the latest ubuntu. the LTS.
I will make a video (record the boot process with my camera) so you can see what I am talking about.

Glad you got if fixed.

I just found a bug reported on this [https://bugs.launchpad.net/wubi/+bug/566490](https://bugs.launchpad.net/wubi/+bug/566490)

You could add a 'me too' to that - might help get it looked at sooner. It seems wubi isn't up to speed on the extra boot partition that win7 uses and the developer isn't sure how to solve it.

---

### Post by headbuster on 2010-07-24
Added a me too!

---

