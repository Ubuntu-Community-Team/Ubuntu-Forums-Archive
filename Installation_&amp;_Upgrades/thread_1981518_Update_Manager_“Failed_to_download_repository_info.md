---
title: "Update Manager “Failed to download repository information” error"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by and1script on 2012-05-16
Whenever I try to install updates I get this:


[IMG]http://i.imgur.com/nPKYi.jpg[/IMG]


This is what it says under Details:

W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I am using 11.10 and Gnome 3, if it's relevant. Thanks

---

### Post by cortman on 2012-05-16
Whew- next time please post the screenshot as an attachment. There's a button for that down below the text box. Just FYI. :)

Looks like some repositories are no longer existent. Remove the entries from sources.list- in a terminal-

```
gksu gedit /etc/apt/sources.list
```

Delete the lines for the nonexistent repos and save. If they're not there, run

```
gksu nautilus /etc/apt/sources.list.d
```

and there'll probably be (at least one) file in there named something similar to the missing repository. Delete it/them.

---

