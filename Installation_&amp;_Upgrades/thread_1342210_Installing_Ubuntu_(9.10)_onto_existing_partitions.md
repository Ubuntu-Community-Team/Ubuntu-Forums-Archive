---
title: "Installing Ubuntu (9.10) onto existing partitions"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by olmecnz on 2009-11-30
I have and existing ubuntu system which I have upgraded from 9.04 to 9.10

Since the upgrade there seem to be some issues (documented in another thread) and as I am relatively new to this stuff I am looking at reinstalling ubunutu 9.10 from the CD i have here.

My question is:
Can I install ubuntu from the CD onto the existing partition structure I have (separate /home and /) without destroying the data on there? I have some systems already setup (apache and so on) that I do not want to delete.

Is this possible, what is the best approach?

Many thanks.
Olmec

---

### Post by diaa on 2009-11-30
Yes, this is possible, I have done it.

I usually use the advanced partitioning option in the Ubuntu installer and then select the root, home and swap partitions, unless you tell it to format one of them the data will remain there(except for the root partition).

However I advice you to take a backup of your home partition, it never hurts.

For the backup you can use partimage which works very well and even compresses the backed-up data.

---

### Post by grizzler on 2009-11-30
Doesn't apache store things in /var somewhere? Better check that too before you lose the sites you built.

---

### Post by t.h.w. on 2010-01-22
Thanks for this!
I have some problems with my screensaver now and some ather things... I don't trust my installation anymore and want to reinstall (have upgraded from 9.04 to 9.10). A fresh install without losing my existing data and partition-scheme is very welcome I think... 

A suggestion I found for reinstalling all your installed packages:
[http://www.addictivetips.com/ubuntu-linux-tips/reinstall-your-currently-installed-packages-after-a-fresh-ubuntu-install/](http://www.addictivetips.com/ubuntu-linux-tips/reinstall-your-currently-installed-packages-after-a-fresh-ubuntu-install/)

Going to try this this weekend!

Greetz!

---

### Post by oldfred on 2010-01-22
I did the same thing except using the command line.
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

You also have to be sure to enable the same sources and repositories. 

Command line version:
Make list:
sudo apt-get -y update
sudo apt-get dselect-upgrade
dpkg --get-selections | grep -v deinstall > ubuntu-files


reinstall from my history:
  101  sudo apt-get update
  102  sudo apt-get dist-upgrade
  104  sudo dpkg --set-selections < ubuntu-files
  105  sudo dselect
  106  sudo apt-get -y update
  107  sudo apt-get dselect-upgrade

I tried this from my old install that I had upgraded for three years to a test install and I got tons of old packages that I did not want anymore. But it worked great for installing to my portable where I copied from my clean install on my desktop. I manually installed restricted extras and the medibuntu-key.gpg first. If any package is duplicated it does not matter.

---

