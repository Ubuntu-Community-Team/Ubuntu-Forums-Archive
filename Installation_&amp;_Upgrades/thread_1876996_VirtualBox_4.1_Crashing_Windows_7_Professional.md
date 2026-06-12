---
title: "VirtualBox 4.1 Crashing Windows 7 Professional"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by eyemole on 2011-11-07
Hi,
I am running Ubuntu Maverick 10.10 64 bit on Dell Latitude E6410. I am running VirtualBox 4.1.4 on it with Windows 7 64 Bit installed. It was running fine. But suddenly I see windows 7 after the boot just crashed and VirtualBox shows aborted. It could not even stand more than 2 mins after logging. It was working fine until previously. I had done no kernel updates or any other system updates. 
I even tried upgrading VirtualBox to 4.1.6 but no luck.

Is anyone facing same problem.

PS: I have been running VirtualBox and Windows 7 professioanal 64 bit since last one year and find no issues. But it suddenly started happening.

---

### Post by xyphias on 2011-11-10
Hi,  I am having the same problems.  I am running Oneiric 11.10 64 bit.  I have VB 4.1.6 with Windows 7 Home Provessions 64 bit running just fine.  2 days ago I installed the r74713 upgrade with problems - I had to uninstall 4.1.6 and then reinstall the new release.  Since then I have had a nightmare with, probably my mistake, reverting back to a virtual machine from a cople of months ago including files etc with no access to my windows backup, which had also gone.  Is there a problem with r74713 or Windows 7?  I have even done another clean install of VB to no effect.  Next step is to build a new win7 machine when I get some time.

Anybody got any ideas?

Thanks

---

### Post by recluce on 2011-11-10
> **xyphias said:**
> Hi,  I am having the same problems.  I am running Oneiric 11.10 64 bit.  I have VB 4.1.6 with Windows 7 Home Provessions 64 bit running just fine.  2 days ago I installed the r74713 upgrade with problems - I had to uninstall 4.1.6 and then reinstall the new release.  Since then I have had a nightmare with, probably my mistake, reverting back to a virtual machine from a cople of months ago including files etc with no access to my windows backup, which had also gone.  Is there a problem with r74713 or Windows 7?  I have even done another clean install of VB to no effect.  Next step is to build a new win7 machine when I get some time.

Anybody got any ideas?

Thanks

Did you try downgrading VirtualBox to the last known good version? Synaptic, for example, allows you to force a version. If this should work, I would head over to the forums at virtualbox.org and ask there.

---

### Post by xyphias on 2011-11-10
I used the latest deb package from Oracle so I assume it is the latest good version. Windows is going through lots of updates and reboots at the moment so I cannot give an up to date statement of stability but seems a bit better at the moment. I am installing Office as I need Publisher for work so will wait for the next reboot that it needs! Oh how I prefer Ubuntu

---

### Post by recluce on 2011-11-10
> **xyphias said:**
> I used the latest deb package from Oracle so I assume it is the latest good version. Windows is going through lots of updates and reboots at the moment so I cannot give an up to date statement of stability but seems a bit better at the moment. I am installing Office as I need Publisher for work so will wait for the next reboot that it needs! Oh how I prefer Ubuntu

Installing from the .deb will not allow you to easily up/downgrade from Synaptic, also you will not get automatic updates. Try adding the following, official source:

[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib

Replace "lucid" with your version of Ubuntu, if applicable. Detailed instructions can be found on the virtualbox.org download site. Note that fully automatic upgrades happen within the minor versions only, eg "4.1.x", once "4.2.x" comes around, you will need to use Synaptic to upgrade.

---

### Post by xyphias on 2011-11-10
Thanks Recluse I have done all that and so hopefully all will keep updating.  My problem with the upgrade was virtualbox updates being disabled when I upgraded to 11.10 but now sorted in /etc/apt/sources.list.  It is looking like an issue with Win7.  It has finished updating and has been stable for the last hour whilst I have installed Office and it is now doing a system backup.

Thanks again :)

---

