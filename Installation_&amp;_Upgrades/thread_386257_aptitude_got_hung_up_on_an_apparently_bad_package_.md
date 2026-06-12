---
title: "aptitude got hung up on an apparently bad package graphviz-cairo"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2007-03-16
[COLOR=Indigo][FONT=Georgia]I just got my 6-DVD complete Edgy Ubuntu distro for my AMD-64 system which has Edgy preinstalled. I was able to update the list of available packages using the command apt-cdrom. That part went just fine. During installation, aptitude bombed out when it tried to install graphviz-cairo. Here is output from a terminal screen:

[FONT=Courier New][COLOR=Black] Preparing to replace graphviz-cairo 2.8-2  (using .../graphviz-cairo2.8-2.amd64.deb)
 Unpacking replacement graphviz-cairo ...
 Ouch! Got SIGSEV, dying..
 Segmentation fault[/COLOR][/FONT]

Aptitude lists this package as H, meaning "half installed."
I tried to remove it, and this happened:

[FONT=Courier New][COLOR=Black] Removing graphviz-cairo ...
 /var/lib/dpkg/info/graphviz-cairo: 11: dot: not found
 dpkg: Error processing graphviz-cairo (--purge):
  suprocess post-removal script returned error exit status 127
 Errors were encountered while processing:
  graphviz-cairo
 E: Sub-process usr/bin/dpkg returned an error code (1)
 A package failed to install. Trying to recover:
 Press Return to continue[/COLOR][/FONT]

Now I am unable to install anything else, because no matter how I label that package (hold, purge, manual, whatever) I get one of the above two errors and aptitude bombs out. I might have missed something...

The other package managers also bomb out, but they are less informative than aptitude.

I do not yet have Internet access on my Ubuntu machine. Any suggestions or information regarding how I can resolve this issue and continue installing packages from my DVDs would be appreciated.

I don't particularly care if I ever install Cairo or not. I just want that package to stop hanging up the install process for all the other stuff I want!

Thanks

David
[/FONT][/COLOR]

---

### Post by David J Bush on 2007-03-17
[COLOR=Indigo][FONT=Georgia]Kicking this to the front again. Is there some file I could edit so that I can ignore graphviz-cairo and resume installation of all that software? Thanks[/FONT][/COLOR]

---

