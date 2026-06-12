---
title: "Upgrading Hardy to Lucid: Error during commit"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by ersuforum on 2010-06-02
I'm trying to do an online upgrade from Hardy to Lucid. I"m receiving the following error which occurs after all of the packages have been down loaded.  The error causes the upgrade to be aborted.

Error during commit
'E:Couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cycle.'
Restoring original system state

Searching around, I found some folks suggesting removing the open office package.  Another person went and did smaller upgrades instead of LTS to LTS.  I started to delete openoffice but found other things such as ubuntu desktop were also going to be removed so I stopped.

Can someone please help.  Thanks.

---

### Post by dino99 on 2010-06-02
ubuntu-desktop is a meta-package, so it can be removed if you want/need to customize your install ( ie if you dont want to install all the default apps)

the easiest way with a package/app issue is to remove/purge then reinstall it 

be sure to deselect all the third party repo and ppa before dist-upgrade and clean the cache

---

### Post by ersuforum on 2010-06-02
Thanks for the reply.  I'm a bit of a package management novice so please bear with me.  I use aptitude to perform package management functions and I'm trying to do the upgrade using update-manager --devel-release.

I didn't plan on doing a custom install.

Using aptitude, I tried removing the openoffice.org-writer2latex and openoffice.org packages.  I then retried the upgrade and the error message changed to the following:

Error during commit
'E:Couldn't configure pre-depend openoffice.org-common for openoffice.org-voikko, probably a dependency cycle.'

I'm not sure how to simply remove the openoffice suite without creating more dependency issues.  As shown with the above error message, removing the initial offending package simply moved me to a new dependency issue.  Is there a simple way to remove the open office suite so that I could reinstall it after the upgrade?

I don't think I have any 3rd party repos or ppas.  Would these be specified in my sources.list file?  

Searching around I found a few references to bugs in lucid for the openoffice.org-writer2latex package.  Maybe this is playing a roll.

---

