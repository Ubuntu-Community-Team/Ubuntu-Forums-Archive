---
title: "unmet dependencies during preseed install"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by kill4killin on 2013-05-15
I am working on configuring an automated install for use in the office and have come up with a preseed file that, for the most part, works. The sticking point I've hit is getting the "ubuntu-desktop" to install. When I added the following line to my preseed file:

```
tasksel    tasksel/first    multiselect    ubuntu-desktop, print-server, openssh-server
```

I get the following error:

```
The following packages have unmet dependencies:
xserver-xorg-video-all : Depends: xserver-xorg-video-ati but it is not installable
                                 Depends: xserver-xorg-video-nouveau but it is not installable
E: unabele to correct problems, you have held broken packages.
tasksel: apatitude failed (100)
```

Removing the tasksel line from the configuration resolves this error but it does not fix my problem because I need the tasksel portion to be automated with no user input and removing this line causes it to prompt the installer for a response.

Any help on this would be appreciated, for completeness I've placed my preseed file (redacted of company info) in a github gist:
[https://gist.github.com/anonymous/5588337](https://gist.github.com/anonymous/5588337)

---

