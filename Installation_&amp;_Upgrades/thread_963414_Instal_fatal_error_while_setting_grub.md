---
title: "Instal: fatal error while setting grub"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by smauleon on 2008-10-30
Hi,

I'm installing Ubuntu 8.04 in 20 Windows PCs in my school, in dual-boot mode. I use the livecd for that.

It worked in about half the cases. The rest give me a fatal error near the end, while installing grub. What puzzles me is that I can't find a pattern.

Some are W2000, others XP. There are three different HW configurations, but in all cases I succeeded with some units and failed with the rest. In 2 of the HP all went OK, and the other 3 give me the error. In some of them I tried several times and the error repeats (well, that's a pattern, I guess :-) )

I tried to install Vector Linux light in one of the rebels and it worked. But i prefer Ubuntu :-)

All PCs have the C: partition frozen with DeepFreeze, but I thaw them, uninstall DeepFreeze and reboot in Windows, then reboot again with the Ubuntu CD. So I don't think DeepFreeze is the cause. 

Perhaps a fixmbr would help? I'm puzzled.


smauleon

---

### Post by garyedwardjohnston on 2008-10-30
In my case it was the cd itself.

I cleaned the cd with glass cleaner and a paper towel and it worked.

Seems like a strange fix but it worked for me.

---

### Post by caljohnsmith on 2008-10-30
If the installer fails at about 94% with a "grub-install" error, that is unfortunately a known bug, but here is a workaround:

[http://ubuntuforums.org/showthread.php?t=893156](http://ubuntuforums.org/showthread.php?t=893156)

Let me know if that works for you. :)

---

### Post by smauleon on 2008-11-02
Thank you for your answers.

Gary, I'm sure the cause was not a dirty cd. The problem appears always in the same computers, even with different CDs.

Cal, I'll try your solution next tuesday and I'll let you know.

Thanks again,

smauleon

---

### Post by smauleon on 2008-11-06
Well, it worked!

Using ext2 instead of ext3 fixes the problem. I haven't tried to convert the format after installing, I'm just introducing Linux to my pupils after all.

Thanks again Cal,

smauleon

---

