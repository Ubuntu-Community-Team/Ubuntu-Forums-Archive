---
title: "Uninstall 6.10 and install 6.06"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by markml on 2006-12-11
Hi,
I am very much a newbie to Ubuntu. I have installed 6.10 and although I have a great deal of success, I have a number of hardware problems, that I should be able to solve if I had installed 6.06.
What is the simplest way to uninstall 6.10 and re-install 6.06?
My machine is a dual boot system with a partitioned hard drive with Windows XP.

Many thanks

Mark

---

### Post by bapoumba on 2006-12-11
Hi,
do you have a separate /home partition ?

If so, choosing the  expert mode during the installation process, will allow you to reinstall dapper on the the edgy root (/) partition (hd??) which will be formated and keep all your stuff in /home (hd?? partition, leave it **unformated**).

**cat /etc/fstab** --> will let you know the hd?? for / and /home.

Please backup all your important files before reinstalling, as there always is a risk of loosing data (choosing incorrect options for ex.).

---

