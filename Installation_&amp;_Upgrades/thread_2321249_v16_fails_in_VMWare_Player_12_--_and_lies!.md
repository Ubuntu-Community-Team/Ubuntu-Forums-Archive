---
title: "v16 fails in VMWare Player 12 -- and lies!"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by FerryGnu on 2016-04-21
Just trying to follow the upgrade process as described

  sudo update-manager -d

Contrary to the web page, you can't sit back as there are a string of questions during the process. :D

Which, after answering and a total of twenty minutes elapsed time, I got another message, "Cannot upgrade," and it auto rolled back to v14-LTS. Just prior to that message, I had a dialog asking if I wanted to empty the Trash. Before I could respond it threw up the message and rolled it back.

My guess is it DID NOT look at the VMWare dynamically sized space available and was not smart enough to figure out that the 120GB size I had allocated within VMWare was not the size is was measuring of 346mb free space. 

Can I get some advice on how to upgrade within VMWare Player without a fresh install. 

Also, how about that available size check BEFORE it starts going through the upgrade, rather than have me wait twenty minutes to find out. That's a no brainer for this old programmer.

---

