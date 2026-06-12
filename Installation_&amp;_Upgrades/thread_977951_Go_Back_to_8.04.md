---
title: "Go Back to 8.04"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Nirliq on 2008-11-10
I was using 8.04 and I liked it. I went ahead and let this new 8.10 update from the Auto-update now I can't get at any of my Samba drives, Firefox is like watching paint dry, I get an "Unsupported Platform" message when I try to get into my Network settings and the there is a message in the Network Settings the I need to Click the "Administrator Mode Button". There is no Administrator Mode Button! 


Was there a rush to get this OS out?  How do i go back to 8.04? :confused:

Thanks

---

### Post by eldragon on 2008-11-10
> **Nirliq said:**
> I was using 8.04 and I liked it. I went ahead and let this new 8.10 update from the Auto-update now I can't get at any of my Samba drives, Firefox is like watching paint dry, I get an "Unsupported Platform" message when I try to get into my Network settings and the there is a message in the Network Settings the I need to Click the "Administrator Mode Button". There is no Administrator Mode Button! 


Was there a rush to get this OS out?  How do i go back to 8.04? :confused:

Thanks

you will have to install from scratch...

---

### Post by slakkie on 2008-11-10
Install from scratch.. Hope you have your /home located on a different slice. Backup your /etc directory (maybe copy it to your homedir).

Good luck!

---

### Post by jimv on 2008-11-10
For the love of God, the upgrade feature is a pile of poo.  It's probably the number one cause of screwed up installations.  Can we get rid of it yet?

---

### Post by phersotty on 2008-11-10
No question just some comments and observations.  

I also did the auto update to upgrade to 8.10 this weekend.  It said it would take 4 hours, but it was closer to 5 or 6 because the script started asking questions.  I can't remember if they were errors or Yes/No questions.  Anyway, it hogged my bandwidth while it downloaded all the necessary files so I couldn't use my computer as normal while the upgrade was being performed.

When the upgrade was complete I rebooted my computer to discover that my graphics driver was disabled.  For some reason 8.04 and 8.10 don't like my AGP Nvidia 9700 so in both versions I have to install the driver from the Nvidia site.  After I fixed my graphics driver I was surprised to learn that my old KDE session was gone!  As far as I can tell my only choice for KDE is 4.0  :confused:  We all know Linux is about choice and it seems that the Ubuntu upgrade makes some of those choices for us.  I had a really sweet custom KDE session setup before with custom panels, Super Karamba, Kiba Dock, AWN, Compiz,etc...  In 8.04 I had the choice at the login screen between the original KDE and the new KDE 4.0 now its just 4.0  I don't think the upgrade should have wiped out the old KDE I would prefer to still have both to choose from.  

CONCLUSION:

Overall, I am not convinced that using the built in upgrade is any better than downloading the complete iso especially when upgrade took so long to download.  At least with the iso I can create a Live DVD of 8.10 test it out and then decide if I really wanna upgrade or stick with what I've got.

---

### Post by jimv on 2008-11-10
Yeah, I tried the upgrade once from 7.04 to 7.10 and I never tried it again.

My method now is to try the LiveCD to see if the new release boots without any major issues.  Then I install the new release onto it's own partition.  Then I migrate all my settings from my home folder over.  If everything works good, I wait a few weeks until I'm comfortable and then remove the partition with the old release on it.

---

### Post by hendoc on 2008-11-10
I burned the iso for 8.10, installed, and it would not let me on the web. The network manager said NEVER for connection type. I never did get it to change. I reinstalled 8.04 from the disk and figured I'd try it again with the upgrade . I still have not been able to initiate the upgrade. Maybe I'll give them a few weeks at least to get it together. Staying with Hardy is not a problem. I love it.

---

