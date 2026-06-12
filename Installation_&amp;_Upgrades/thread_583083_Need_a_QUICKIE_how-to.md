---
title: "Need a QUICKIE how-to"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Hoppiesbox on 2007-10-20
Like many others I've had an issue with the upgrade from Fiesty to Gutsy (my fault I'm sure) and am considering a fresh install (I had too many un-needed packages anyway).

I'm TERRIFIED about losing all my configuration with gnucash, firefox, etc.

I won't even speculate - but how can I restore as much of my old setup/configuration/preferences to a new install?

A long-time windows user (never again) I'm quite used to losing all my stuff and having to re-format/re-install. I know Linux isn't going to do me wrong like that...but how exactly, what exactly needs to be backed up?

Thanks, this could really help quite a few people out there I think - so thanks for answering you expertly answering folks!

P.S. you can see my posted problem here if you are extra expertly:
[http://ubuntuforums.org/showthread.php?t=582616](http://ubuntuforums.org/showthread.php?t=582616)

---

### Post by litemotiv on 2007-10-20
do you have your home directory on a separate partition? in that case, you can just reinstall your system partition / and all the configuration settings from /home/yourname will be kept for your new installation. 

if you don't have a separate home partition, you can backup/copy everything under /home/yourname (or at least the directories whose settings you want to preserve), and copy it back once your installation is done. in that case, i would really advise to reinstall with a separate partition for /home so you can avoid having this problem again in the future.

good luck ;)

---

### Post by Pumalite on 2007-10-20
You need to save /home, including 'Hidden Files', and data. If you have /home in a separate partition; better. You can use it in a clean install, just don't format it.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Hoppiesbox on 2007-10-22
Thanks for the advice guys - I finally did resize the partition using a liveCD and installed gutsy from the alternate gutsy .iso, That worked out pretty ok. All my stuff is pretty busted, simply replacing everything in the new home with the contents of the old home, just using rsync  made big problems for me. nautilus refuses to start, and spams out a huge log file...My wife's worked out better - I only added her Desktop folder and .mozilla

Thanks again for your adivice! [SOLVED!]

---

