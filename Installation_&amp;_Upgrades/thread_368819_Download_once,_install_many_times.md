---
title: "Download once, install many times"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by bmartin on 2007-02-23
I have two copies of Ubuntu; one on my PC and one on my laptop. The downloads from the repos are slow on my connection and I get them hourly using a cron job on my PC. Downloading them to my laptop is quite slow, as I don't use it a lot.

I want to set up my PC as a "repository" for other computers on my network so that they connect to it for updates instead of Ubuntu's repos. What's the easiest way to do this? Is there a link you can point me to, or is there a certain term for the thing I'm trying to do... you know, some terms that I could search for to see how this can be done? Please note that I don't want to become a "complete" repository, but I do want to supply a number of packages to other computers on my network. I'm not looking to put another 2,000 packages on my computer to save myself a couple trips to the Edgy repos.

---

### Post by louis_nichols on 2007-02-24
hm... there are certainly several ways, but here's my idea:

use [this howto]("http://ubuntuforums.org/showthread.php?t=42862") to learn how to create your local repo. Make sure you read the whole thread, not just the initial post, as there are many troubleshooting tips there.

Then, you just create a repo in your folder /var/cache/apt. So, you install the updates on that machine and make sure you don't run

```
sudo apt-get clean
```

afterwards. But,

```
sudo apt-get autoclean
```

might be a good idea, though.

Then, you need to install a webserver (say, apache) and point the other computers to yours in sources.list . You could also use samba and mount the repo-folder on the other computers, so it will be seen as local repo.

---

