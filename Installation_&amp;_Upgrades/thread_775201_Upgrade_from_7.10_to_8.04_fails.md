---
title: "Upgrade from 7.10 to 8.04 fails"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ishkabibble on 2008-04-29
I have 7.10 (Gutsy Gibbon) installed.  I go to update manager and am informed that 8.04 (Hardy Heron) is available.  I click upgrade, it says "Downloading two files" finishes and... nothing.  Still have 7.10.  Anyone heard of any problems with the upgrade process?  It's the first time I've tried an upgrade anyway, so I may be just totally naive, but then again I don't want to bang my head against a wall someone else has broken already.

---

### Post by bullfrog2 on 2008-04-29
did you do a update first if not thats proable your trouble hope it helps bullfrog2

---

### Post by ishkabibble on 2008-04-30
Yes, I did before, but now it has errors.  Where do I find the error log to post it?

---

### Post by Partyboi2 on 2008-05-01
If you are looking for the distro upgrade logs they can be found in /var/log/dist-upgrade.

---

### Post by ubunny on 2008-05-01
my upgrade fails as well

what i do:
sudo apt-get update
sudo apt-get upgrade

until I don't have any files left to change.  Then I run

update-manager -d

New Distribution release 8.04 LTS is available (Upgrade)
i click upgrade
Downloading the upgrade tools (2 files)
sudo login screen
Preparing To Upgrade (runs the files, timebars zig, then it hangs)

I check the hardy tmp program in htop, and it's stalls with zero cpu activity with exactly 11.7% of memory each time on 512mb (503 avail so around 59mb)  

A few months ago I upgraded this machine four consecutive times from 5.10 and up (all i had was the 5.10 cd, then network installs).  Certainly the later upgrades have been getting easier and easier.

a couple of days ago there was an update for update-manager so I wonder if this was missing something?

any tips are gold
thanks

---

### Post by acl123 on 2008-05-01
I found the servers were extraordinarily busy when I was trying to upgrade - they could still be very busy.

You can change the server you are getting it from though:
[http://tombuntu.com/index.php/2007/09/04/automatically-find-the-fastest-repository-in-synaptic/](http://tombuntu.com/index.php/2007/09/04/automatically-find-the-fastest-repository-in-synaptic/)

By the way, I wouldn't recommend upgrading at this stage, unless you have a backup of your system and are prepared for the possibilities of serious stability problems in Hardy.

---

### Post by ubunny on 2008-05-01
yes I agree it seems that way.  I'm happy with gutsy for now.

I'll just put a note that for those who have done a backup, if you don't like the gui managers you just:

edit /etc/apt/sources.list and global replace gutsy with hardy
run
apt-get update
apt-get dist-upgrade

this process has worked most of the time between versions.  I'll wait a bit more I think ;)

---

### Post by agerbo on 2008-05-01
I followes the instructions and the upgrading went fine.

But when I wanted to do something as root, I got a message like unable to find host. I had to go to  from the menu: System > Administration >
Network > Hosts. Here I read mshome after my laptop name. I deleted that and now I can log in with sudo

My sound was wrong. But it helped with:
sudo /etc/init.d/alsa-utils reset
I found it there:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213206](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213206)

---

### Post by bhavin66 on 2008-05-02
I upgraded just to be safe of any horror stories.

I used the instructions provided
[http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

It took me about 4 hours as it had to dowload about 840mb (1160 files as it said) on my basic DSL.

Asked me some question along the way to keep my printer setup and samba setup. For safety and laziness i said keep the old configuration and do not upgrade.

Everything went fine !!!!!

Now i am on 8.04 and everything seems to be working fine.

---

