---
title: "[SOLVED] Oops!"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-01-07
I gotta' do a distro upgrade.

THIS time, I need to backup first, kinda' like system restore in windows. I didn't do that on another machine last week, and my wireless config bailed on me. Bein' a nuuuuuubuntu, it was a problem.

How do I do a backup, such that if stuff gets jammed again by the upgrade, I can revert, and figure out how to solve the conflicts???

Thanks.........

---

### Post by taurus on 2008-01-07
You probably should back up your $HOME directory, all your personal settings, and /etc, system settings.

---

### Post by leonidas666 on 2008-01-07
I think there is no feature like system revert in ubuntu.
You could do the following things:
- Try running first with the liveCD. if (for example) your wireless is working with the new version on the live cd, i don't see any reason why it should stop working after the upgrade on your hd.
- If you want to be completely sure, you could make a backup of your system partition (you do have one partition for the system, and one for your home directory, right?). This should only be a few GB, so the complete backup should not be so problematic. If something goes wrong, you can use the backup to get your system to the previous state.
- while you are at it, of course making a backup of your home partition also doesn't hurt.

For making the backup, you can use dd. More info in google or here:
[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)
However, you should read the documentation very carefully, because you could accidently delete all your data. For backing up your system partition, it's best if you boot with the livecd, and make the backup while running from the livecd so that the system partition is not in use.

---

### Post by buccaneere on 2008-01-08
I don't know if I did the back-up correct or not, but I pulled the trigger on upgrade.

And I still got wireless! 

Now that I remember, it was a Broadcom box in which I got jammed, and I have not upgraded it... Exactly how is backup executed, when done on local disk???

---

