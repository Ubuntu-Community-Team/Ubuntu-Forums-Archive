---
title: "How to install to new HD and move data properly"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by AJI on 2006-08-11
I currently have Kubuntu 5.10 running fine on a poorly-configured HD (I partitioned only half the space, /boot is too small and /swap is 10 times larger than necessary).

I want to install Kubuntu 6.06.1 to a new HD and move my current contents (/home/, some /var/ directories, a Samba tree) to the new installation.  That would leave me in a position to use the old HD as the 2nd drive in a RAID 1 array.

**Questions**:
[LIST]
[*]Is the following sequence a good way to do it?
[*]Am I leaving any important steps out?
[*]How should I transfer /home/specificuser ?  Is it ok to use "cp -a"?  Can I do so while running the GUI *as that user*, or should I exit KDE & use the command line?
[/LIST]

**Process**
[LIST=1]
[*]install new HD
[*]insert Kubuntu 6.06.1 CD
[*]reboot
[*]set BIOS to boot from new drive 1st, then CD
[*]install Kubuntu
[*]add users
[*]mount previous version
[*]copy files
[*]done!
[/LIST]

Suggestions and links to more information greatly appreciated. :KS

---

