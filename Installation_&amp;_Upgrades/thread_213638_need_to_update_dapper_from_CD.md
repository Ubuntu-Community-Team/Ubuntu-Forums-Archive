---
title: "need to update dapper from CD"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by jjf on 2006-07-11
I have 10 computers on which I need to install Dapper and update it.  The problem is that I have a weak Internet connection, and the updates are up to 183 MB now.  I need some way to burn the updates to a CD, then update from that CD on the other computers.

Here's what I attempted:

01. gksudo nautilus to have permission to copy the appropriate files
02. go to /var/cache/apt/archive 
03. Select All and Copy
04. go to "Blank CD-R"
05. Paste
06. click "Burn," title the CD "ubuntu_updates"
07. pop the CD in another computer

Here's where the fishy stuff begins.  The CD doesn't mount right away.  If I eject it and put it back in a second time, it does mount.

08. r-click the orange sunburst "updates are available" icon, choose Preferences
09. click the "Add Cdrom" button

At this point Ubuntu unmounts the CD while flashing a dialog box titled "Scanning CD-ROM."  Then it pops a message box: "Please insert a disc in the drive".  Since I have on in there, I click "OK."  Then it tells me "Error scaning [sic] the CD. E:Unable [sic] to locate any package files, perhaps this is not a Debian Disc."

Help?

---

