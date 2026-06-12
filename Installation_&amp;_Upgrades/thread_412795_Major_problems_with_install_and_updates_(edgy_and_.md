---
title: "Major problems with install and updates (edgy and feisty) - mirrors corrupted?"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by gsyoungblood on 2007-04-18
I just finished a fresh install of edgy from CD, followed by several updates. Then I tried to upgrade to feisty, as well as install xemacs (edgy universe) followed by regular emacs. In every case I end up battling problems that result in the command being aborted.

Even changing the sources.list to use different mirrors does not help. Apt-get update frequently fails.

First, using the defaults sources.list (which for me points to us.archive.ubuntu.com), apt-get update frequently fails with the following error:
[INDENT][I]bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
  Sub-process bzip2 returned an error code (2)
Fetched 3559kB in 19s (179kB/s)                                                
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)[/I][/INDENT]

There is more than one file that triggers this error. Using wget to retrieve one of the failed files manually, and then running bzip2 to decompress or test confirms the file has a problem. bzip2 -t reports:
[INDENT]*bzip2: Packages.bz2: data integrity (CRC) error in data*[/INDENT]

Next I tried installing xemacs21 from universe, and the emacs21 from main. Both failed due to md5sum errors. Here's the error from the emacs21 attempt:
[INDENT][I]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacs21/emacs21-common_21.4a-6ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacs21/emacs21-common_21.4a-6ubuntu2_all.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacs21/emacs21_21.4a-6ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacs21/emacs21_21.4a-6ubuntu2_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I][/INDENT]

Running apt-get update as instructed, with fix missing, didn't appear to make any changes. Rerunning the emacs21 returns the same error.

I have tried us.archive.ubuntu.org and the mirrors at kernel.org, utah.edu, gatech.edu, and easynews.com. All return the same errors. I started this last night, stopped for about 10 hours in case mirror sites needed to refreshed, all to no avail.

I had dabbled with ubuntu in the past. This was the first time I installed it and planned to use it as a daily work environment. I don't recall ever having these kinds of problems. 

Any ideas or suggestions on fixing this? Judging by some of the scattered comments, this appears to have been an intermittent or ongoing problem for at least a couple of months, but none of the threads I read so far seemed to have any real solutions. Is this kind of problem normal? Is there some kind of corruption messing up install source and mirrors? Is it a local configuration issue? 

I welcome any suggestions on resolving this.

Thanks

---

### Post by old_geekster on 2007-04-18
Try using the following command to do your upgrade:

sudo update-manager -c -d

I have used this twice and it worked perfectly.

---

### Post by gsyoungblood on 2007-04-18
I was using update manager. And also apt-get.

I think it might be something more unusual. I have a Thinkpad T43p laptop. If I use the ethernet port, I have the problems. If I connect using wireless, everything worked.

The "aha" moment came when I started getting corrupt MAC errors on SSH connections. and I started to suspect something software. I knew the hardware (and network) were OK, as other machines work correctly, and the laptop worked correctly with XP and other distros.

I've since upgraded to feisty (via wireless) with no problems. However, the problem with the ethernet port persists.

---

### Post by gsyoungblood on 2007-04-18
the problem was not fixed by switching to wireless. 

I ran the following command three times:
[http://mirrors.easynews.com/linux/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.38-0ubuntu1_i386.deb](http://mirrors.easynews.com/linux/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.38-0ubuntu1_i386.deb)

As well as pulling the same file from us.archive.ubuntu.com and [www.gtlib.gatech.edu](www.gtlib.gatech.edu).

Below is what md5sum reported for each of the files.

7669ca6a2c84a5431034ef8e8e8c92d9  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb
613baaf4d093e8170cdac0728dc46a48  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb.1
3ee6ce72962a0e4f88d82501b80453fe  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb.2
40288d7ded7e9452c538f373daefd18e  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb.3
758143843e6132210a1446077f8c0c3a  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb.4
2f84f49675759ddb5c85610f07040933  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb.5
d0e48f359a489b9297df338b6e2fbbb5  mysql-server-5.0_5.0.38-0ubuntu1_i386.deb.6

File 6 was retrieved using the same command above, except on a different (non ubuntu) computer (on the same network, using the same router/ISP/etc as the Ubuntu laptop) and then SCP to the Ubuntu box. This file survived the scp copy process and has the correct md5sum.

I don't know if the problem is networking, or isolated to wget or something special about wget. I should point out this problem was affecting me on both 6.10 and 7.04.

---

### Post by gsyoungblood on 2007-04-18
Message posted to networking forum: [http://ubuntuforums.org/showthread.php?p=2478501#post2478501](http://ubuntuforums.org/showthread.php?p=2478501#post2478501)

---

### Post by gsyoungblood on 2007-04-19
Problem is networking related, additional details posted to: [http://ubuntuforums.org/showpost.php?p=2485129&postcount=3](http://ubuntuforums.org/showpost.php?p=2485129&postcount=3)

Summary: something seems to be wrong with ubuntu (6.10 and 7.04) network stack that affects larger data transfers over fast connections. using a slower connection increased the odds of succesful transfers. Problem is on both wired and wireless interfaces. Problem does not exist with Windows using same hardware and same network. Computer is IBM Thinkpad T43p w/broadcom NIC and intel 2200bg wireless.

---

### Post by JoshRoss on 2007-04-21
I am having the same problems, I also get corruption, of HTTP downloads, on my MacBookPro.  Try using the FTP servers to get your updates.  It worked for me.

Is your ISP WideOpenWest?

---

### Post by gsyoungblood on 2007-04-22
I was able to get a second (identical to the first) laptop from the office. It's looking more and more like there is some kind of hardware problem with the laptop that was having this problem. For whatever reason, Ubuntu (and Windows) worked well enough to make it seem like the hardware was working fine and there was a software problem. Yet, as far as obvious problems, Windows seemed to work just fine, and only Ubuntu was having problems.

I tried FTP. I also tried NFS. If it came over the network (wired or wireless) it would have a problem with corruption. 

The replacement laptop does not have this problem. Feisty is working just fine and is able to install from remote repositories with zero problems.

---

### Post by unibuntu on 2007-04-25
I have just upgraded from Edgy wich worked just fine and and now I have exactly the same problem in Feisty: MD5Sum mismatch on all and sundry updates...
No such problem in my windows boot no such problem in Edgy just with Feisty!

Also I have the same corrupted browser pages some time that someone else mentioned in this forum since the upgrade to Feisty

Any suggestions would be welcome

HW:
Abit AW-9Pro, Core2Dua 2.4
1GB Ram ATI 1650Pro
2 Monitors

Help me please....[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

