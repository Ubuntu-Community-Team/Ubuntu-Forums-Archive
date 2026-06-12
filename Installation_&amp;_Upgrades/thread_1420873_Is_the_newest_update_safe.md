---
title: "Is the newest update safe?"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by 006ruler on 2010-03-03
Hi all, I am asking this question because the LAST time i installed the selected upgrades, it distroyed the operating system and i had to reinstall it. Is this update safe, as in it won't send me to the text startup where it needs something it doesn't have?

---

### Post by ajgreeny on 2010-03-03
What update(s) are you talking about?  Also what update caused the problem you are saying caused the destruction of your system last time, which I think is not really what happened?

I think it may have been something as simple as a new kernel, and that does not actually destroy your system at all, but may make the display disappear, depending on the graphics card you have.

---

### Post by Timothy Taylor on 2010-03-03
If your system is working, leave it alone!

I tried upgrading to 9.10 and have had nothing but trouble just trying to get the wretched thing to run.

I'm now back to running XP.  How depressing is that?

---

### Post by presence1960 on 2010-03-03
> **Timothy Taylor said:**
> If your system is working, leave it alone!

I tried upgrading to 9.10 and have had nothing but trouble just trying to get the wretched thing to run.

I'm now back to running XP.  How depressing is that?

very depressing given the fact if 9.10 wouldn't work on your machine you could have installed 9.04

---

### Post by MasterMac on 2010-03-04
I just bought this netbook 2 weeks ago. It HAD Windows 7 Starter pre-installed, which was absolute crap. So I looked into Linux and found the netbook remix Ubuntu 9.10. Install went well and I'm running it now. So far I haven't had any problems. But that still remains to be seen I guess.

---

### Post by BenAshton24 on 2010-03-04
You can check if there are any update problems via ubuntu's new twitter account. [http://twitter.com/ubuntustatus](http://twitter.com/ubuntustatus)

---

### Post by spectralblue on 2010-03-04
As always, individual systems vary, and with each release of ubuntu, they try to have support for as many systems available while keeping the size of the iso low. 

Because of these, on some systems, a little configuration is needed, kinda like loading drivers for Windows. In most systems though, ubuntu should install with no problems, and you should be able to use it fine. As always though, whenever you're upgrading, you should always consider backing up your data - as is with any operating system. 

I don't think any update in ubuntu actually would destroy your system, unless of course it was interrupted during a critical state (like a sudden power outage). If it can't display your desktop, or your graphics are messed up, you can usually use the previous kernel as mentioned, activate another driver, reinstall something via the command line, etc. and you can get help, just like this :)

---

### Post by Timothy Taylor on 2010-03-04
> **presence1960 said:**
> very depressing given the fact if 9.10 wouldn't work on your machine you could have installed 9.04

[[COLOR="Blue"]_Yeah, right..._[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8914683#post8914683")

---

### Post by slakkie on 2010-03-04
> **006ruler said:**
> Hi all, I am asking this question because the LAST time i installed the selected upgrades, it distroyed the operating system and i had to reinstall it. Is this update safe, as in it won't send me to the text startup where it needs something it doesn't have?

Step one: [http://clonezilla.org](http://clonezilla.org)
Step two: Burn the clonezilla image to a CD
Step three: Reboot from the clonezilla CD and clone your whole disk and/or root partition
Step four: Boot Ubuntu, do the upgrade
Step five: Reboot (for the kernel updates etc etc)
Step six: Enjoy

If step six fails:
Step seven: Boot from clonezilla CD
Step eight: Restore your partition/disk
Step nine: Reboot and enjoy your current installation once again.

And you have nothing to worry about.

---

