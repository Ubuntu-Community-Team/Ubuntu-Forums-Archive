---
title: "Great to be Back!! - Install issue? Root out of HD space!"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by garpt01 on 2011-08-04
Hello all,
  Its been a couple of years (about three) since I last had a great time with Linux on an old laptop- whatever version of Ubuntu was around then. I am now using it on myu desktop "supercomputer" with 4ghz AMD quad core, dual Radeon cards in crossfire, bluray, three 1TB storage drives, 8GB ram, 28" Samsung monitor etc.....Linux has come a LONG way!~ I can definitely see myself replacing Windows 7 Ultimate before long with the latest distro (I think), 11.04. Multimedia is catching up fast! Plus better security, more streamlined, etc. Anyway, this post isn't about my hardware or a rant about Windows, it's about an issue I am having because the hardest thing I am having problems grasping with Linux is file/ folder management after using Windows at work and home for many years. I have searched and tried several solutions to no avail. Remembering this is the best forum out there for Linux, I really need some help and hopefully answers. Now..........The specifics.
 I am using a totally separate 1TB H/D just for Linux, I have Windows 7 on a separate disk in a dual boot setup. 11.04 installed off a CD download onto the empty drive. I started having issues a few days after install. My "root" (I guess also known as home?) usage is at 100%  and I am getting the warning that I am low on disk space. I am using NTFS file system and have well over 900GB free. I do have many files- music, pics, videos, docs, etc. which I copied from my third (backup) hard drive directly to the appropriately named folders ( Music, Pictures, Video, etc.)  I have only been successful copying the music folder (about 3GB) before I get the warning on start up. I am showing only about 2.5GB free in the other media folders. My pics and video folders are larger than that. I am recently out of work so I have spent about 8 hours a day for the last week or so customizing Ubuntu to the point where I really don't want to lose it and do a fresh install, so I am looking for solutions. Obviously space is not an issue. The drive I am using USED to use Windows XP as a backup O.S., but I removed it---although I did NOT reformat, as I just tried installing Linux on a whim then kinda fell in love with it. Is there ANYTHING I can do to fatten uo these folders, especially the root, so that I don't need to reinstall? I know file management is much stricter than what I am used to, but I still think this is a solvable issue. :confused:

  Sorry for the long post- just wanted to reintroduce myself and get back into the community. Fortunately- (or unfortunately depending on how one looks at it) I can't make a phone call to India or China or someone who doesn't have a clue about computers but reads prepared texts to "walk you through" things that you KNOW have nothing to do with your issue. ](*,)
  That's why I'm here. Thanks in advance for your support and assistance!=D>

-Gary

P.S.- I had like three beans before I left the forum back when, but forgot my logon-- so I start anew, fresh at one bean, one post.

---

### Post by dino99 on 2011-08-04
Hello Gary, and welcome back :)

what a long post, blah, blah, blah ...
what nobody can do for you is to define your needs; so clear your mind first: all is about logic.

A standard installation is like:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by oldfred on 2011-08-06
With the new very large hard drives space is not an issue, but organizing it is.

I prefer small system or / (root) partitions and separate data partitions. For new users I just suggest a separate /home as that is relatively easy to set up and moves data, but still has user settings in /home hidden files & folders which are still part of the system. 
For more advanced users I then suggest a separate /data partition with all the normal data folders like Music, Documents etc and maybe a few others that are hidden folders with lots of data in /home like my Firefox profile & Kmymoney files. But then the user settings are still in the / partition and hard drive does not have to search over 1TB of space for often used system/user files.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

---

### Post by jmszr on 2011-08-06
garpt01,

To clear out _some_ space in your root (/) partition here are two things you can do (1):

In the terminal (Applications > Accessories > Terminal) run:

```
sudo apt-get clean
```

and (2): open the Synaptic Package Manager and in the search box type "ttf" (no quotation marks), click on "Search", and then scroll down through the language packs (ttf-), removing all that aren't applicable to you (some of them use a lot of space). 

Hope that helps

---

### Post by garpt01 on 2011-08-06
Deae JMSZR and Old Fred,
 Thank you both so much for your helpful and thorough responses..I was gonna give up on this forum after the curt response from Dino99 that made me feel rather foolish. After following (or trying to) his too broef instructions, I was left with a totally hosed hard drive and a destroyed MBR. That's of course not his fault- but my assuming that according to him and his "blah blah", etc, that all I lacked was logic and common sense made me attempt a repair I should not have attempted without more instruction. I guess we all can't be as bright as him when it comes to Linux. 
 But now that I have reformatted my drive and repaired the MBR, I will follow your detailed advices.
  Thank you both again for your assistance and renewed faith in the community!

---

### Post by jmszr on 2011-08-06
garpt01,

Glad you decided to stay. Now that you have the opportunity for a fresh install you can set it up so you won't run into any problems. I suggest you use 20GB for your root (/) partition - I use 15GB and that's getting pretty full. Also, a separate /home partition is highly recommended - it simplifies upgrading or if for any reason you have to reinstall. 

It looks like "oldfred" has you covered as far as documentation, but if you have any questions, just ask - somebody on the forums is bound to have the answer.

Edit: D'oh! You need to use ext3 or ext4 for the file system. Linux is incompatible with ntfs -"> With ntfs-3g, linux can read and write NTFS, but since the concept of UID-user assignments stored in registry is alien to linux, it won't be able to handle permissions."  I was rereading your post when I noticed that - better late than never I suppose.

---

