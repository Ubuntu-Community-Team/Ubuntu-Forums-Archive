---
title: "Edgy to Feisty upgrade problems; multimedia files, etc."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by theblackcat on 2007-05-20
I am using a Dell D620 w/ Intel duo core processor.

I upgraded to Feisty from Edgy the other day - all was fine.  

Yesterday, I ran some software updates and now my computer will not play multimedia files.  XMMS, for example will open the FLAC or MP3 file from either a local folder or a SMB share on my home network but will not play the file.  The applications just hang...  I have had other random problems with applications, Firefox, etc. hanging.  The computer also seems to hang when I am removing programs from either Synaptic or Automatix.  I seem to be able to play multimedia files just fine when I boot to safe mode.

Please don't post with "reinstall clean Feisty" as I am trying to salvage my current computer.  However, if you know of a post or page that explains how to backup all of my configuration information and files so that I can reinstall with a clean Feisty that would be much appreciated.

---

### Post by starcraft.man on 2007-05-20
Ok, this is a simple task, what you will want to do is create a separate partition to copy your home directory (it holds most of your user data and preferences. Follow this [guide]("http://www.psychocats.net/ubuntu/separatehome") for that (I assume ya don't have one already).

Once you make and copy the home folder, you can reinstall with all your files saved, and create a root and swap file as always, make sure that home is actually mounted as your home folder and all should go well. Then you can install all your program again and they should see the already existing folders. I think that covers it :).

Wish ya all the best, one day Ubuntu will have a full-proof upgrade path :).

---

### Post by theblackcat on 2007-05-29
Outstanding!  Worked like a charm and just what I needed. 

Thank you!:p

---

