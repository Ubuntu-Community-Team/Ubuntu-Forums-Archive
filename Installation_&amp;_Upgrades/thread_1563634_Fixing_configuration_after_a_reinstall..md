---
title: "Fixing configuration after a reinstall."
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by t0mppa on 2010-08-29
First off, apologies if this is a commonly known problem, but I couldn't really find anything too useful by doing a search, possibly because of not really knowing what keywords would best describe the problem.

The thing is, I finally had time a few weeks ago to update from 9.10 to 10.04 (Desktop version) and figured I'd do it properly this time and reformat my / and /boot partitions, while leaving /home untouched. The install itself went mostly without trouble only for me to realize that I had forgotten about trying out encrypting my /home directory earlier and now couldn't even boot the computer as it was encrypted and the OS refused to load up.

So, I had to sneak around from a liveCD to chroot into the filesystem and copy the contents away from the .Private folder (after unencrypting them, where the official tools had a few nice bugs). After that I chmod'ed (to 755) and chown'ed all the files to my new user and figured that'd do the trick. Author for all of them is root, but I can easily access them with my main user now.

Problem is, none of my settings are being saved, if I change something, it goes back to the old state the next time I boot my machine and my browsers are complaining about not being able to open up profile properly.

Thus I was wondering what is it that I need to do now, to get full functionality back? Just delete all the .[something] directories from /home/[user_name], have the OS recreate them and tweak all the settings again from the ground up or is there an easier route, that lets me keep my current configuration and enable the system to actually save all made changes?

---

