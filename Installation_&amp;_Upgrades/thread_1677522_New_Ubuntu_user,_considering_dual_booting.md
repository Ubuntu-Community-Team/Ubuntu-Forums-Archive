---
title: "New Ubuntu user, considering dual booting"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by Frank Einstein's Bride on 2011-01-28
Last week Windows XP suffered death by virus, I didn't have a disc to reinstall and had a friend install Ubuntu instead. It's been good so far with a few exceptions and now I'm considering installing windows 7 as a dual boot. I was planning on getting a new 1TB SATA HD  (currently using a 320GB IDE installed) I was planning on installing Ubuntu on the new 1TB and windows on my current 320GB as it's looking like I will get more use from Ubuntu now.

I've been reading how to do this, as it will be the first time I've installed an OS myself, Would I be right in assuming the easiest way to go about this would be to wire in the new 1TB drive and remove the 320GB and install Ubuntu from cd onto the TB drive. Then removing the 1TB drive and putting in the 320GB and installing windows 7 on it finally connecting both drives? Does Ubuntu +grub need to be on hard drive 1 to work, if so how do I ensure the TB is drive 1 and not the old 320GB?

I was going to get a new wireless network card as well, this one I'm currently using is quite dated and took a much more technically capable friend several hours to get working, A process I doubt I could complete with out the aid of google. Should I install the wireless card before or after the two OS?

---

### Post by Quackers on 2011-01-28
It might be a good idea to install the new network card and make sure it works in Ubuntu.
Regarding your suggestions for installing Win 7 and Ubuntu, that should work fine.
You will then have the separate bootloaders on separate drives, which is preferrable. When you've got both installed, plug both drives in (if you want Win 7 to be first hard drive use first the SATA port). Then you can choose the second hard drive as first boot device in the bios. That way, when Ubuntu boots up you can run sudo update-grub in a terminal, which will pick up the Windows Loader and give you a grub menu at startup, with a choice of operating system to boot.

---

