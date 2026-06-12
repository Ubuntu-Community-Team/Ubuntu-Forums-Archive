---
title: "Install on Mac G3 Alternative CD software selection Problem"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Gondor81 on 2008-05-12
I recently acquired a Mac G3 tower.  I did not like the Mac OS 9 install that was running on the system so I decided to put Ubuntu linux on the system.  It has a 6 GB HD with 512 MB of RAM.  I checked the system by running the Live CD with no known issues.  I could browse the web, play games, creating office documents with open office work.  So I decided to install using the live install.  This did not work.  It would hang at 46% everytime.  I let it run over night with no progress and no error messages.  I was able to move the mouse around, but nothing responded when I clicked on it so I shut the system off and tried to install with the alternate CD.  Everything was going great until I got to the Install and Select Software section.  The alternate CD gave an error message and said that I could skip this part so I went on to the next section and it had an error as well.  When I selected the yaboot section it continued on and I was able to do the Finish the Install.  Then when I rebooted I got a prompt instead of the gnome desktop.  I thought, OK and used apt-get to install ubuntu-desktop.  While it was installing there were errors on hda.  I am thinking, I must have a bad HD so I replaced it with another HD.  This did not help.

I went through the process again with a different HD and had the same issue.  When I got to the Install and Select software section it died.  This time I did a Disk check and there was a file that was corrupt.  So I burned a new disk at 8x and tried again.  The same file was corrupt when I did a CD check.  Not sure where to go next.  Does anyone have suggestions?

Thanks.

---

### Post by dstew on 2008-05-12
Did you check the downloaded .iso Md5 checksum? Even though the Live CD ran, there might be a corrupt file in the .iso that is needed for installation.

---

### Post by stream303 on 2008-05-12
You may want to post this question in the Apple forum for wider exposure.

Which G3 tower do you have?
[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html)

Note that some systems that are capable of dual-drives have had some problems needing a custom yaboot configuration.  To preserve your existing mac-os, I'd use that replacement drive, and try to keep the partitioning to no larger than 125 gb unless you have performed a firmware upgrade.

Be sure to see these two faqs

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

If you have a dual-drive capable machine, there are a few issues with that, but I'm sure that the Apple PPC gang will do their best to help you out..

---

### Post by Gondor81 on 2008-05-12
> **dstew said:**
> Did you check the downloaded .iso Md5 checksum? Even though the Live CD ran, there might be a corrupt file in the .iso that is needed for installation.

I when I ran the CD check and got the check sum error, I downloaded the alternative cd again and burned it off.

[QUOTE=stream303]You may want to post this question in the Apple forum for wider exposure.

Which G3 tower do you have?
[http://www.everymac.com/systems/appl...wermac-g3.html](http://www.everymac.com/systems/appl...wermac-g3.html)

Note that some systems that are capable of dual-drives have had some problems needing a custom yaboot configuration. To preserve your existing mac-os, I'd use that replacement drive, and try to keep the partitioning to no larger than 125 gb unless you have performed a firmware upgrade.

Be sure to see these two faqs

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

If you have a dual-drive capable machine, there are a few issues with that, but I'm sure that the Apple PPC gang will do their best to help you out.. [/QUOTE]

Thanks for the suggestions.  I have read through the PowerPC FAQ and Known Issues pages as well as done a lot of searching on my own.  The system that I have is a Blue & White.  I am not sure what processor speed, but it has the 16 MB ATI card, and the PC100 RAM as well as the 6.0 GB QuantumEX HD.  I replaced the 6.0GB drive with a 10GB Quantum Drive.  I am going to try and download the CD again and burn it then do an MD5SUM check on it.  Both times I burned the 2 different alternative install CDs I got an MD5SUM error on the same file name.

---

### Post by Gondor81 on 2008-05-13
As pointed out in another thread, the Mac G3 I am using has a problem with CD-RWs so I burned the alternative install iso to a CD-R and everything worked great.

---

