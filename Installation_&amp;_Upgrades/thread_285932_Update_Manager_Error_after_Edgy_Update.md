---
title: "Update Manager Error after Edgy Update"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Wheelman on 2006-10-27
My update from the CD seemed to have gone smooth although it said since I have a slow connection it disabled some third party repositorys and that I could re-enable them later.  Anyone know where I can go to do this?  I should have written it down. ](*,) 

Also when I try to run update manager now I get this error.

"Could not download all repository indexes"
"the respository might no longer be availible or could not be contacted because of network problems........

the one it lists is 
"http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:Sub-process gzip returned an error code (1)"

Any idea how to fix this one?

Thanks

---

### Post by sylverpyro on 2006-10-29
> 
it said since I have a slow connection it disabled some third party repositorys and that I could re-enable them later. Anyone know where I can go to do this?


As long as edgy has not changed where it keeps apt the file you are going to want is:
/etc/apt/sources.list

Find the repositories that you want to enable again and simply remove the #'s from in-front of them.  There is some GUI tool for this also, but I do not know what it is called off the top of my head.

---

