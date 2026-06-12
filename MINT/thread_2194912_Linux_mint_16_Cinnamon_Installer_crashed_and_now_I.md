---
title: "Linux mint 16 Cinnamon Installer crashed and now I can't even get the boot loader"
date: 2013-12-21
forum: MINT
---

### Post by silvercats on 2013-12-21
I do not get the boot loader to go to the Windows at atleast. All I get is this CLI of Linux. No option to select OSs. When I was installing it said "installer crasshed, send a bug report blah ....". I had Ubuntu on that partition before.

---

### Post by d-cosner on 2013-12-21
It might be possible to start over. You could try updating the installer from the live session and install again. I do not duel boot but I still wanted to try and help you out.

---

### Post by silvercats on 2013-12-22
I tried several times. Is there any safe way to install Linux mint when there is win 8, without touching win8 partition?

---

### Post by Karlchen on 2013-12-22
Hello, silvercats.

Have you read the Linux Mint release notes for Mint 16 Cinnamon and Windows 8 UEFI boot? [Release Notes for Linux Mint 16 Cinnamon]("http://www.linuxmint.com/rel_petra_cinnamon.php") Go down to the section titled "EFI support".
Have you tried searching the Linux Mint forums for information on your problem?
Have you tried asking for help on the Linux Mint forum? Might be the most obvious approach to do so. :wink:

Oh, and the question which should have been asked in the first place: Have you verified the MD5 checksum of the ISO download file before starting to use it for installing? ([Linux Mint 16 "Petra" - Cinnamon (32-bit)]("http://www.linuxmint.com/edition.php?id=143") - [Linux Mint 16 "Petra" - Cinnamon (64-bit)]("http://www.linuxmint.com/edition.php?id=144"))

About your question: > Is there any safe way to install Linux mint when there is win 8, without touching win8 partition? The answer clearly depends. It depends on the question whether there is enough unallocated disk space available or whether the whole harddisk has been occupied by Windows partitions. Which sadly and stupidly is the default situation on machines that come with Windows pre-installed.
Provided, however, there is enough unallocated disk space available, then the answer will be: Well, yes, it should be feasible.

Apart from this general statement, sorry, personally I cannot give any piece of advice on installing Linux Mint 16 alongside Windows 8.x from my own experience, because I am convinced that tiles should be found on bathroom walls, but not on flatscreen monitors. :rolleyes:
[SIZE=1](This is the reason why on the machine where I am typing this reply, there is Windows 7 x64, Precise Pangolin x64, Linux Mint 13 x64 and a free disk partition for another Linux distribution, the name of which has not been decided on, yet.)
[/SIZE]
Having said so, I would like to point you to a tutorials and to an artiicle on how to install Linux Mint alongside Windows 8. Though the video tutorial is about Mint 15, the same steps apply to Mint 16 as well.
+ [Install Linux Mint 15 Olivia Alongside Windows 8 by AvoidErrors](http://www.youtube.com/watch?v=1SwUgRtcrdk)
+ [Dualboot Ubuntu or Linux Mint with Windows 8 UEFI](http://alllinuxstuff.blogspot.de/2013/07/dualboot-ubuntu-or-linux-mint-with.html)
Please, remember the best tutorial or article won't help in case the downloaded ISO image is bad. So take the time to verify the MD5 checksum.

Kind regards,
Karl

---

### Post by silvercats on 2013-12-22
Thanks fro trying to help. The tutorials are kind of irrelevant as they generally show how to install Linux mint with win. Somehow I managed to fix the issue by deleting the partition and then dividing that partition again in to two parts, one for "root" and one for "home". I also changed the location of GRUB loader (to the main drive) and then all went OK without messing with those EFI stuff. thanks!

---

### Post by Karlchen on 2013-12-28
Hello, silvercats.

Great you have solved the problem on your own. :-)
The assumption [the tutorial](http://www.youtube.com/watch?v=1SwUgRtcrdk) were about a Mint4win installation is incorrect by the way. The tutorial only starts on Windows in order to get the Linux Mint installation ISO image file. Then he boots to the Linux Mint live system and performs a normal installation.

Cheers,
Karl

---

