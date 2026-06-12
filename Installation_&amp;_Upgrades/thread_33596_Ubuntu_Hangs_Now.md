---
title: "Ubuntu Hangs Now"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by rykel on 2005-05-11
Dear friend,

I had a Ubuntu Warty machine, which I tried to upgrade to Hoary.

What I did was change all "warty" references in Synaptic to "hoary" and then did a Smart Upgrade.

Suddenly, I received a "No Signal" for my CRT monitor.

After I hard rebooted, the mouse did not work.

Next, after a second hard reboot, the whole PC hangs at the Hotplug system. There was an earlier error message about "Buffer I/O Error at hdc...", but I do not think that is a big problem as the bootup continued.

Finally, after a third hard reboot, the PC will not even start up, and the PC bell will beep frequently. (sounds like a hard disk crash to me!)


Could you please advise me:

1.   What is the officially correct way to upgrade Warty to Hoary?

2.   What can I do to resurrect my corrupted system now without resorting to format-and-reinstall?



Best Regards,

Rykel
Singapore

---

### Post by lt_kije on 2005-05-11
[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary) has the "official" upgrade notes. It does sound like your system is rather screwed up -- is there important data on it still? If so, I'd boot a live cd, copy the data off (if it's accessible), and install fresh from a Hoary CD.

Sorry...

lt_kije

---

### Post by derrick1985 on 2005-05-11
I've always been told:

"If you are upgrading your distribution, get out of your GUI"

So, best bet would be to start it up in a terminal mode. I think you type init 3 to do that.

Then, like you did, change all warty to hoary and type:

apt-get dist-upgrade

---

