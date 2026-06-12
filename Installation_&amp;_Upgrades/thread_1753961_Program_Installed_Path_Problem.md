---
title: "Program Installed Path Problem"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by SomeoneKnows on 2011-05-09
I'm not sure which forum is best to ask this question but it is related to an installation problem. I'm trying to learn about using Git to download a repository and compile the source. I'm trying to download and install Git itself.

I originally used Synaptic to install the git-core program and used Git 1.6.6.3 to download a newer version of Git. I changed directory to the downloaded code. I ran:
   make prefix=/user/local all
   sudo make prefix=/user/local install

When everything finished I ran git --version but still get the old 1.6.6.3 version.

I used "whereis git" and found:
git: /usr/bin/git /usr/local/bin/git /usr/share/manl/git.1.gz

So I tried using Synaptic again and marked git-core for Complete Removal assuming that getting rid of the first install would allow the second in /usr/local/bin/git work instead.

Now when I run $ git it says:
   bash: /usr/bin/git: No such file or directory

If I run $ /usr/local/bin/git --version it displays my new install:
   git version 1.7.5.1

What am I missing to get the new version to run when I try running just $ git?

---

