---
title: "Cloning an Ubuntu install from drive to drive"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by CDR Services on 2013-05-13
My laptop has Ubuntu 12.04 installed on a 64gig SSD and I want to clone or ghost the os to a larger SSD. Is there an easy way to do this or is it just easier to backup my content and do a clean install on the new drive?

---

### Post by oldfred on 2013-05-13
I am in the clean install group, others may suggest clonezilla or even dd.

If you are leaving old drive installed you have to edit UUIDs, change fstab & reinstall grub. If not using old drive then the duplicates will not matter.

Clean install does auto house clean histories, logs, and caches. You can copy /home if you have it on SSD using cp -a or rsync, just be sure to use paramaters to preserve permissions & ownership.

I assume when my hard drive fails that I will do a clean install. So my backup plan is to have /home, a list of installed apps and I also list hardware info. I generally manually copy any system file in /etc that I edit into /home so my regular copy of /home includes those.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
           
 rsync -auvP /home /media/backup

---

### Post by Thee on 2013-05-13
Clonezilla will do a great job, without the hassle.

---

