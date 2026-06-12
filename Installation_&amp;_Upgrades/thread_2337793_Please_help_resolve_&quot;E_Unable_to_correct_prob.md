---
title: "Please help resolve &quot;E: Unable to correct problems, you have held broken packages.&quot;"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by Metallinut on 2016-09-21
I believe this may have begun when I attempted to upgrade from 14.04 to 16.04.

I'm on 14.04 now. If I try to upgrade via Software Updater it fails at "Calculating the changes". At the time, I gave up for the moment. Now, still on 14.04, I wanted to install some software, and when installing dependencies, some packages fail. Here is an example:

```

jp@mythtv:~$ sudo sudo apt-get install php5-sqlite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php5-sqlite : Depends: phpapi-20121212
               Depends: php5-common (= 5.5.9+dfsg-1ubuntu4.19) but 5.6.7+dfsg-1 is to be installed
E: Unable to correct problems, you have held broken packages.
jp@mythtv:~$

```

Another package is libdbd-sqlite3-perl:
```
jp@mythtv:~/Videos/TV$ sudo apt-get install  libdbd-sqlite3-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdbd-sqlite3-perl : Depends: perlapi-5.18.1
E: Unable to correct problems, you have held broken packages.
jp@mythtv:~/Videos/TV$ sudo apt-get install  perl-doc
Reading package lists... Done
Building dependency tree
Reading state information... Done
perl-doc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I saw [this]("http://askubuntu.com/questions/122105/how-do-i-locate-and-remove-broken-packages-that-i-have-installed"), but Synaptic doesn't show any packages with status 'broken'

---

### Post by sisco311 on 2016-09-21
Duplicate closed.

See: [https://ubuntuforums.org/showthread.php?t=2337791](https://ubuntuforums.org/showthread.php?t=2337791)

---

