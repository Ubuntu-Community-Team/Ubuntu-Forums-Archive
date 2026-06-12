---
title: "upgrade keeping /home"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by cryptozoologist on 2008-02-06
hi all,
when i was living in mandrakeland i recall fairly seamless upgrades by keeping my /home folder and wiping out the old install and replacing it with the newer version.  i just looked at both the gutsy and alternate gutsy install cds and i failed to find an option that allows me to do this.  i have done a little poking around and it seems likely that whan i was in mandrakeland i had a separate /home partition whereas on my current dapper install i used the recommended (by the installer) scheme that only uses a swap partition and one other partition for the rest.

i am trying to upgrade from dapper to gutsy and would like some recommendations for the best way to proceed that would allow me to (hopefully) keep my /home intact and upgrade with the least amount of grief.  thanks in advance!

peace
cryptozoologist

---

### Post by insane_alien on 2008-02-06
do you have a seperate home partition or did you just bung it all on the one?

if you do then you just install over but keep the partitions the same and tell the installer not to format the home partition.

normal upgrades done through update manager just require two clicks and you don't need to download a cd or anything.

---

### Post by cryptozoologist on 2008-02-06
i have just 2 partitions. swap and the rest.i investigated the update manager and it will update installed packages but not (as far as i can tell) upgrade to a new version.

i want to upgrade for several reasons:
my sound keeps failing which has an annoying work around to get it going again.
i want firefox 2.x instead if 1.5 which is possible to do in dapper but absurdly complicated.
i like the gutsy install i have on another one of my boxes.  i admit my reasons are shallow:i like the eye candy.

by the way, insane_alien managed to respond to my post before i was even able to navigate back to the forum to view it.  thank you for making my day a little more surreal.

peace
cryptozoologist

---

### Post by logos34 on 2008-02-06
You can[ transfer your /home to a separate partitio]("http://www.psychocats.net/ubuntu/separatehome")n, then do a fresh install of Gutsy, making sure to also specify /home mountpoint, but like insane_alien said do not format it. (uncheck box)

---

### Post by cryptozoologist on 2008-02-06
ok,
i am in the middle of following the instructions that logos34 linked to and after executing the line that "looks really complicated" ie
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
it appeared that several of the files gave a permission denied error.  these seemed to be the hidden files (the ones that start with a .) this is worrisome because these files contain all the configuration information i am trying to keep.  should i be worried?

peace
cryptozoologist

---

### Post by cryptozoologist on 2008-02-07
well it seems that several hidden files did not get transfered properly.  but fixing the problem was not difficult since the instructions include backing up your old home directories.  to save browser and email settings i only needed to:
log into the account that needed fixing (only 4 on this box)
open a file browser window for the user's home folder and the backup of the original home folder
make sure you can view hidden files
drag .mozilla and .thunderbird from the backup to the active home folder.
one user was using evolution which gave me fits but that is an issue with evolution that i have encountered before.

as an aside, i am going to warn folks away from evolution because it is a pain in the backside to move one's evolution from one computer to another and has been for a long time.  hey ximian, make migrating simple and robust without having to note down all configuration information and re enter it on the destination pc!  although not too arduous for a typical setup that only uses one pop (type) server and one smtp server, if a user checks 5 or 6 or more accounts, it is a drag collecting all the server info and passwords again.

this preserved browser and email but other desktop configuration info was lost.  although it could be restored moving the proper .whatever files over, since i am doing this to upgrade i'll worry about that stuff when i am living in gutsyland.

does anyone have a clue why permission errors would crop up when using a live cd?

peace
cryptozoologist

---

