---
title: "[SOLVED] Can't add new software from Synaptic without Ubuntu CD"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by cmdi035 on 2008-07-23
I'm a newbie to Linux and I've been running Ubuntu 8.04 for ~1 month and did the install via Wubi. All along, I have been able to add and remove applications without an issue via the Synaptic Package Manager.  Yesterday I inserted the DVD from this month's Linux Magazine (which contained Ubuntu 8.04 and 6 different flavors of Ubuntu that run in Virtualbox) into my CD/DVD burner so that I could copy of some of the iso files for Mythbuntu and Ubuntu Studio so I could burn them directly to a CD.  Unfortunately, buy putting the DVD into my drive something in Synaptic changed and now when I try to install any application from Synaptic I'm asked to " Please insert the disk labeled: Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)in drive /cdrom/ ".   

I'm assuming that when I inserted the DVD that some file was written over / changed thus requiring the new DVD to be in the tray to add new applications.  When I insert the DVD into the drive the applications installed - but I don't want to be tied to this DVD.  What file needs to be changed so that Synaptic can pull the applications & dependencies from their original sources (as it has been doing) and not from the DVD?

Thanks in advance.

---

### Post by overdrank on 2008-07-23
> **cmdi035 said:**
> I'm a newbie to Linux and I've been running Ubuntu 8.04 for ~1 month and did the install via Wubi. All along, I have been able to add and remove applications without an issue via the Synaptic Package Manager.  Yesterday I inserted the DVD from this month's Linux Magazine (which contained Ubuntu 8.04 and 6 different flavors of Ubuntu that run in Virtualbox) into my CD/DVD burner so that I could copy of some of the iso files for Mythbuntu and Ubuntu Studio so I could burn them directly to a CD.  Unfortunately, buy putting the DVD into my drive something in Synaptic changed and now when I try to install any application from Synaptic I'm asked to " Please insert the disk labeled: Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)in drive /cdrom/ ".   

I'm assuming that when I inserted the DVD that some file was written over / changed thus requiring the new DVD to be in the tray to add new applications.  When I insert the DVD into the drive the applications installed - but I don't want to be tied to this DVD.  What file needs to be changed so that Synaptic can pull the applications & dependencies from their original sources (as it has been doing) and not from the DVD?

Thanks in advance.

Hi and welcome, you can try and remove the DVD from your source list. System, Administration, software sources, then uncheck any box that is checked by the cdrom.

---

### Post by cmdi035 on 2008-07-29
Thanks Overdrank for you help!  That solve the problem.

---

