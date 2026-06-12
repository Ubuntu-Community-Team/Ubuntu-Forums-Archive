---
title: "glibc detected double free or corruption"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by rold50 on 2006-06-27
Hi..

I was wondering why ever since I upgraded to dapper drake, when my upgrade manager tries to upgrade some packages.. I get this error.
It doesn't happen to all the packages. Usually, when it's upgrading gnome packages like gnome-applet, panel..etc.. I get this error message and I have a trouble installing it. I tried apt-get remove the package I still get that message.


Today, it's trying to upgrade ubuntu-docs and now I get this same error message


Setting up ubuntu-docs (6.06.2) ...
*** glibc detected *** double free or corruption (!prev): 0x0826f7d0 ***
/var/lib/dpkg/info/ubuntu-docs.postinst: line 7:  5395 Aborted                 scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 ubuntu-docs

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running. First rename this file to see if it clears the issue, and if so, try a different theme. I was using "Glider" but changed to "Human" to correct this issue.

The app in question here is zenity--attempting to pop up a minor config dialog.

---

