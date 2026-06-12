---
title: "[SOLVED] Updater Stopped Working"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by ronparent on 2008-09-05
My updater stopped working with the following message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

What do I do now (besides informing this forum of the problem)?

I've encountered this type problem before with "Available" and was able to eliminate it by rerunning the updater repeatedly and manually corrected the corrupted line where it crashed.  It seems that for this type problem I should be able to somehow reconstruct the essential configuration files from scratch. Line by line editing is tedious to say the least!

---

### Post by ronparent on 2008-09-06
I see I'm getting no response to my questions - so I played around a bit and fixed the problem!

Since the file "/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages" would not parce, I used the following command to remove it:

sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages.old

And then in order ran:

sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

This solved the problem. I admit I had only the foggiest notion of what I was doing - sort of like a half trained monkey following a trail of bread crumbs. :) :) :)

---

