---
title: "Minimal BASH-like line editing is supported ......."
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by nabeels on 2009-12-21
Hello everybody
I installed ubuntu v9.10 (ubuntu installer for Windows, wubi) a week ago on my Vista operating laptop (No partition was made). Last night, after finishing the installation of two main programs, I was asked by ubuntu to install some updates. Unfortunately, I'm not able to get into the ubunto environment again after the startup and the following message comes:
"Minimal BASH-like line editing is supported ....." and some Grub problems:confused:. I can still see the option list but once I choose "ubuntu", the above message appears.
My questions are:
1. How can I solve this problem knowing that, I don't have the CD for Wubi?
2. How can I avoid this problem in future?
By the way, I tried some of the solutions available in the forum and none could success.
Thank you all in advance and your help is really appreciated
Regards
nabeel

---

### Post by talsemgeest on 2009-12-21
> **nabeels said:**
> Hello everybody
I installed ubuntu v9.10 (ubuntu installer for Windows, wubi) a week ago on my Vista operating laptop (No partition was made). Last night, after finishing the installation of two main programs, I was asked by ubuntu to install some updates. Unfortunately, I'm not able to get into the ubunto environment again after the startup and the following message comes:
"Minimal BASH-like line editing is supported ....." and some Grub problems:confused:. I can still see the option list but once I choose "ubuntu", the above message appears.
My questions are:
1. How can I solve this problem knowing that, I don't have the CD for Wubi?
2. How can I avoid this problem in future?
By the way, I tried some of the solutions available in the forum and none could success.
Thank you all in advance and your help is really appreciated
Regards
nabeel
Does the message come up before or after the windows boot selection screen?

---

### Post by nabeels on 2009-12-21
> **talsemgeest said:**
> Does the message come up before or after the windows boot selection screen?
 It comes after the boot selection screen and after choosing ubunto as the OS. Windows Vista can be started very smoothly!
Any suggestion?!!!!

---

### Post by talsemgeest on 2009-12-21
> **nabeels said:**
> It comes after the boot selection screen and after choosing ubunto as the OS. Windows Vista can be started very smoothly!
Any suggestion?!!!!
I have very little experience with Wubi, so all I can suggest is to either download or order an ubuntu cd, and do a proper install.

The problem appears to be that the grub is unable to mount the root filesystem, which in wubi is a file on the windows drive. Since you don't have access to any Linux tools, I cannot see how you could fix it.

---

