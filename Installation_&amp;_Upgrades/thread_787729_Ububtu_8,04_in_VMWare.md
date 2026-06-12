---
title: "Ububtu 8,04 in VMWare"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by kangal3632 on 2008-05-09
I have been running Ubuntu 7.10 under VMWare 6.03 for some time with out any problems.  I opened a new virtual machine for Ubuntu 8.04 and did an install.  I was able to load Ubuntu and then loaded the new patches.  The process required that I enter my password - no problem.

I used Ubuntu 8.04 for a while and shut it down.  I went back a couple days later and when I tried to perform any administrator actions that requires my password it fails.  

The system does not reject the password but when you want to add a new program through Add/Remove or get new updates, a window normally pops up asking for your password.  In this case, there is a box at the bottom saying "starting admin services" but nothing happens.  I am also unable to shut down the process window without shutting down Ubuntu 8.04.  

This doesn't affect other programs and I can continue to use Ubuntu for web browsing or word processing.

I had the same problem when I did an upgrade from 7.10 to 8.04 so I deleted the virtual machine and started fresh but after the initial updates, I get the same errors.

Any one have any ideas?  I fully know that the problem maybe a VMWare/Ubuntu 8.04 compatibility issue.

UPDATE:  I finally took a look at the authentication logs and found:
kangal3632-desktop sudo: kangal3632 : unable to resolve kangal3632-desktop
kangal3632-desktop sudo: pam unable to open dlopen (/lib/security/pam_smbpass.so)
kangal3632-desktop sudo: pam [error: /lib/security/pam_smbpass.co: cannot open shared object file : no such file on directory]
kangal3632-desktop sudo: pam adding faulty module : /lib/security/pam_smbpass.so

I just logged onto my Ubuntu 8.04 and found similar errors for gdm [5187]

---

### Post by lemming465 on 2008-05-10
Hmmm.  I'm not sure what's wrong with DNS or Samba or Pam here, but something is.  As a temporary workaround while you resolve the underlying issue, one option would be to boot in recovery mode, which should put you in a single-user root shell on a text virtual console.  You can do *passwd root* to set a root password.  At that point you should be able to log in as root with the new password and can probably do maintenance.  You'd want to log out as root and back in as yourself except when you were doing software maintenance.

---

### Post by kangal3632 on 2008-05-12
Thanks for the help.  As I was browsing the forum the other evening, I found the problem and it is a known fault.  When I added my workgroup name for the office system, it modifies the user name to username.workgroup name.  Once the workgroup name is edited out from the updates will work again.

Thanks for the help.

---

