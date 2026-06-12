---
title: "reinstall 14.04 or go to 16.04"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2016-07-01
I've had 14.04 installed for a few years and it has become corrupted and quirky. I don't know if I should do a reinstall over the existing version.
Would it be possible to do a complete new install of 14.04 side by side, or install the new Ubuntu 16.04 in a separate partition.
If I chose to install 16.04, will I have to go through the version upgrades like I do with the usual process?

I'd like some help with these questions.
Thanks

---

### Post by sudodus on 2016-07-02
It is a good idea to try the systems you want to install:

1. live before installing

2. install a new system alongside the current system in the internal drive or in an extra USB 3 pendrive before deciding which system to make as your main system.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Gnusboy on 2016-07-02
Ok. Thanks.
One more question: If I install 16.04 alongside the 14.04 - does the new version have to be in a different partition?
Can I install it into the same partition as my current version and will both versions be discrete i.e. Boot into one, or the other as I chose?

Oops. That's actually 2 questions. :)

---

### Post by howefield on 2016-07-02
16.04 would need a separate partition if you wanted to boot into both 14.04 and 16.04 as required. The 2 installs could share the same swap partition though.

Installing into the 14.04 partition would wipe out that install.

---

### Post by grahammechanical on 2016-07-02
> If I chose to install 16.04, will I have to go through the version upgrades like I do with the usual process?

I am not sure what you mean. With 14.04 you did not need to upgrade to 14.10 and 15.04 and 15.10. Did you? So, with 16.04 you will not need to upgrade to 16.10 and then 17.04 and then 17.10. Ubuntu 16.04 is a Long Term Support (LTS) release with 5 years support just like 14.04.

Regards.

---

### Post by RobGoss on 2016-07-02
This would depend if you wanting just one OS on this machine of are you trying to dual boot, if not I would just do a clean installation of Ubuntu 16.04

---

### Post by danbosse1 on 2016-07-03
I upgraded my system and have no regrets. Be sure to back up all important documents! I use Mega, 50 GB of cloud storage, and be sure to install the extension into your browser.  
If something is wrong with 14.04 you may have to re-install it.

*sudo apt-get install --reinstall ubuntu-desktop*

---

