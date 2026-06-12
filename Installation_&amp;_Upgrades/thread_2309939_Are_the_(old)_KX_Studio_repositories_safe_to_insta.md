---
title: "Are the (old?) KX Studio repositories safe to install into a new Ubuntu (Studio)?"
date: 2016-01-14
forum: Installation &amp; Upgrades
---

### Post by yoshii on 2016-01-14
It used to be somewhat common practice to install the KX Studio repos on top of Ubuntu Studio or other Ubuntus.  
I am wondering if this is still safe?  The reason why I ask is because I did it and looked at the installed PPA list for KX Studio and it includes entries for Lucid AND Trusty.  
My current system is Trusty (Trusty Tahr) so it seemed somewhat dangerous to me to be installing outdated stuff from Lucid, which is several years old now.  
Ultimately, I removed the entries before performing a sudo update and sudo upgrade.  My system is stable, but I have the suspicion that installing old Lucid packages instead of Trusty packages could be a stability risk.  

For what it's worth, I followed the normal instructions from within the KX Studio website where it describes the Ubuntu installation instructions.  

Does anybody have any thoughts or experience on this?

---

### Post by grahammechanical on 2016-01-14
Personal Package Archives (PPA) are a kind of software repository. There should a separate repository for each supported version of Ubuntu and each PPA should have its own location on the servers.

So, if we are using trusty (14.04) and we install a PPA for trusty then there should be no problem. In fact if we follow the usual method for setting up a PPA as a software source then the code name for our version of Ubuntu will automatically be inserted in the URL to the location of the Archive,

For example. If the PPA is for trusty & we are using Ubuntu wily, then "wily" would become part of the URL and there would be update errors if there is no PPA for wily. 

If we entered the location by hand so that the URL contained the name "trusty" but we were using Ubuntu wily then we might get package conflicts if we update & install the application or packages. But maybe not.

Regards

EDIT: The launchpad page for the KXStudio PPA says not to use the PPA and provides a link to this web page. It provides instructions for installing on Ubuntu 14.04 & 15.10.

[http://kxstudio.linuxaudio.org/Repositories](http://kxstudio.linuxaudio.org/Repositories)

---

