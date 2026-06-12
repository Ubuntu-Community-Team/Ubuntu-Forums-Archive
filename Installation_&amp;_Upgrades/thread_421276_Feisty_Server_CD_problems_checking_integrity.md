---
title: "Feisty Server CD problems checking integrity"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Eladon on 2007-04-24
Well, I've found lots of posts with people having various problems with CD's.  Haven't found one quite like my situation, but maybe they're all related to the same problem???

Anyhow, the short version is that there is something unique about the Feisty server CD that is causing it to fail it's integrity check on my Dell PowerEdge 2500 server.  Specifically, it hangs at 0% checking "./dists/feisty/main/binary-i386/Packages"

The long story is that I have downloaded iso copies of Feisty server from both distribution sites and bittorrent.  All of my downloads pass the md5sum test.  I have two desktops and one laptop, all with DVD burners.  I have burned copies of these ISO's from each computer using 2X or slower onto two different brands of CD media, and also DVD media.  All copies can be booted from and pass their integrity test on my desktops and laptop, and without exception all copies fail as described above on the server.  I tried installing from it anyways, but predictably the install failed.

Also, I have burned copies of Dapper and Edgy which both verify and work fine in the server.  And if I boot the server I can read the files on the Feisty CD without issues.  I have not, and am not having problems reading any other CD's from my server.  However, just in case I even tried swapping the CD module out for another, but this had no impact.  Also, all bios updates to the server were already up to date some time ago.  

So bottom line is,my hardware seems to be fine, and yet there must be something in my hardware that is triggering the Feisty server CD to have issues.  

Any suggestions?

---

### Post by c0d4041292 on 2007-06-14
same problem  any help

---

### Post by debby_k on 2007-07-03
I have the same problem on an IBM Thinkpad R32.  Any solution?

---

### Post by MCapito on 2007-07-05
I'm having the same problem getting Feisty's server build to pass the integrity check on the Poweredge.  It passes on other machines, and I've tried multiple disks on multiple Poweredges... Any ideas?

mC

---

### Post by jd3010 on 2008-05-05
Hi all,

had the same problem, but got it solved by installing 6.10 and then upgrading through network to 8.10.

I updated manually the sources.list file to include all links to Hardy and to dapper-updates .... and it seemed to have worked.

Hope this helps

---

### Post by Eladon on 2008-06-13
OH NO, I can't believe this is still a problem.  I just wiped my server to reload, thinking "NO WAY 2 yrs later they'd release another LTS without having solved this problem yet.  But they haven't solved this problem yet.

Here's a bug report:

[https://bugs.launchpad.net/dru/+bug/148466](https://bugs.launchpad.net/dru/+bug/148466)

---

