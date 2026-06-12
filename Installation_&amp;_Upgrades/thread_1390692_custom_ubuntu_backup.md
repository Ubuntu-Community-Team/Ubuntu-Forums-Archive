---
title: "custom ubuntu backup?"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by skarychinezeguie on 2010-01-25
whenever i reinstall ubuntu, which i am about to do AGAIN, i have to spend many hours reinstalling apps and customizing my compiz, etc. Is there a way i can just make an image of my ubuntu system and just restore from the image? I'm tired of setting everything up.


***side note***:o
btw, the reason i am installing again is because i want to try the new virtualbox because they have made some improvements that allows windows to run seamlessly, much as parallels does for Mac OS X. but i made my ubuntu partition too small, so i am going to wipe again and this time use ubuntu as my only OS, and windows will be virtual. I just want to test how games run in the new virtualbox and if it performs like i think i'll just uninstall and go back to wine.

---

### Post by aysiu on 2010-01-27
What you want is Remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

It makes a custom live/installer CD of your Ubuntu installation.

---

### Post by skarychinezeguie on 2010-01-27
thanks. that looks much easier than the other tutorial i found earlier

[http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup)

i included a screenshot that shows some of the visible changes i've made. thanks again!

---

### Post by skarychinezeguie on 2010-01-27
got a question. only 1 so far. everything seems pretty straight forward except the part that says > Then copy the appropriate settings directories to the /etc/skel directory. . I found the home/username folder and the root/etc/skel folder, but what are the appropriate settings? from what i know about Mac OS X i'd guess any folder starting with a period is the preference folder. can i just copy all of them? or are there some files that i should NOT copy?

and just so i got it straight, the reason we're doing that is so that the root will have all of the settings there already, because Remastersys will not be copying the users. right? what about applications? are they already in the root?

also, can i make it store the image somewhere else? i only have a couple gigs left on my ubuntu partition.

---

### Post by aysiu on 2010-01-27
The applications are already in root, so you don't have to worry about that.

The settings are, as you suspected, the subfolders with the . in front of them in your /home/*username* folder.

I don't know if you should copy all of them. It's probably safer to copy just the ones you need. I think .gnome .gnome2 .gconf .gconf.d and .mozilla are good ones to start with.

---

### Post by skarychinezeguie on 2010-01-27
thanks a lot! i'm still new to linux and stuff but bein an apple tech support advisor i'm kinda familiar with how the OS is set up, but it is so much cooler than any other OS i've ever used.

i did think of another question BTW. Once i have my virtualbox windows all set up, will all that be copied too? because i plan to give my backup to some people who are interested in ubuntu, but they are also gonna want to use windows programs as well. I thought if i set it up for them it would help the transition. any idea how that might play out?

---

