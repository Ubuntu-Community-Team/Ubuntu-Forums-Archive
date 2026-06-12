---
title: "How do I replace a missing kernal after an interrupted upgrade?"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by VeryFoggy on 2011-12-14
(This may belong under absolute beginner talk)

I am running 11.10. I am new and something seems to go wrong every time I update stuff, so I have been putting it off. I finally hit the update manager and let it update everything. Computer freezes in the middle of this process and is restarted without incident. After the update manager is finished, computer is restarted and comes up grub. This has happened before and the code I have used to fix it before is thus:[INDENT]grub> set root=(hd0,1)
grub> linux /vmlinuz root =/dev/sda1 ro
grub> initrd /initrd.img
grub> boot

[/INDENT]It took the first line just fine, but gave me this error after the 2nd line[INDENT]grub> linux /vmlinuz root =/dev/sda1 ro
error: cannot read the Linux header.
[/INDENT]I believe the disruption while downloading resulted in a corrupt file and thus a missing or corrupted kernal. 

I am running ubuntu off of a USB drive. I can access the hard drive. 

How do I identify the missing kernal, and replace it, so that I can run my computer like normal again?

---

