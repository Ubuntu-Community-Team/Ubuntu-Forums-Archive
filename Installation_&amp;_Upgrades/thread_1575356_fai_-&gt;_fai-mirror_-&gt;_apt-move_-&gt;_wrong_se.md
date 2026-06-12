---
title: "fai -&gt; fai-mirror -&gt; apt-move -&gt; wrong sections"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by #Valentin on 2010-09-15
Good evening,

I am using FAI (fai-mirror) for creating a partitial mirror on my local system. This mirror servers for creating a installation medium (.iso for CD/DVD).

In general, a custom script is calling fai-mirror and fai-mirror itself calls apt-move for moving the downloaded packages from the apt cache into the designated directory (e.g. /home/ftp/mirror/pool/main/....).

I am also using non-free packages, such as opera.

Unfortunately the section of those packages (section entry in the debian/control file of each package) is something like non-free/browser and therefore apt-move creates a new directory in my pool.
Example directory structure:

/home/ftp/mirror/pool..
-> directory main
-> directory non-free
-> directory contrib
etc.


My goal is that the packages from non-free, contrib etc. are moved into "main". Therefore I think it is necessary to change the "section" entry in debian/control in e.g. "main" or something like this.

A possible solution would be not to touch anything and just move the packages manually after the creation of the pool and .iso-file is complete. Unfortunately this is not always possible for me and of course this is not a very beautiful workaround.

My goal is to automatize this process while fai-mirror or apt-move are doing their job.

So, at first my idea was to have a look at what really happens in fai-mirror and apt-move. As it turns out, an apt cache is created during the whole process and this cache also contains lists of the downloaded packages. Those lists are created before apt-move moves the packages to the mirror/pool folder.

I had the idea to write a little bash script (or let's say to enter some lines of code in fai-mirror or apt-move) which modifies the package lists and changes the section entries.

Unfortunately this did not work since fai-mirror and apt-move get the information for the correct section elsewhere (in fact they are asking the dpkg-tools to hand over the section for each deb package).

But I don't want to modify the packages and e.g. extract them, change the information in debian/control and then build them again.

My final question is:
Do you have any idea how I can force fai-mirror and apt-move to move the packages to the main directory instead of to /mirror/pool/section-name?

The problem in my case is that the apt sources-list files don't know all possible sections of all packages, therefore updates etc. are not applied (packages are simply not found when they are not in "main", but in non-free etc.).

I already had a very close look at fai-mirror and apt-move, but unfortunately I did not find a good solution (I am open to patching those tools if it is necessary).

As far as I know the ppl which are working on apt-move once planned to let apt-move modify section entries or the target directories, but this is just a rumor and I don't know how reliable this information is.

Any help is highly appreciated.

---

