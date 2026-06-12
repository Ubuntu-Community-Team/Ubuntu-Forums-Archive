---
title: "Debootstrap error during installation"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by Zdravko on 2006-03-03
Hi,
I am trying to install Ubuntu Breezy Badger 5.10 on my computer, while having already WinXP on it.
C:WIN(NTFS)
E:DATA(NTFS)
left ~28GB
The other free space is left unpartitioned. So, with the partition manager in the Ubuntu installation I managed it so:
logic, 10GB, ext3, /
logic, 16GB,, ext3, /home
logic, 2GB, swap
Then the installation starts, and after a while a message appears:
"Base system installation error, The debootstrap program exited with an error (return value 1). Check /target /var/log/bootstrap.log for the details."
Now I am unable to have the installation completed successfully. Please, help me :(

Edit: It appears that the CD was not correctly written. I chose a CD-Verification and the result was obvios: "./pool/main/x/xfsprogs/xfsprogs_2.6.28-1_i386.deb failed the MD5cheksum verification". I am very dissapointed from Ubuntu, because the CD was ordered from Ship-It! After Dapper Drake emerges I will order 5 CDs and test them. Now I think to give Ubuntu second chance :) I am downloading it via a torrent, maybe I have to burn the ISO at a lower speed just for sure?

---

### Post by Herman on 2006-03-03
[http://www.ubuntuforums.org/showthread.php?t=132424&highlight=debootstrap+program+exited+error](http://www.ubuntuforums.org/showthread.php?t=132424&highlight=debootstrap+program+exited+error)
It looks like we're not too sure about that one judging by the above link it could be several different possible causes and cures.
I have never had this same problem  myself, so I cannot say anything for sure. Try out some of the solutions in the link above and I hope one of them will work for you, good luck, Zdravco, from Herman. :-D 

Oh, I see you have added an edit to your post. Good, it's just the CD that is faulty. Shipit CDs are free, but some are not the best, that happened to me once too. I had ten for free so I just used another. Downloading from the internet and burning slowly should work. Good.

---

### Post by Zdravko on 2006-03-03
Herman, thank you for the link. When I changed the language, the installation reached farther. But this time the error was connected with the initrd-tools package. Anyway I wil try with a new cd. :)

---

