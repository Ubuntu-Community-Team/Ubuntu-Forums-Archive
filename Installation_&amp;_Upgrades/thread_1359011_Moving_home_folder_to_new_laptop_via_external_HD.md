---
title: "Moving /home folder to new laptop via external HD"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by mrmagpie on 2009-12-19
Hello,

I'll be receiving a new laptop for Christmas (and thank god for that, because the one I have now is nearly 7 years old and very much on its last legs). I was informed by a friend that it would be possible for me to move my entire /home folder from this old laptop to my new installation of Ubuntu on my new laptop, provided the versions of Ubuntu (8.10) and my user names are the same, via my external harddrive.

He gave me the impression that simply copying the entire folder to my external HD was all that needed to be done, and then the /home folder could be moved to the new HD, and the /home folder already there could be deleted, and things would sort of...work themselves out. Is this true? Exactly what would I be saving and what would I not be saving if I were to do this? For instance, what about programs such as wicd and Wine? Are those really all part of the /home folder - in other words, I wouldn't need to re-install any of my old settings?

I've read a bit on the Ubuntu forums on questions having to do with the /home folder, but generally it concerns people looking to make separate partitions for their /home folder and things of that nature, which isn't what I'm after at all. Any feedback anyone could give me on this would be greatly appreciated.

---

### Post by vanadium on 2009-12-19
It should be 100% reliable to copy over your home directory and find your settings back, if you install exactly the same Ubuntu, and have the same username and user id.

In backing up your /home, you must be sure to copy any ownerships, permissions and links as well. You can use rsync for that, provided your destination drive is formatted with a linux file system.

rsync -av /home/$USER  /media/<yourdrive>/home/$USER

You will not be able to copy the ~/.gvfs directory: that is normal and is not a problem.

You may also need to reinstall some applications that you used, but were not installed by default. These will automatically take over your old settings that are already there.

Alternatively, you could tar your /home, which would result in a big archive that you then can store on any file system that supports large files (for example, vfat only supports up to 4 GB).

---

### Post by unmole on 2009-12-19
These should help you out
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Ofcourse you will have to adapt them to move from one system to another.

---

### Post by mrmagpie on 2009-12-19
-deleted-

---

### Post by mrmagpie on 2009-12-20
Thankyou for the responses!

The problem with using rsync to backup my current /home folder on my external HD before transferring it to my new laptop is that I already have Ubuntu 8.04 installed on my external HD, as I had to use it as my primary HD for a period of time while I was in Japan. It seems that if I used rsync, it would essentially correct any differences in content between my current /home folder and the one on my external HD? Which would be completely counter-productive, as I've been using that external HD to, well, store movies and books and so on. Am I misunderstanding how this process would work, or what it would do?

---

