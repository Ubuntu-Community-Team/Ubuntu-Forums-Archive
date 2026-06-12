---
title: "Can not see the files/folders at windows side"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by PeaceOcean on 2011-04-25
I installed Ubuntu 10.04 a few days ago. I partitioned the single Hard drive using the ubuntu installation CD. In detail, set up windows 7 (64 bit) side as a primary partition. I then created a extended partition and divided it into 3 logical partitions, swap, /, and /home. I recall when doing installations, I went through a step asking me to map some windows 7 side folders. I then picked up all of them. After the installation, I received a warning message. it says the /home folder was almost full. I looked into it and found it was mainly occupied by files from a folder at window 7 side. I had to delete the all those files and freed up /home (when logging into window 7 side, I found those files and the folder are intact). so far, everything works fine with the ubuntu system. And I can a few empty folders such as music, videos, and pictures inside /home. I think they are the windows side folders I picked up during the installations. however, they are all empty. other than that, I can not see any file/folder from windows side. I was told after the 10.04 installation. I should have seen the windows side. I don't know what is wrong with my installation. Could anyone give me some help?

thanks in advance!

---

### Post by Mark Phelps on 2011-04-26
You see the files in the Windows "side" by going to Places and clicking on the disk icon representing your Windows partition.

That will open Nautilus and show the folder.

If you're doing that and the folder is empty, you have a different problem.

You're not trying to share /home between Ubuntu and Windows are you? If so, that is a BAD idea -- as the two file systems use very different permissions and each one will corrupt the other.

---

### Post by PeaceOcean on 2011-04-26
thanks a lot! I am actually a newbie with Ubuntu. I got it work.

---

