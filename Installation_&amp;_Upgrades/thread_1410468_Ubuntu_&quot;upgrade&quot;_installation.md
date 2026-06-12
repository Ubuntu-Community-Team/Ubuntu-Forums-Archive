---
title: "Ubuntu &quot;upgrade&quot; installation"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by jader32 on 2010-02-18
I have the new 9.10 Ubuntu ready to install but wonder if there is a way to upgrade without wiping out other apps and files that are in the current 7.4 (I think that's the version) I am running on my laptop.  I started from the 9.1 disk but can't see a upgrade-type install option.  Is this possible or do I really need to do a clean install of Ubuntu every time there's a new release?

---

### Post by kenny2009 on 2010-02-18
I came here looking for the exact same answer. Instead of making my own thread I'll just add to this one. I have the 9.04 distro that I would like to install tonight. However I will be away from highspeed internet for about two weeks so if I can't upgrade 9.10 without losing all my data then I'm just going to wait until I can get to the high speed internet before I do any installs because I don't have the 9.10 ISO yet.

---

### Post by kenny2009 on 2010-02-18
jader32, I found the answer to questions here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) and here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes).

To me it looks like you will have to go from version to version. > An upgrade is the process of going from an earlier version of Ubuntu to a newer version of Ubuntu. An example of this would be going from Ubuntu 7.10 to Ubuntu 8.04 LTS. To avoid damaging your system, upgrading should only be done from one release to the next release (e.g. Ubuntu 9.04 to Ubuntu 9.10) or from one LTS release to the next (e.g. Ubuntu 6.06LTS to Ubuntu 8.04LTS).
> #

You can only directly upgrade to Ubuntu 9.10 from Ubuntu 9.04 (see UpgradeNotes).  
# Be sure that you have all updates applied to Ubuntu 9.04 before you upgrade.  
#

Before upgrading it is recommended that you read the release notes for Ubuntu 9.10, which document caveats and workarounds for known issues in this version.

---

### Post by JPWhite on 2010-02-18
Let me make sure I understand you want to upgrade from Ubuntu 7.04 to 9.10?

If so it can be done, however there is no longer an *online* upgrade path for you. You will need to do incremental upgrades from CD-Roms.

Download Ubuntu 7.10 and burn a CD Rom.
On the 7.04 system go to software sources and under 'other software' add the CDRom as a source of software.
Run update manager and check for updates.
It should offer you the option to upgrade to 7.10 and should do this without losing data, programs or configs. (Do an image backup just in case).

After it is updated and finished, in software sources un-check the CD Rom you added.
Repeat for version 8.04.
Once you are upgraded to version 8.04 you should now have the option to go directly to 9.10 via online update via update manager.

That should do it.

To avoid this problem in future you should either do an online upgrade each time a new Ubuntu version comes out (once every six months) *or* stick to the LTS releases only and do an online upgrade from one LTS to the other, which will occur once every two years.

---

### Post by jader32 on 2010-02-18
Great, thanks for the help all.  I didn't know it was so easy to upgrade each version to the next.  I was actually a version behind to start, with 8.10 on my laptop.  So I had to first upgrade to 9.04 and 9.10 is now upgrading.

Thanks again for the help!

---

