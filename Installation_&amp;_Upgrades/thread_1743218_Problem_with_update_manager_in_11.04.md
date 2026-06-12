---
title: "Problem with update manager in 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by NewReformist on 2011-04-29
So I just installed the new Ubuntu 11.04 Natty system on my computer, one thing that doesn't seem to work well is the update manager. At first it worked, but now I get the error message: 

W:Failed to fetch [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I get a similar response when I try to update through the terminal (sudo apt-get update)

Anyone who know what I can do?

---

### Post by mörgæs on 2011-04-29
It could be because of overloaded servers. Do you still have the problem?

---

### Post by NewReformist on 2011-04-30
> **mörgæs said:**
> It could be because of overloaded servers. Do you still have the problem?

Yes unfortunately :( 

I couldn't at first find my original thread about this so I started a new one with more info about my issue here:

[http://ubuntuforums.org/showthread.php?t=1744148](http://ubuntuforums.org/showthread.php?t=1744148)

---

### Post by dino99 on 2011-04-30
can you open these url with your browser ? (watch at typo error maybe)

as you can find yourself, there is no natty repo, the latest is karmic !!!
[http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/)

---

### Post by NewReformist on 2011-05-01
> **dino99 said:**
> can you open these url with your browser ? (watch at typo error maybe)

as you can find yourself, there is no natty repo, the latest is karmic !!!
[http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/)


What exactly does this mean then? What do you mean with open them?

Should I try to re-install ubuntu again?

---

### Post by pixering on 2011-05-01
Update manager error:
> W:Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

With the first source, starting from [http://ppa.launchpad.net/](http://ppa.launchpad.net/) , I went through the directories to find if the source existed.
It stops at [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/), where the "natty" subfolder does not exist.

I have tried using different servers, such as the main server which gave me this error:
> Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

I haven't been able to update for 15 days... HELP!

---

### Post by pixering on 2011-05-01
> **dino99 said:**
> can you open these url with your browser ? (watch at typo error maybe)

as you can find yourself, there is no natty repo, the latest is karmic !!!
[http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/](http://ppa.launchpad.net/wgrant/mercury/ubuntu/dists/)

I get the feeling that many updates aren't available for ubuntu 11.04...

---

### Post by mörgæs on 2011-05-01
This might be the fast and safe solution:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by NewReformist on 2011-05-02
Thanks all for the help.

So this is what I did: re-installed the ubuntu system.

I tried the other options but it did not work, now it seems though that updates works as they should.

---

### Post by mörgæs on 2011-05-02
Good, please mark the thread 'solved'.

---

