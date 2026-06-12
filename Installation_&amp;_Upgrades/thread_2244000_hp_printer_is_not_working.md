---
title: "hp printer is not working"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by sbshaikh on 2014-09-12
Printer was working fine on Ubuntu 12.10, then shortly after upgrade to  Ubuntu 14.04, when I wanted to print for the first time, I found that the printer was not being found.
The system will not auto-detect the printer. what should I do or as to how I get resolved this problem. please help me to resolve the problem.
When I checked the status of hplip then my terminal window shows following output:


                      ubuntu@ubuntu-linux:~$ dpkg -l | grep hplipii  hplip                                                       3.14.3-0ubuntu3.2                                      i386         HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                                  3.14.3-0ubuntu3.2                                      all          HP Linux Printing and Imaging - data files
ii  hplip-gui                                                   3.14.3-0ubuntu3.2                                      all          HP Linux Printing and Imaging - GUI utilities (Qt-based)
ubuntu@ubuntu-linux:~$

---

### Post by yancek on 2014-09-12
The obvious first, make sure it is securely plugged in and turned on then go to System Settings and find the Printer option.  What happens from there?  If you have done this already, post what the results were.

---

### Post by sbshaikh on 2014-09-13
Thanks a Lot..Friend..

---

