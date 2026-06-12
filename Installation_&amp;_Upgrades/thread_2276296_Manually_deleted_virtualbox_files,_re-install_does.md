---
title: "Manually deleted virtualbox files, re-install doesn't restore"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by Joe_Lyman on 2015-05-01
Upgraded to 15.04 the other day, and VirtualBox wasn't working. No problem, I figured I'd remove it and re-install. So, I used apt-get remove.... but then I got cute and said to myself "I'll remove all the virtualbox files I can find, just to have a really clean re-install."

So, using locate I manually found and annihilated every last virtualbox file on my system.

Upon re-install with apt-get, I noticed that /etc/init.d/vboxdrv was missing. Odd, I figured everything would be re-installed. Then I noticed LOTS of virtualbox related files were missing. The entire /usr/lib/virtualbox/src folder, for example. I tried apt-getting pretty much every virtualbox package I could find. No dice.

My questions are: 1) why in the world aren't ALL files that Virtualbox depends on installed with Virtualbox; and, 2) What is the best way to go about fixing what I messed up?

Thanks for any help you can provide.

---

### Post by ajgreeny on 2015-05-01
Did you install the working version from the repos or direct from Oracle, which has a later version of VBox (for 14.04) than is in the repos.

I hope you did not also remove all the VBox OSs that were probably sitting in your home in a folder called **VirtualBox VMs**

---

### Post by Joe_Lyman on 2015-05-01
I have worked only with the repo versions. I believe I've installed the extensions from Oracle's website in the past, but never the application.

Luckily, I didn't remove anything that was specific to my user... all of my VMs are on a different hard drive.

---

### Post by Joe_Lyman on 2015-05-01
Ok, for now I installed the version of VirtualBox (all distributions) directly from Oracle, rather than from apt-get. It is working perfectly. I suppose I could probably copy the files out of /opt (where it installed) into the various locations in my filesystem and re-try the repo, but I'm curious if there is any other more "correct" way of fixing this kind of issue. I suppose it can't be unheard of for someone to carelessly remove package files from the filesystem? Since they're not part of the distro itself (they were added), should there be a way to re-install them??

---

