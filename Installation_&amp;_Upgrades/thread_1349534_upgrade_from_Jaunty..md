---
title: "upgrade from Jaunty."
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by jauntybluefish on 2009-12-08
Hi fellas,
I am considering the upgrade and will most likely go for it soon.
What I want to know is, will my home partition get zapped during the upgrade.
I have a separate partition for /home.

What do I need to do before or during the upgrade to ensure that I keep everything on /home intact.

Also, I guess I will have to be prepared to reinstall the B43xxfwcutter again to fire up my Broadcom wireless chip. Is that the case?

I am trying to avoid any audio situations with Skype too as it caused many headaches initially with Jaunty.

Any advice please?
Thanks
Andy

---

### Post by phillw on 2009-12-08
> **jauntybluefish said:**
> Hi fellas,
I am considering the upgrade and will most likely go for it soon.
What I want to know is, will my home partition get zapped during the upgrade.
I have a separate partition for /home.

What do I need to do before or during the upgrade to ensure that I keep everything on /home intact.

Also, I guess I will have to be prepared to reinstall the B43xxfwcutter again to fire up my Broadcom wireless chip. Is that the case?

I am trying to avoid any audio situations with Skype too as it caused many headaches initially with Jaunty.

Any advice please?
Thanks
Andy

Hi, your /home will be safe - Although I always advise a backup before such a major alteration to a computer.

If you boot in LiveCD mode for 9.10 - It will quickly give you a 'feel' of any issues that you may face with drivers, skype etc. It's not 100% check, but is pretty good at pointing out the majority of 'gotchas' you may encounter.

Regards,

Phill.

---

### Post by slakkie on 2009-12-08
> **jauntybluefish said:**
> Hi fellas,
I am considering the upgrade and will most likely go for it soon.
What I want to know is, will my home partition get zapped during the upgrade.
I have a separate partition for /home.


An upgrade will NOT, I repeat will NOT harm your /home directory.
Although the application which will be installed during the upgrade could change contents of some files in /home/$username, but most of them (if not all) will be located in .dirs,  eg .mozilla for firefox. I haven't noticed any issues with switching OS (hardy/jaunty/karmic) on the same box using the same homedir, but YMMV.

> 
What do I need to do before or during the upgrade to ensure that I keep everything on /home intact.


Nothing :) However, your data is as important as the amount of backups you have of that data. In other words, if the data inside your /home is precious, make sure you back it up! I use clonezilla for this. And for my homedir I also transfer files to external disks.. 

> 
Also, I guess I will have to be prepared to reinstall the B43xxfwcutter again to fire up my Broadcom wireless chip. Is that the case?


I don't have experience with this, but ideally you shouldn't, but prepare for the worst.

> 
I am trying to avoid any audio situations with Skype too as it caused many headaches initially with Jaunty.


No experience with Skype, but for me personally I haven't had any sound issues after my upgrades.

---

### Post by jauntybluefish on 2009-12-08
Thank you guys.
All my questions answered, and very quickly too.
Great place this forum!

---

