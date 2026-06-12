---
title: "failed to find release.gpg when upgrading to 6.10"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by ace_low on 2006-10-26
Good evening good people, 
when trying to upgrade from 6.06 to 6.10 using upgrade manager, the upgrade process begins, I'm still at first step (Preparing the upgrade), I'm beginning to fetch files, then I'm getting the following message:
"Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Temporary failure resolving ‘packages.freecontrib.org’"

did anyone encountered the same error message? is there anything missing in my current configuration? could it be because of heavy load on servers?

thanks.

---

### Post by arthurbarnhouse on 2006-10-26
I'm gonna bump this, I had this exact same problem and this is the only thing that is coming up on the forum searches.  

Any help would be apprecated.

---

### Post by robert_h06 on 2006-10-26
I have the exact same problem.

---

### Post by robert_h06 on 2006-10-26
Fixed the problem.  I disabled the [http://packages.freecontrib.org/](http://packages.freecontrib.org/)... in the repositories list in Synaptic Package Manager.

---

### Post by ace_low on 2006-10-27
Hi again, I removed the freecontrib packages and tried again... this time I get:
"Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz) Sub-process gzip returned an error code (1)".

any ideas?

thanks

---

### Post by pattu on 2006-10-27
I'm getting the exact same problem.

```
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg Temporary failure resolving 'packages.freecontrib.org'
```

---

### Post by ace_low on 2006-10-27
I saw at another posting that the package might be in process of updating. I initiated the upgrade about 10 minutes ago, and currently it's working without any problem.

---

### Post by nevillef on 2006-10-27
I have been trying to upgrade as well but have had no luck. I have tried using the alternate CD for AMD64 and using Update manager and they both come up with the same error.

Failed to fetch [http://seveas.ubuntulinux.nl/dists/dapper-seveas/Release](http://seveas.ubuntulinux.nl/dists/dapper-seveas/Release) Unable to find expected entry  list_of_sections/binary-amd64/Packages in Meta-index file (malformed Release file?)

I don't know why it is looking there as all the updates come from a server in Australia where I live. Why is it looking for Dapper? Shouldn't it be looking for Edgy?
Any ideas or is it just so busy with everyone trying to update. Maybe should just wait a couple of days.

---

### Post by nevillef on 2006-10-27
I worked it out. Apparently it is a source for automatix packages and must not be updated for Edgy yet. Just took it out of the sources list.

---

