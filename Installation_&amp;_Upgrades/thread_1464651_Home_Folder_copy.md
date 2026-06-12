---
title: "Home Folder copy"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by gnarliprime on 2010-04-28
I had backtrack partition the drive during installation and busted my  ubuntu 10.4. The graphics are looking like an old version. when i log in  it goes to black screen then goes back to login. There is a message  that comes up upon logging in that says something  about "install did not configure power correctly" or something of the  like.  When i go to tty1 i am able to log in and run apps. I reinstalled  x server, did apt-get update, upgrade, and dist-upgrade. 

Essentially  all I am looking to do is grab my files out of the home folder and copy  them to my other partition so i can reinstall. Or a fix would work as  well. I tried to cp my Documents folder to /home, which did nothing, i  got a message that said "cp: omitted /home/cereal/Documents" i also  chmod 777 the home folder then tried to copy and i got the same result.  Any ideas?

And the home folder is encrypted and i can't figure out how the ecryptfs-private-mount works to be able to retrieve them from the working distro. I get a "this folder was not encrypted correctly" or something to the like when i try.

---

