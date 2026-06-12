---
title: "Computer shut off during Upgrade."
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by Son Of Nova on 2011-08-02
Last night I decided to upgrade to Natty Narwhal 11.04 from MM10.10. I tried to leave it to install overnight.

Some bright spark turned off the power supply to my computer.

I don't know exactly what stage the installation was at, but it must have been installing the upgrade at least, because I'm now locked out of my computer.

Boot up progresses until the ubuntu loading screen. At this point is says,
 
'Ubuntu 10.10'

The disk drive for / is not ready yet or not present
Continue to wait; or press s to skip mounting or M for manual recovery.

(If I press 'S', it says something like 'cannot find /tmp folder')

I don't know if the upgrade installation was completed, but I suspect not, because the power was turned off just an hour into the installation. Also it still tries to load Ubuntu 10.10.

Anything I can do besides formatting for a fresh 11.04 install? If only to save some files?

---

### Post by westie457 on 2011-08-02
> **Son Of Nova said:**
> Last night I decided to upgrade to Natty Narwhal 11.04 from MM10.10. I tried to leave it to install overnight.

Some bright spark turned off the power supply to my computer.

I don't know exactly what stage the installation was at, but it must have been installing the upgrade at least, because I'm now locked out of my computer.

Boot up progresses until the ubuntu loading screen. At this point is says,
 
'Ubuntu 10.10'

The disk drive for / is not ready yet or not present
Continue to wait; or press s to skip mounting or M for manual recovery.

(If I press 'S', it says something like 'cannot find /tmp folder')

I don't know if the upgrade installation was completed, but I suspect not, because the power was turned off just an hour into the installation. Also it still tries to load Ubuntu 10.10.

Anything I can do besides formatting for a fresh 11.04 install? If only to save some files?
When you turn on your computer and your Grub menu is displayed do you have the option to boot into an earlier kernel version. They look something like this EG 2.6.30-35 (the newest) 2.6.28-30 (older).

Select one of the earlier ones and then redo all the updates and then run the upgrade.

---

### Post by Son Of Nova on 2011-08-03
Hey westie457, thanks for replying. 

I've just had the opportunity to try that, the earlier options present the same thing as the most recent boot.

Any other ideas?

---

### Post by dodle on 2011-08-03
I would try re-installing from a live CD without formatting. That way you should get a fresh install without losing your files. During the install you'll probably have to use the manual partition editor. My guess is that the partitions are already set up correctly, you will just have to set the mount points and make sure that "Format" is unchecked for all the partitions on which you want to save the data.

---

### Post by Son Of Nova on 2011-08-04
> **dodle said:**
> I would try re-installing from a live CD without formatting. 

Just gave that a go. Installed ubuntu 10.10 on a small 7GB partition, and from there I can access all of my files.

Man, its annoying though, because I had wine set up and web-browsing with shockwave, and google chrome and java working nicely. I know I'm getting greedy now, but is it at all possible to resume the upgrade in anyway to get my old system structure back?

If not, I'll just bite the bullet, grab my files, re-format and upgrade to NN.

---

