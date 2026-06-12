---
title: "cant upgrade from 11.04 to 11.10 + 12.04"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by LinuxIsTheBest on 2012-05-18
*sorry for my English, i'm just 13 from Europe*
I've tried to upgrade my 11.04 ubuntu (64bit), and I've failed when I've by the terminal + update manager + disk on key...
At first I've tried by the update manager- problem with the serve or internet connection (the famous problem).
terminal-

W: Failed to fetch [http://ppa.launchpad.net/antonoio/ch...source/Sources](http://ppa.launchpad.net/antonoio/ch...source/Sources) 404 Not Found


W: Failed to fetch [http://ppa.launchpad.net/antonoio/ch...amd64/Packages](http://ppa.launchpad.net/antonoio/ch...amd64/Packages) 404 Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.


And by a DOK-
Everything was OK till I should choose between install alongside, replace, upgrade, sometging else.
What happend? I wasn't able to select upgrade- it was a little bit darker gray then the others + didn't give to me choose it.
Also, even I was connected to the internet it didn't give me to mark download updates while installing + written that I without an internet connection!
I've tried it with 12.04 + 11.10 (I have 11.04) & it's the same!
What can i do?
Please help, i got tired of this version...

---

### Post by zvacet on 2012-05-20
In terminal

```
gksudo gedit /etc/apt/sources.list
```

put # sign in front of PPA-s.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

After that you should be able to install 11.10 from update manager.

---

