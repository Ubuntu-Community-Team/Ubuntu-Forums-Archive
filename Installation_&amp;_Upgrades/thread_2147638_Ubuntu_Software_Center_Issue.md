---
title: "Ubuntu Software Center Issue"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by baqar on 2013-05-22
Not downloading Chromium
Not downloading Gpartred
And several others.

I need to download Gparted as i am desperate to resolve this issue [http://ubuntuforums.org/showthread.php?t=2147618](http://ubuntuforums.org/showthread.php?t=2147618) :(

So here is it!
This is it what it shows on software center

When i tried the terminal 

[ATTACH=CONFIG]242898[/ATTACH]

When i tried the software Center

[ATTACH=CONFIG]242899[/ATTACH]


Now i downloaded the debian and tried to install it directly, this is what i got! What shall i do, i am in a mess now.

[ATTACH=CONFIG]242900[/ATTACH]

---

### Post by mantisdolphin on 2013-05-22
Same problem. Software Center says there are dependencies that are unresolved for Gparted. Grrrr.

---

### Post by mantisdolphin on 2013-05-22
Okay, in Ubuntu Software Center, just search "partition." GParted Partition Editor" comes up first on the list. Click install. The little progress arrows at the top of the window should start spinning with a little number "1" in front of them. I assume I'm installing the GParted now.  Ooops: "Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/g/gparted/gparted_0.16.1-1~getdeb1_amd64.deb](http://archive.getdeb.net/ubuntu/pool/apps/g/gparted/gparted_0.16.1-1~getdeb1_amd64.deb) 502  Proxy Error"

Hmmmm. So I need to download Gparted from elsewhere I guess. Wait.

So I click the link in this post and download the .deb file...and try to install with Software Center?

---

### Post by mantisdolphin on 2013-05-22
That worked. Not the easiest install ever.

---

### Post by fantab on 2013-05-23
Post the output of:
cat /etc/apt/sources.list

Certain additional repositories have to be enabled to install certain software. Have you enabled 'Independent' and 'Partner' repos. You can check with Software Center ->EDIT -> Software Sources -> Other

After enabling them you have to close Software Center and run sudo apt-get update from the terminal, then sudo apt-get install gparted.

---

