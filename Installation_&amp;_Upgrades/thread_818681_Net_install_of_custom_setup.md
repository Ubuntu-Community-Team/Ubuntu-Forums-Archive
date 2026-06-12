---
title: "Net install of custom setup"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by vtechstu on 2008-06-04
Hi,

I'm trying to figure out the best way to push out a custom build of ubuntu.  ie, I intalled ubuntu on one system, completely customized it, installed the files and all my documents, and wanted to push that exact thing to 20 other identical machines in parallel, not serially, if possible.  

I have considered using rsync or partimage somehow, but both seem to require linux be on the computer one is copying to. The 20 or so computers will be blank drives.

In the past we have used a cloner, which given a Master, clones out 5 completely identical drivers in an hour or so. The problem with this is that it does it bit for bit (dd?)  I think I would save a lot of time if I could speed up this process by not doing bit by bit, but only the used part part of the build.

Any ideas on this?

#### One idea i'm currently having is to do a netboot install from an image on the server all at once.  then after the installation, have each run a script which will update the folders from sbackup

####### Unless anyone has a better idea.  I might go with an unattended network install of each machine, then after the systems are finished, have a script have each of them use sbackup to restore the settings to the master image. 

chase

---

