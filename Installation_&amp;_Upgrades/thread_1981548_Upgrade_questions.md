---
title: "Upgrade questions"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2012-05-17
I'm considering upgrading, and I have the following questions:
1) Can I upgrade over my existing system, keeping my installed software, data files, etc?
2) Can I simply install a new version of my current system (10.04) to fix system errors caused by an attempt to install software that was for a later version of Ubuntu?  Will this allow me to keep my installed software?  Data files?
3) If I do upgrade, and desire a pretty stable system and updates, but later than 10.04, what should I choose?  I rely on the system, and can't have it crashing often.

Any and all advice would be appreciated!

---

### Post by Skaperen on 2012-05-17
Lots of people prefer to upgrade this way ... over the existing system.  It usually works just fine.  If you have made certain kinds of changes, it may run unto problems.

I typically do full re-installs on another machine, then migrate services or everything at once, often by a quick switch of IP address.  But I'm doing this because we typically prefer to keep downtime as small as possible, and want a fallback path, as well as pre-testing, to minimize the downtime.

For a home desktop, your personal needs are the primary issue.

I'd go with 12.04.  We already have a couple machines on 12.04 (one launched as beta2, and upgraded since then).  The only issues I have run into affected by desktop (sound handling bugs and worse UX).

---

### Post by jadtech on 2012-05-17
12.04 is very stable 
though I recommend a fresh clean install ,if you have room to do it just make room and partition for the new install keeping what you already have once it going  and your feel confident programs all going you can move files on to the new install :) 

or you could back everything up  go for the upgrade and pray it all goes well ...

---

### Post by Skaperen on 2012-05-17
> **jadtech said:**
> 12.04 is very stable 
though I recommend a fresh clean install ,if you have room to do it just make room and partition for the new install keeping what you already have once it going  and your feel confident programs all going you can move files on to the new install :) 

or you could back everything up  go for the upgrade and pray it all goes well ...

Or buy a 2nd hard drive and install on it ... switching hard drives when needing to go back to USING your old system for a while.  Once the new system is installed, tweaked, and you have all those extra packages installed that you had on the old one, then attach the old drive as the 2nd drive and copy all the /home files over.  After a couple weeks and you are sure nothing more needs to be copied and you're staying on the new system, you can repartition and format the old drive and use it as a backup drive.

---

### Post by RogerDavis on 2012-05-17
How about re-installing 10.04 (I guess I can get a download of the current version?).  Would that likely be less risky, and fix the minor problems I currently have?

---

### Post by mastablasta on 2012-05-17
> **RogerDavis said:**
> How about re-installing 10.04 (I guess I can get a download of the current version?). Would that likely be less risky, and fix the minor problems I currently have?
 
 
if you have updated regulary you already have 10.04, the latest version.
 
reisntall would solve your issues, but you will also need to reinstall the programmes. partial upgrade is also possible but not recommended.
 
It would be best to backup your home and do a fresh install of 12.04 (which comes with new interface but ther eis a gnome fallback session available as well as MATE and Cinamon desktop verisons avaialble for those that prefer more traditional approach).
 
make sur eoyu backup up hidden files in home (they uusally include settings and maybe some programmes) you can use mintabackup tool to help you.

---

### Post by RogerDavis on 2012-05-17
Is 12.04 a long term release, with full support for a long time?

Does an upgrade usually go ok over the existing version, and leave the programs and data in place and functional?

I presume the best / safest way is from an ISO CD?

Or maybe the network method as below
-----------------
It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading.

To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

    Start System/Administration/Software Sources
    On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
    Press Alt-F2 and type update-manager -d
        Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
        A message will appear informing you of the availability of the new release. Click Upgrade. 
    Follow the on-screen instructions. 
-------------------------------------------------------

Thanks!

---

### Post by pabloikba on 2012-07-05
I have a Dell XPS Studio 7100 with 1TB hard drive and 500GB hard drive. The 1TB is sda running 10.10. The 500GB is sdc running 12.04 w/Cinnamon. I have all of the files I want from the 10.10 installation copied onto 12.04 and am ready to get rid of 10.10.
Is there a way to copy 12.04 from 500GB drive onto 1TB drive and replace 10.10? Or, do I need a complete new install of 12.04 on the 1TB drive?
(I want to use the 500GB for another computer when I am finished using 12.04 on it.
Many thanks for any help.
Pablo

---

