---
title: "Upgrading Wubi Drive Size"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by barrycorbett on 2011-07-07
Hi this is my first post so I appoligse if this is in the wrong topic ;). I recently installed Ubuntu 11.04 on my 5 year old laptop and I think it runs pretty well :). It was installed with Wubi and is dual booting with Windows XP Home edition. I was wondering how to increase the size of my Ubuntu drive from 6GB to 7GB. I know that there are articles about this in the Wubi guide but I just want confirmation about the exact commands I need to use. I dont want any of my XP files harmed and I don't want any of my Ubuntu files harmed. 

Thanks in advance :D,

Barry Corbett

---

### Post by bcbc on 2011-07-07
Take backups of your files if you are worried about them. :p

The wubi virtual disk can be resized using this guide: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

(It's mentioned in the Wubi guide, so you've probably seen it already. If you need help with any particular part of it, then feel free to ask for specific explanations.)

---

### Post by barrycorbett on 2011-07-12
Hi! 

I just followed the guide and it works great :D :popcorn:

---

### Post by bcbc on 2011-07-12
> **barrycorbett said:**
> Hi! 

I just followed the guide and it works great :D :popcorn:

Great! I've used it quite a few times myself ;)

PS avoid hard shutdowns on wubi installs - even if it appears unresponsive, first attempt a restart using Alt+SysRQ R-E-I-S-U-B. If you follow this approach you should be okay. Unfortunately there are reports of some users losing their wubi virtual disks through corruption combined with windows chkdsk. My advice is to keep regular backups of anything that is important to you (off the virtual disk). 

On that note, Ubuntu One is great for auto-synching small files to the cloud, and any large multimedia files you can leave on the host ntfs partition, mounted under /host (then you also will be less likely to run out of space in the future).

---

