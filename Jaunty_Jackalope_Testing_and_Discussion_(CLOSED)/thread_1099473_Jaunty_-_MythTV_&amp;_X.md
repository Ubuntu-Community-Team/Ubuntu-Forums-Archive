---
title: "Jaunty - MythTV &amp; X"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bon_the_one on 2009-03-18
Hi all,

I'm wondering if anyone else has this problem, I was running Jaunty Alpha 5 with Mythtv for a good 2 weeks and everything was fine. Then I ran a dist-upgrade on Monday 16th March 2009 and since then Myth is not working.

I'm using an ATI X300 Graphics card, and when you load either frontend or setup, you get a black outline of the box where you would normally see the icons being updated at launch, then nothing. Focus switches to the 'Myth' window, but nothing is visible. 

If you launch from a terminal, there is a large output of errors thus : 
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 62
  Minor opcode: 0
  Resource id: 0x3800030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode: 149
  Minor opcode: 5
  Resource id: 0x3800031

I'm running on the Radeon drivers, not fglrx. I've kept up to date since Monday, but there are no improvements. I have filed a bug on Launchpad, #344743 in case this is a new bug coming through.

Has anyone else seen this, and are there any suggestions on what might be wrong please?

Thanks,

Ian

Description: Ubuntu jaunty (development branch)
Release: 9.04

mythtv-common:
  Installed: 0.21.0+fixes19961-0ubuntu4
  Candidate: 0.21.0+fixes19961-0ubuntu4
  Version table:
 *** 0.21.0+fixes19961-0ubuntu4 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
        100 /var/lib/dpkg/status

mythtv-frontend:
  Installed: 0.21.0+fixes19961-0ubuntu4
  Candidate: 0.21.0+fixes19961-0ubuntu4
  Version table:
 *** 0.21.0+fixes19961-0ubuntu4 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
        100 /var/lib/dpkg/status

mythtv-backend:
  Installed: 0.21.0+fixes19961-0ubuntu4
  Candidate: 0.21.0+fixes19961-0ubuntu4
  Version table:
 *** 0.21.0+fixes19961-0ubuntu4 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
        100 /var/lib/dpkg/status

xserver-xorg-video-radeon:
  Installed: 1:6.12.0-0ubuntu2
  Candidate: 1:6.12.0-0ubuntu2
  Version table:
 *** 1:6.12.0-0ubuntu2 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status

---

### Post by rmcd on 2009-03-28
I just (3/28 ) upgraded to Jaunty beta from Intrepid and I have exactly the same problem, also with an X300 Radeon. It looks as if my package versions are more recent:

Package: mythtv-common
Version: 0.21.0+fixes19961-0ubuntu8

Package: mythtv-frontend
Version: 0.21.0+fixes19961-0ubuntu8

Package: xserver-xorg-video-radeon
Version: 1:6.12.1-0ubuntu1

Bug #341898 appears to be the same issue.

---

### Post by bon_the_one on 2009-03-28
Hi rmcd,

Bug #341898 is the problem. I've been tracking it and trying to help out whereever I can there.

Mario Limonciello kindly tracked it to a problem in Xorg, and developed at patch. I have tested it and now Myth works fine. Hopefully this will filter thru to release, but you can add his patches to your system and it should sort you out.

Bon


> **rmcd said:**
> I just (3/28 ) upgraded to Jaunty beta from Intrepid and I have exactly the same problem, also with an X300 Radeon. It looks as if my package versions are more recent:

Package: mythtv-common
Version: 0.21.0+fixes19961-0ubuntu8

Package: mythtv-frontend
Version: 0.21.0+fixes19961-0ubuntu8

Package: xserver-xorg-video-radeon
Version: 1:6.12.1-0ubuntu1

Bug #341898 appears to be the same issue.

---

### Post by rmcd on 2009-03-28
Thank you Bon.

---

