---
title: "Upgrade failed - what does this mean?"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2006-07-17
I followed the official directions for updating Breezy, then using Update Manager to get Dapper.  The text (pasted in below) popped up a couple of times during the process of updating Breezy in an "Error during Update" box, but I pushed on anyway.  Famous last words.  Finally, when Update Mgr. was trying to update to Dapper, the message came up again and the update process just quit.  
  
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

What does this mean?  The PC still appears to be functioning.  Stuck w/ dial-up @ home.  Had to do some maneuvering to get to a broadband connection.  I so wanted this to work tonite but looks like it ain't gonna happen!!

---

### Post by gerbman on 2006-07-17
> **Bartender said:**
> Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

What does this mean?The update manager isn't able to access the repository listed, which is a non-standard one to begin with. Look at your /etc/apt/sources.list file - you should see lines with URLs similar to those reported as errors. Comment them out with a "##" at the start of each line. Try to update again.

---

### Post by Bartender on 2006-07-17
gerbman -
Thanks very much!  Those two repositories have something to do with Automatix.  Editing the sources.list was right at the edge of my pathetic Linux abilities but I think it worked.  Update Mgr. commented that third-party repositories had been disabled, then proceeded.  It's upgrading right now.  You're a lifesaver.

---

### Post by gerbman on 2006-07-17
> **Bartender said:**
> gerbman -
Thanks very much!  Those two repositories have something to do with Automatix.  Editing the sources.list was right at the edge of my pathetic Linux abilities but I think it worked.  Update Mgr. commented that third-party repositories had been disabled, then proceeded.  It's upgrading right now.  You're a lifesaver.Cool. You're welcome. I'm curious as to why it mentioned anything about third-party repositories. Would you mind posting your sources.list file to satisfy my curiosity? :)

---

