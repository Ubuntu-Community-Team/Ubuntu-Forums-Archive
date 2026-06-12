---
title: "System crash Ubuntu 22.04 recovery help needed for MySQL"
date: 2023-06-14
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2023-06-14
I had a system crash from which I could not recover.  I had the system backed up in Timeshift.  So, after several exhausting days, I used my Live USB to reinstall the OS.  Then I began the process of installing the programs I needed in addition to what was installed from the Live USB.  Many of the applications have config files and folders scattered around, so I renamed the ones that I needed to after installing the applications (the ones created by the new install), found the ones I needed in the Timeshift files and copied them in.  Voila, I thought, things will be back to normal when I replace the new config files with the backed up ones.  That is until I got to MySQL and MySQL Workbench .  I installed MySQL, renamed all the neewly created config folders and/or files as needed, moved over the old config folders and files (obviously I did not rename any files that were contained in folders I replace, just the folder itself), and installed MySQL Workbench and did the same.  Hard stop!  When I tried to log into Workbench, I received the following:```
Cannot Connect to Database Server
Your connection attempt failed for user 'user' to the MySQL server at 127.0.0.1:3306
Access denied for user 'user' @'localhost' (using password: YES)
```
In addition, I cannot get to MySQL from the command line.  Since this always logged me in before, I am not sure how to correct this.  I assume I did not get everything restored that I needed to in order to set things as they were before the crash and reinstall.

All suggestions would be appreciated.

---

### Post by cscj01 on 2023-06-17
bump

---

### Post by cscj01 on 2023-06-20
Well, I resolved this problem..  I was able to install mysql, replace the newly created /var/lib/mysql with the one on my Timeshift backup, and all is fine.

---

