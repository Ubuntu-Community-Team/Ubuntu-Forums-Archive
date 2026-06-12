---
title: "Windows 7 won't start after ubuntu install"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by xetea on 2010-01-11
Hi,

I just installed Ubuntu 9.10 on my HP Pavilion dv6-1341eo and ran into some problems.

I downloaded Ubuntu 9.10 (64-bit) today and ran the live-cd. Everything seemed to work, so I installed it from the live-cd desktop. I used the "Install side by side" option and gave Ubuntu 30GB of space of my harddrive, taken from the Windows 7 partition. The install went on smoothly and I restarted when the option was given me.

When the computer started I chose Ubuntu in the GRUB menu, but xorg and/or gnome wouldn't start, all I could see was the console (xorg claimed it couldn't find a display when I wrote startx). I solved that through upgrading (apt-get upgrade), so now ubuntu works. Sort of strange that I had to upgrade though, since the live-cd worked.

Anyway, right now the problem is that Windows 7 doesn't start. It says I have to check the harddrive, but that I can cancel it by pressing any key before 10 seconds. The problem is that any key doesn't work and it gets stuck 1 second before start.

I should mention that when I try to open the windows partition in Ubuntu I have to authenticate myself, which I don't have to on my other computer which runs Ubuntu 9.04 (32-bit). Is that a new feature in 9.10? Could it have anything to do with my problems?

Do anybody know how to solve this? I'm gonna try using my Windows 7 dvd to restore things, but this is some serious problems that shouldn't occur.

Edit: Okay, I don't know what happened but when I put the windows dvd in the computer windows started as it should after the message about the harddrive check. I hope this post helps somebody.

I want to add that ubuntu seems to work perfectly on HP Pavilion dv6-1341eo, besides from what I mentioned above.

Edit2: For anyone out there who is interested: The internal speakers doesn't turn off when you plug in your headphones. That is a major problem and I have found no solutions for it.

---

### Post by presence1960 on 2010-01-12
did you use gparted from the Live CD to resize windows vista/7? If so that is the cause of your problem. You really should use windows disk management utility to shrink Vista/7 after defragging & turning off system restore.

---

### Post by wlraider70 on 2010-01-13
I used live cd and now i cant boot vista.
any soultions?


edit:
I did fix it.

[http://ubuntuforums.org/showthread.php?t=1380499a](http://ubuntuforums.org/showthread.php?t=1380499a)

---

