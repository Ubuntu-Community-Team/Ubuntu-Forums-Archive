---
title: "Upgrading to Dapper RC from ISO without CD"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by shalinmangar on 2006-05-28
Hi Everybody,

I have been using Ubuntu Breezy stable for the last 5 months. I wanted to try out the Dapper Release Candidate and have downloaded it's alternate install CD ISO image.

But today, just as the download finished, I found out that my CD-writer has developed some problems and it'll take a week to get it fixed. So now my question is:
How do I upgrade my breezy distribution to dapper release without burning the ISO to a CD? I have a spare vfat partition on my disk on which I have enough space to copy or extract the ISO. Can I boot from that ISO without using a CD? I have heard about the bootfrom: GRUB parameter but never used it. I have a breezy CD that I can use to start the boot process. Now can anyone tell me how to go about it?

---

### Post by cjm5229 on 2006-05-28
Hi, if you have been doing the updates, chances are you were in RC before you downloaded the ISO. If not, just do a dist-upgrade and you will be. In fact there been some updates allready, since the ISO release that you will get with dist-upgrade.

---

### Post by cjm5229 on 2006-05-28
Sorry, miss read your post, just woke up. It would still be pretty easy to dist-upgrade I did it to my wifes computer a couple weeks ago might take an hour or so, especially if you are on dialup. Otherwise I would guess you would need to get the path to your ISO added to your repositories. and then do the dist-upgrade. 
You can use the update manager.  Use  [HTML]gksudo "update-manager-d"[/HTML]
It will do a pretty good job of upgradeing with or without the ISO in your repositories. You may have software installed that won't get upgraded just the ISO that will with dist-upgrade.

---

### Post by R3linquish3r on 2006-05-28
[QUOTE=cjm5229]Sorry, miss read your post, just woke up. It would still be pretty easy to dist-upgrade I did it to my wifes computer a couple weeks ago might take an hour or so, especially if you are on dialup. Otherwise I would guess you would need to get the path to your ISO added to your repositories. and then do the dist-upgrade. 
You can use the update manager.  Use  [HTML]gksudo "update-manager-d"[/HTML]
It will do a pretty good job of upgradeing with or without the ISO in your repositories. You may have software installed that won't get upgraded just the ISO that will with dist-upgrade.[/QUOTE]

You made a typo :). The command should be:

```

gksudo "update-manager -d"
```

:)

---

