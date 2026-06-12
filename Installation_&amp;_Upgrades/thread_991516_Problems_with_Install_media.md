---
title: "Problems with Install media?"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Rucas on 2008-11-23
Ok this is what i have come to think after a very bad experience running both Ubuntu 8.10 and Kubuntu. By the way this is not a rant, im simply explainning what exactly happened to me and what i think the issue really is.

My machine is a Toshiba Laptop 2.20GHZ, 500MegRam, Intel Celleron.
So i decided to install Ubuntu 8.10. Download the ISO image, burn the iso, and off we go.

1) The CD took over 2 hours to really install, it would hang and i had to wake the machine, press keys to get the cd to read again.
So i thouhgt ok my CD rom is going.

Anyways finnally get it in and its not good. Before the login shows up it takes very long, and the machine heats up within a matter of 10 seconds to some really worrying levels. I mean it really heats up. And this just by starting it up, no login window or any GUI in sight.
So i carry on trying to use Ubuntu 8.10 but its soo slow and the fans warmth are really worrying me. I came here to post and asked for help, many mentioned getting more ram, or better even try Kubuntu.

2) So Kubuntu 8.10 it is.
EXACTLY THE SAME PROBLEM...

So i started to think that this cannot be my machine, but maybe a problem with the actual install media. so i redownloaded both Ubuntu and Kubuntu 8.10 i386 32 bt version from a mirror close to me. Still same problem.

Now i decided that maybe that mirror had a buggy version or some problem, so i decided to again download the ISO from another location, but the same problem persists.

So now i have roled back to Ubuntu 8.04 (Hardy Heron) and all works fine again,  machine doesnt overheat like crazy, CD/Rom is working fine, and did the install perfectly, not hanging up or any issues at all.

My point to all this. Is it possible that the ISO file for the 32 bit versions is damaged or indeed someone made a mistake and its infact a 64bit version?

Can anyone please verify this? 
Regards

Also i read a lot off threads regarding individuals whom have had no problems with 8.10, are you running 64bit versions, or the 32bit?

---

### Post by Rucas on 2008-11-24
No one? Any ideas has to how this can be checked? Md5 check has reported errors for some, but if i understand correctly, MD5SUM is merely a security check, so you can be shure that yes it is Ubuntu you have and not some bad software.
I would really like to ear from other i386 32bit installers, if they had similar problems, etc...
Also i looked properly at the Minimum and recommended system requirements for both Ubuntu and Xubuntu 8.10, and my machine is fairly secure in the above requirements field.
So if this also happened with Xubuntu 8.10, then something is really wrong, thus my belief that the iso images are wrong, corrupt or something.
Cheers fellow users.

---

### Post by Partyboi2 on 2008-11-24
md5sums need to match to make sure that there are no corrupt files from the download process. So you should make sure they match.
I run the 32bit and have no problems.

---

### Post by Rucas on 2008-11-24
Ok, i understand that. But i have burnt 3 cd's with Ubuntu 8.10, all downloaded via Ubuntu's homepage (mirror's) and all 3 have the same problem.
Same goes for Xubuntu. So if it is the MD5 that is corrupt from download and everytime i have downloaded a fresh iso, what does that help?
Also how can i fix it then? Thanx for your reply.

---

### Post by Partyboi2 on 2008-11-24
If you have  downloaded the iso using a torrent  you should be able to start the torrent again and this should recheck the downloaded iso and download anything that might be missing. If you did not use a torrent to download the iso then maybe give it a go and try downloading from a different server. Before burning to disk check that the md5sum matches then burn at  x4 or less speed to avoid data corruption.

---

