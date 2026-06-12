---
title: "upgrade 12 to 14 fails"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by nigelhorne on 2014-10-11
Any ideas?  Google shows nothing.  I get this:

```
[FONT=Menlo]root@utilite:/home/njh# apt-get clean[/FONT]
[FONT=Menlo]root@utilite:/home/njh# do-release-upgrade [/FONT]
[FONT=Menlo]Checking for a new Ubuntu release[/FONT]
[FONT=Menlo]Your Ubuntu release is not supported anymore.[/FONT]
[FONT=Menlo]For upgrade information, please visit:[/FONT]
[FONT=Menlo]http://www.ubuntu.com/releaseendoflife[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Get:1 Upgrade tool signature [198 B]                                           [/FONT]
[FONT=Menlo]Get:2 Upgrade tool [1,134 kB]                                                  [/FONT]
[FONT=Menlo]Fetched 1,134 kB in 0s (0 B/s)                                                 [/FONT]
[FONT=Menlo]authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' [/FONT]
[FONT=Menlo]extracting 'saucy.tar.gz'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Reading cache[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Checking package manager[/FONT]
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]Building dependency tree        [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]Building data structures... Done [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal Release.gpg                                [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal Release.gpg                                [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security Release.gpg                       [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates Release.gpg                        [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security Release.gpg                       [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates Release.gpg                        [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal Release                                    [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal Release                                    [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security Release                           [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates Release                            [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security Release                           [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates Release                            [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main armel Packages/DiffIndex              [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main Translation-en_GB                     [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main Translation-en                        [/FONT]

[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main Sources/DiffIndex                     [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/universe Sources/DiffIndex                 [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main armel Packages/DiffIndex              [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/universe armel Packages/DiffIndex          [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main Translation-en_GB                     [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main Translation-en                        [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/universe Translation-en_GB                 [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/universe Translation-en                    [/FONT]

[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main Sources/DiffIndex            [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/universe Sources/DiffIndex        [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main armel Packages/DiffIndex     [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/universe armel Packages/DiffIndex [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main Translation-en_GB            [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main Translation-en               [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/universe Translation-en_GB        [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/universe Translation-en           [/FONT]

[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main Sources/DiffIndex             [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/universe Sources/DiffIndex         [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main armel Packages/DiffIndex      [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/universe armel Packages/DiffIndex  [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main Translation-en_GB             [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main Translation-en                [/FONT]

[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/universe Translation-en_GB         [/FONT]
[FONT=Menlo]                                                  
..


[/FONT]

[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main Translation-en_GB             [/FONT]
[FONT=Menlo]Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main Translation-en                [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main armel Packages                        [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main Sources                               [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/universe Sources                           [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/main armel Packages                        [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal/universe armel Packages                    [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main Sources                      [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/universe Sources                  [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main armel Packages               [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/universe armel Packages           [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main Sources                       [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/universe Sources                   [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main armel Packages                [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/universe armel Packages            [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-security/main armel Packages               [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Err [http://ports.ubuntu.com](http://ports.ubuntu.com) quantal-updates/main armel Packages                [/FONT]
[FONT=Menlo]  404  Not Found                                                               [/FONT]
[FONT=Menlo]Fetched 0 B in 6s (0 B/s)                                                      [/FONT]
[FONT=Menlo]Reading package lists... Done    [/FONT]
[FONT=Menlo]Building dependency tree          [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]Building data structures... Done [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Updating repository information[/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release.gpg                                  [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release.gpg                                  [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release.gpg                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release.gpg                          [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release.gpg                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release.gpg                          [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release                              [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release                              [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy/main Sources                                 [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy/universe Sources                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security/main Sources                        [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security/universe Sources                    [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates/main Sources                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates/universe Sources                     [/FONT]
[FONT=Menlo]Fetched 0 B in 0s (0 B/s)                                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release.gpg                                  [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release.gpg                                  [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release.gpg                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release.gpg                          [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release.gpg                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release.gpg                          [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release                              [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release                              [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy/main Sources                                 [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy/universe Sources                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security/main Sources                        [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security/universe Sources                    [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates/main Sources                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates/universe Sources                     [/FONT]
[FONT=Menlo]Fetched 0 B in 0s (0 B/s)                                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release.gpg                                  [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release.gpg                                  [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release.gpg                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release.gpg                          [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release.gpg                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release.gpg                          [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy Release                                      [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release                              [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security Release                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates Release                              [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy/main Sources                                 [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy/universe Sources                             [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security/main Sources                        [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-security/universe Sources                    [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates/main Sources                         [/FONT]
[FONT=Menlo]Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) saucy-updates/universe Sources                     [/FONT]
[FONT=Menlo]Fetched 0 B in 0s (0 B/s)                                                      [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Error during update [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]A problem occurred during the update. This is usually some sort of [/FONT]
[FONT=Menlo]network problem, please check your network connection and retry. [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W:Failed to fetch [/FONT]
[FONT=Menlo]http://ports.ubuntu.com/ubuntu-ports/dists/saucy/Release Unable to [/FONT]
[FONT=Menlo]find expected entry 'main/binary-armel/Packages' in Release file [/FONT]
[FONT=Menlo](Wrong sources.list entry or malformed file) [/FONT]
[FONT=Menlo], W:Failed to fetch [http://ports.ubuntu.com/dists/saucy/Release](http://ports.ubuntu.com/dists/saucy/Release) [/FONT]
[FONT=Menlo]Unable to find expected entry 'main/binary-armel/Packages' in Release [/FONT]
[FONT=Menlo]file (Wrong sources.list entry or malformed file) [/FONT]
[FONT=Menlo], W:Failed to fetch [/FONT]
[FONT=Menlo]http://ports.ubuntu.com/dists/saucy-security/Release Unable to find [/FONT]
[FONT=Menlo]expected entry 'main/binary-armel/Packages' in Release file (Wrong [/FONT]
[FONT=Menlo]sources.list entry or malformed file) [/FONT]
[FONT=Menlo], W:Failed to fetch [/FONT]
[FONT=Menlo]http://ports.ubuntu.com/dists/saucy-updates/Release Unable to find [/FONT]
[FONT=Menlo]expected entry 'main/binary-armel/Packages' in Release file (Wrong [/FONT]
[FONT=Menlo]sources.list entry or malformed file) [/FONT]
[FONT=Menlo], W:Failed to fetch [/FONT]
[FONT=Menlo]http://ports.ubuntu.com/ubuntu-ports/dists/saucy-security/Release [/FONT]
[FONT=Menlo]Unable to find expected entry 'main/binary-armel/Packages' in Release [/FONT]
[FONT=Menlo]file (Wrong sources.list entry or malformed file) [/FONT]
[FONT=Menlo], W:Failed to fetch [/FONT]
[FONT=Menlo]http://ports.ubuntu.com/ubuntu-ports/dists/saucy-updates/Release [/FONT]
[FONT=Menlo]Unable to find expected entry 'main/binary-armel/Packages' in Release [/FONT]
[FONT=Menlo]file (Wrong sources.list entry or malformed file) [/FONT]
[FONT=Menlo], E:Some index files failed to download. They have been ignored, or [/FONT]
[FONT=Menlo]old ones used instead. [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Restoring original system state[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Aborting[/FONT]
[FONT=Menlo]Reading package lists... Done    [/FONT]
[FONT=Menlo]Building dependency tree          [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]Building data structures... Done

Here's my sources.list:

[/FONT]
[FONT=Menlo]deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) quantal main[/FONT]
[FONT=Menlo]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) quantal main universe[/FONT]
[FONT=Menlo]deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) quantal main universe[/FONT]
[FONT=Menlo]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) quantal-security main universe[/FONT]
[FONT=Menlo]deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) quantal-security main universe[/FONT]
[FONT=Menlo]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) quantal-updates main universe[/FONT]
[FONT=Menlo]deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) quantal-updates main universe[/FONT]
[FONT=Menlo]deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) quantal-security main[/FONT]
[FONT=Menlo]deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) quantal-updates main[/FONT]
```

---

### Post by ian-weisser on 2014-10-11
Looks like you are trying to update from 12.10 (quantal) to 13.10 (saucy) .
Both 12.10 and 13.10 are past end-of-life and are no longer supported.
Both sets of repositories have been withdrawn, which is why you cannot reach them.

12.04 (precise) and 14.04 (trusty) are currently supported releases.
There is a direct upgrade path from 12.04 to 14.04 . But you don't seem to be running 12.04.
There is no direct upgrade path from 12.10 to 13.04 nor to 14.04 .
The only supported upgrade path from 12.10 was to 13.04 (not 13.10), which is also past end-of-life.

That's a longwinded way of saying that the version of Ubuntu you seem to be running (12.10) has missed the bus for upgrades.

The recommended method for upgrading older, unsupported versions of Ubuntu are to 1) Backup your data, and 2) Use the 12.04 or 14.04 installer to install (not upgrade) a supported version of Ubuntu. The installer will try to preserve your data.

Why your system is trying to jump a from 12.10 to 13.10 instead of 13.04 is an interesting question...but only relevant if your system keeps trying after the install.

---

### Post by nigelhorne on 2014-10-13
Thanks for the reply.  There's nothing on it that I need to back-up, I can recreate it all.  Where is the installer for version 14?  All I could find was Wintel archictecture installers, not one for my Arm box.  Thanks.

-Nigel

---

### Post by ian-weisser on 2014-10-13
Desktop 14.04 for ARM isn't supported yet.
See [http://www.ubuntu.com/download/server/arm](http://www.ubuntu.com/download/server/arm) for available images.

---

### Post by nigelhorne on 2014-10-14
Ian,

Thanks for your reply.  Just to make sure that I've understood you correctly, Ubuntu have E-O-L'd a version for which they haven't produced an update?  That doesn't seem to make much sense.

-Nigel

---

### Post by ian-weisser on 2014-10-14
Ubuntu has never committed to forever support of any architecture. And has never supported all ARM versions.
Perhaps you were using a successful port? There are some out there.

Server for some versions of ARM is supported in 12.04 and 14.04.

I could be wrong, but I don't think Desktop for (some versions of) ARM was ever supported. I don't recall seeing it. Desktop for (some versions of) ARM is one of the goals of the Ubuntu For Devices (Ubuntu Touch / Ubuntu Phone) project.

Ubuntu evolves over time, and that means flavors and architectures come and go sometimes. One entire flavor, Gobuntu, was ended - it's functionality replaced by one checkbox in the installer. Other flavors, like Lubuntu and GnomeBuntu have been added. Similarly, architectures come and go - PowerPC was supported until a few years ago, and (some versions of ARM) will gain support soon.

---

