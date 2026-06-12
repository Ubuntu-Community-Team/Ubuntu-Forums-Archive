---
title: "downloads keep failing when doing an upgrade from hoary to breezy"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by lerouxb on 2005-11-20
Hi

I upgraded my laptop to breezy first and then copied all the /var/cache/apt/archives deb files over to my desktop (in a hope that I won't have to download as many files)

I then changed my desktop's sources.list file in the same way I changed the one on my laptop.

I did a sudo apt-get update
and then a sudo apt-get -f dist-upgrade (so that it can download so long. I only have a 128kbps connection)

Then when I got to my pc, I saw it downloaded hundreds of files and then gave some error that it couldn't download all of the files. so I ran apt-get update again and started the whole sudo apt-get -f dist-upgrade again. I noticed that it said "Need to get 322MB/655MB of archives". (which was a bit funny, because I was pretty sure that was what it said before I started. what happened to all the files that downloaded over the past few hours?!)

Then the same thing happened.. same error and it wanted to download 332MB of files again. Then I didn't bother doing an update before starting again and deliberately killed the download here and there and started it again to make sure that the amount of files to download decreases along the way. It got down to about 70MB before I had to leave. (in other words.. it cached the files that already downloaded like it should)

Next day I wanted to continue the upgrade and it said 332MB again.. in the meantime I killed the update-notifier (thinking that it is what is somehow interrupting things) but that didn't help. I can only guess something is still periodically running apt-get update in the background and that is somehow interfering, but I don't know what/why.

When I upgraded this desktop from warty to hoary, I used the cd which explains why I didn't have this problem.

By the way.. I didn't restart in between tries, so I can't see how this failed because of temporary files. I have 65 gigs of space on my root partition, so that isn't the problem either.

and 332MB of packages don't change every few hours..

Any ideas? I'm going to download the breezy install cd iso and try to use that, but still.. it shouldn't be necessary. I've been an ubuntu  user since warty and I've installed/upgraded quite a few machines without ever having this issue..

---

