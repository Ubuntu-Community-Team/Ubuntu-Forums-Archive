---
title: "Downgrade Lyx version"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by user73916237 on 2018-10-03
Hello,

I come here from [this post]("https://askubuntu.com/questions/1080648/how-to-install-old-version-of-lyx?noredirect=1#comment1775814_1080648") in Ask Ubuntu. Yesterday, after installing some updates, Lyx stopped working properly. I have reported the bug to the Lyx developers in [this link]("https://www.lyx.org/trac/ticket/11323#comment:2"). The fact is that I need Lyx back again urgently and cannot wait one month to the new version with the bug (maybe) fixed. I wold like to return to the previous version that was ok, but cannot figure out how to do it. The update history log from yesterday is:

[IMG]https://i.stack.imgur.com/aPm2v.png[/IMG]

It seems to me that the version I had was 2.3.0-1 and it was updated to version 2.3.1-2. I have already tried 

```
sudo apt-get install lyx=2.3.0-1~bionic~ppa1
sudo apt-get install lyx=2.3.0-1
sudo apt-get install lyx=2.3.0
```

with no success. In all cases I got the error that the version does not exist.

Is there anything that can be done? I am in Xubuntu 18.04.

---

### Post by deadflowr on 2018-10-03
You have the ppa version, so you can downgrade to the Ubuntu repository version with [ppa-purge]("https://askubuntu.com/questions/307/how-can-ppas-be-removed")
Also, you should contact (or report a new bug) to the ppa team:
[https://launchpad.net/~lyx-devel/+archive/ubuntu/release]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release")
So they know it's broken and can get a fix out quickly.

---

### Post by user73916237 on 2018-10-03
Thanks for your answer. I have used ppa-purge and it worked. Now I have an old version of Lyx (2.2.3) that is properly working, although I cannot open any of the documents I have created with the version I had (the one before the update, 2.3.0-1). Is there any way to install version 2.3.0-1? Or it is impossible?

I have already reported the bug to the developers. They told me they will fix it by November.

---

### Post by user73916237 on 2018-10-03
My definite solution was to manually install Lyx 2.3.0-1 (lyx - 2.3.0-1~artful~ppa1 in [this link]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release/+packages")). For that, I manually downloaded the packages [fonts-lyx_2.3.0-1~artful~ppa1_all.deb]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release/+files/fonts-lyx_2.3.0-1~artful~ppa1_all.deb"), [lyx-common_2.3.0-1~artful~ppa1_all.deb]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release/+files/lyx-common_2.3.0-1~artful~ppa1_all.deb") and [lyx_2.3.0-1~artful~ppa1_amd64.deb]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release/+files/lyx_2.3.0-1~artful~ppa1_amd64.deb") from [here]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release/+sourcepub/8863078/+listing-archive-extra") (which indeed is part of [this]("https://launchpad.net/~lyx-devel/+archive/ubuntu/release/+packages")). Then I removed the 3 corresponding packages from my computer (manually using Synaptic) and finally I installed the downloaded packages using "right click --> software manager". Now I have Lyx 2.3.0-1 in Xubuntu 18.04 happily running, and will not update for a long time.

---

