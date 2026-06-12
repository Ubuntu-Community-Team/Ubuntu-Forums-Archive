---
title: "VMWare Fusion 2.0 and &quot;hardy herron&quot; strangeness..."
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by yrrej on 2008-10-23
Hi,
I am running Ubuntu 8.04.1 under VMWare's Fusion 2.0  on a MacBook Pro 
running the latest OSX software with 4GB memory and a vast amount of
diskspace :) The MacBook Pro is last years 2.4 GHZ Santa Rosa chip set.

My problem is with updates/installs.

Most of the times when the update manager shows that there are updates some of
the updates appear to be corrupted ( I get a "bad tar archive" error message) during
the unpack phase.

Removing the "bad" deb from the archive directory and re-downloading generally
does no good, I get the same error.

However if I download to my mac and import the deb to the archive directory and
tell the update manager to do its magic, it works!  ( I manually download the new
debs from packages.ubuntu.com).

I have never had this problem with my WinXP or Fedora 9 VMs.

I have even downloaded the Ubuntu install CD and created a fresh VM but
attempting to upgrade the system lead to the same corrupt deb files...

The Fusion forums "suggested" that perhaps the archives were corrupted on
the servers...I find it hard to believe that a corrupt kernel would go unnoticed 
for long...

Any suggestions?

Jerry

---

