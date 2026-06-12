---
title: "Upgrade 6.06 to 7.04 Evolution"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by gabbman on 2007-04-01
I have run 6.06 on my laptop for almost two years now, and Fiesty (Beta) Live works flawlessly, so in anticiapation of the clean install when it released, how to I export my Evolution files, folders, calender, and contacts to another drive for a sucessful retreive after a clean install of fiesty when it's released?

---

### Post by gabbman on 2007-04-02
I googled the right method to back up your Evolution (mail + calendar + contacts) data the right way:
I got the right method to back up your Evolution (mail + calendar + contacts) data the right way:

$gconftool-2 --shutdown
$evolution --force-shutdown

Step 2:
Create an archive with the data and configuration files:
Note: To completely save the Evolution data and configuration, you need to save the following directories/files:   
1. ~/.evolution/
2. ~/.gconf/apps/evolution/
3. ~/.gnome2_private/Evolution

then:

$cd
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution

Now the file evolution-backup.tar.gz is the backup you want. You can move the data over to another Ubuntu computer if you like, and just un-tar the archive while in your /home/username/ directory to restore it.  Copy the hidden folders back to your /home/name directory.

I've done this from my 6.06 lappy to the 7.04 test box, I'm also going to try it to PCLinuxOS to see how that goes.

---

