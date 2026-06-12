---
title: "[HACKED]  GIMP Won't Print"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by heliboy on 2015-04-10
In GIMP 2.8.10, "File | Print" causes no activity in an HP Photosmart 8750 printer.  The Print menu's default values for the printable area are subtly wrong.  lpstat -p states "Rendering completed" forever, with no mention of an error.  /var/log/syslog and /var/log/cups/error_log are unremarkable.  Printing from the "Print Preview" window causes printer activity, but no printing actually takes place, and the printer displays an error message:  "PAPER IS TOO SMALL".  In contrast, printing of the same image by EOG / Image Viewer works perfectly fine, with correct margin defaults (hence the "HACKED" prefix for this post).  Printing text with "lp" works fine.  As of about three weeks ago, when this printer was used with another computer running Ubuntu 12.04, GIMP printed fine.  I do have a moderate amount of experience with GIMP, and I'm pretty sure I'm setting the printing options correctly.

During the course of many happy hours troubleshooting this problem, I have tried all manner of printer drivers including all the non-proprietary drivers included in Ubuntu 14.04, as well as the hplip package in the standard repositories.  The driver currently in use is that which ships with hplip downloaded directly from HP (3.15.2).  It took me a long time to figure out that the printing problems are  confined to GIMP and may not be related to any particular driver.  Therefore, my system has been subject to a lot of tinkering by a knuckle-dragging end-user (me). 

My motivation for this post is mostly to characterize the problem for the benefit of the next guy or gal and point out that printing can be accomplished through EOG.  Nevertheless, if you've got a definitive fix, I'm all ears.  I do recognize that I am probably doing something wrong because these forums, as  well as sources at large, are not crawling with similar complaints.  Thanks for considering this post.

bill@dell:~$ dpkg-query -W *gimp*
gimp    2.8.10-0ubuntu1
gimp-data    2.8.10-0ubuntu1
gimp-data-extras    
gimp-help    
gimp-help-common    2.6.1-1
gimp-help-en    2.6.1-1
gimp-helpbrowser    
gimp-plugin-registry    
gimp-python    
libgimp2.0    2.8.10-0ubuntu1

bill@dell:~$ uname -a
Linux dell 3.16.0-31-generic #43~14.04.1-Ubuntu SMP Tue Mar 10 20:13:38 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
On a Dell Optiplex 960

bill@dell:~$ dpkg-query -W *gutenprint*
cups-driver-gutenprint    
gutenprint-doc    
gutenprint-locales    
libgutenprint2    5.2.10~pre2-0ubuntu2
printer-driver-gutenprint    5.2.10~pre2-0ubuntu2

---

