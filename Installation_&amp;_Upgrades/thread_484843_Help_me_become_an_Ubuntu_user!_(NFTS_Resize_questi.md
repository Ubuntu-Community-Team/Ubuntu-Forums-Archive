---
title: "Help me become an Ubuntu user! (NFTS Resize question)"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Dolfhin01 on 2007-06-26
Hey guys :D

Situation is simple, I would love to use Beryl, I would absolutely love to mount a FTP server as a network share without headaches and I'm dying to play Age of Kings again (which works fine under Wine but has some serious problems with Vista).

So, what is the problem?

Well, I downloaded Wubi and tried it, it failed which sucks. No problem I downloaded GParted and tried to re size my partition to install it normally, it couldn't do that (might be because NFTS compression is enabled?). No problem I'll just use a windows based partition program, right? Doesn't work because my C drive is in use. So I tried the built-in windows application and it gives me 0 (zero) MB available to re size! Fun...

Does anyone know of a way to re size my NFTS Partition? I do not have the available storage to backup my work and school files and music/movies so that is out of the question. I also would strongly prefer not to loose my Vista installation. 

Thanks in advance!

edit :

These two posts deal with the problems I had with Wubi, the might be of some help :

[http://ubuntuforums.org/showthread.php?t=438858](http://ubuntuforums.org/showthread.php?t=438858)
[http://ubuntuforums.org/showthread.php?t=438858](http://ubuntuforums.org/showthread.php?t=438858)

edit again :

NFTS compression doesn't seem to be a problem. I'm out of ideas :

[https://answers.launchpad.net/ubuntu/+question/3093](https://answers.launchpad.net/ubuntu/+question/3093)

---

### Post by Metacarpal on 2007-06-26
Have you run defragment on your hard drive lately?
(In Windows, open My Computer.  Right-click the drive, choose Properties.  Under the Tools tab, you'll find defragment)

I highly recommend you do this before any attempt to re-partition your drive, or you could lose data or system-critical files.  For that matter, you should perform a full backup of your drive whether you defragment or not!!

Ooh - and you should start Windows in Safe Mode to run defrag.  If anything (like screen saver, antivirus, virtual memory, etc) is writing to the drive when defrag is running, it'll keep restarting over and over, then fail.

---

### Post by nyvalbanat on 2007-06-26
As Metacarpal mentioned, you should check for errors and defragment the windows partition before resizing. After doing that, I booted into Feisty off the CD and used gparted  to resize the windows partition without any problems.

Since you mentioned setting up an ftp server, consider using ssh instead for better security (sftp, psftp.exe - that sort of stuff).

---

### Post by Dolfhin01 on 2007-06-27
Ah, thanks guys :P I'll try and do the defragmenting (in safe mode!) overnight and then do the file checking first thing in the morning.

Just for other vista users that find this thread, a word of warning :

[https://bugs.launchpad.net/ubuntu/+source/linux-ntfs/+bug/94690](https://bugs.launchpad.net/ubuntu/+source/linux-ntfs/+bug/94690)
[http://lists.alioth.debian.org/pipermail/parted-maintainers/2007-January/001008.html](http://lists.alioth.debian.org/pipermail/parted-maintainers/2007-January/001008.html)

Proper way to resize :

[http://gparted-forum.surf4.info/viewtopic.php?pid=3053](http://gparted-forum.surf4.info/viewtopic.php?pid=3053)

---

