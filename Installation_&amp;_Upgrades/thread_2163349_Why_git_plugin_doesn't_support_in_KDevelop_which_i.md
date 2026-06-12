---
title: "Why git plugin doesn't support in KDevelop which installed from Ubuntu 12.04?"
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by sinjin0 on 2013-07-18
Hi Guys,

I prefer to use long term support version, so I'm still using Ubuntu 12.04 LTS.

Recently I wanted to change C/C++ IDE tool, so I chose KDevelop and it's quite nice :-)
But the problem is that I wanted to use KDevelop **with Git plugin feature**, but when I installed KDevelop from 12.04 repository, I can't find the feature in KDevelop.
The installed KDevelop version was 4.3, so **basically this version should have Git support, but it doesn't**...
Does any one know why this was happen?
And how I can add git plugin feature for KDevelop?

Just for reference, I installed 'git' before installing KDevelop.

I wanted to build KDevelop myself, but there was some dependencies issues, so I had to re-install Ubuntu...
So this is not good option for me... :-(

Thank you in advance.

Best Regards,
Sinjin

---

### Post by sinjin0 on 2013-07-18
Hmm, weird thing... Actually I just resolved this issue. What I did that

1) Removed all kdevelop/kdevplatform packages with sudo apt-get remove & sudo apt-get purge
2) Clean the apt-get cache with sudo apt-get clean
3) Install lots of git replated packages
  sudo apt-get install git git-core gitk git-el git-gui git-sh git-stuff gitg
4) Reinstall kdevelop, then it worked.

However I still don't know which packages was exactly depending on this issue yet...
Anyway I'll close this issue for now...

---

