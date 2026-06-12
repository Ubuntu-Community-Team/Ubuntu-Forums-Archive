---
title: "Packaging overwrite issues"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by AngelousAmore on 2010-01-22
I'm fairly new to the forums but I'm having some packaging issues. I follow the instructions given to both through the terminal and synaptic. First synaptic tells me to use the broken packages filter and when I use that this is the error I get

E: /var/cache/apt/archives/arc-brave_2.7-1ubuntu1_all.deb: trying to overwrite '/usr/share/gdm/themes/Arc-Brave/logo.png', which is also in package ultimate-edition-themes 0
E: /var/cache/apt/archives/arc-human_2.7-1ubuntu1_all.deb: trying to overwrite '/usr/share/gdm/themes/Arc-Human/logo.png', which is also in package ultimate-edition-themes 0
E: /var/cache/apt/archives/arc-wine_2.7-1ubuntu1_all.deb: trying to overwrite '/usr/share/gdm/themes/Arc-Wine/logo.png', which is also in package ultimate-edition-themes 0
E: /var/cache/apt/archives/arc-wise_2.7-1ubuntu1_all.deb: trying to overwrite '/usr/share/gdm/themes/Arc-Wise/logo.png', which is also in package ultimate-edition-themes 0



 then from trying to bypass that error information I get this error in my terminal

                          The following NEW packages will be installed:    arc-brave arc-human arc-wine arc-wise 
 0 upgraded, 4 newly installed, 0 to remove and 53 not upgraded. 
 1 not fully installed or removed. 
 Need to get 0B/1,570kB of archives. 
 After this operation, 2,265kB of additional disk space will be used. 
 Do you want to continue [Y/n]? y 
 (Reading database ... 554058 files and directories currently installed.) 
 Unpacking arc-brave (from .../arc-brave_2.7-1ubuntu1_all.deb) ... 
 dpkg: error processing /var/cache/apt/archives/arc-brave_2.7-1ubuntu1_all.deb (--unpack): 
  trying to overwrite '/usr/share/gdm/themes/Arc-Brave/logo.png', which is also in package ultimate-edition-themes 0:0.0.7 
 dpkg-deb: subprocess paste killed by signal (Broken pipe) 
 Unpacking arc-human (from .../arc-human_2.7-1ubuntu1_all.deb) ... 
 dpkg: error processing /var/cache/apt/archives/arc-human_2.7-1ubuntu1_all.deb (--unpack): 
  trying to overwrite '/usr/share/gdm/themes/Arc-Human/logo.png', which is also in package ultimate-edition-themes 0:0.0.7 
 dpkg-deb: subprocess paste killed by signal (Broken pipe) 
 Unpacking arc-wine (from .../arc-wine_2.7-1ubuntu1_all.deb) ... 
 dpkg: error processing /var/cache/apt/archives/arc-wine_2.7-1ubuntu1_all.deb (--unpack): 
  trying to overwrite '/usr/share/gdm/themes/Arc-Wine/logo.png', which is also in package ultimate-edition-themes 0:0.0.7 
 dpkg-deb: subprocess paste killed by signal (Broken pipe) 
 Unpacking arc-wise (from .../arc-wise_2.7-1ubuntu1_all.deb) ... 
 dpkg: error processing /var/cache/apt/archives/arc-wise_2.7-1ubuntu1_all.deb (--unpack): 
  trying to overwrite '/usr/share/gdm/themes/Arc-Wise/logo.png', which is also in package ultimate-edition-themes 0:0.0.7 
 No apport report written because MaxReports is reached already 
                                                               dpkg-deb: subprocess paste killed by signal (Broken pipe) 
 Errors were encountered while processing: 
  /var/cache/apt/archives/arc-brave_2.7-1ubuntu1_all.deb 
  /var/cache/apt/archives/arc-human_2.7-1ubuntu1_all.deb 
  /var/cache/apt/archives/arc-wine_2.7-1ubuntu1_all.deb 
  /var/cache/apt/archives/arc-wise_2.7-1ubuntu1_all.deb 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 

Right now this issue is of course preventing me from doing any updates and installs on my system and its getting annoying. Any help would be much appreciated and the current operating Linux I'm running is "Ultimate Edition 2.5".

---

### Post by diesch on 2010-01-22
The arc-* packages contain some files that are also contained in the package *ultimate-edition-themes* so you can't have both installed. Either remove the arc-* packages or  *ultimate-edition-themes.*

---

### Post by AngelousAmore on 2010-01-22
> **diesch said:**
> The arc-* packages contain some files that are also contained in the package *ultimate-edition-themes* so you can't have both installed. Either remove the arc-* packages or  *ultimate-edition-themes.*
I understand removing one or the other however when I attempt to remove them through the terminal it regurgitates this  You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  arc-colors: Depends: arc-brave but it is not going to be installed
              Depends: arc-human but it is not going to be installed
              Depends: arc-wine but it is not going to be installed
              Depends: arc-wise but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

even after attempting to remove arc this really beginning to frustrate me I may just wipe out all my themes and then go from there but I'm trying to avoid that if possible. Is there someone to possible tell the system to ignore arc and its sub-groups and proceed with the rest?

---

### Post by diesch on 2010-01-22
You can use
>  apt-get remove arc-\*
to remove all packages starting with* arc-*

---

### Post by AngelousAmore on 2010-01-27
Thanks problem solved

---

