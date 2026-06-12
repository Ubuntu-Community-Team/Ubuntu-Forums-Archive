---
title: "Upgrade ubuntu from 11.4 to 11.10"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by fadi3001 on 2013-04-07
Hi Experts 

I running Ubuntu 11.04 on Mac using Virtual box and trying to upgrade Ubuntu 10 11.10 by going to system-->Administration-->update manger 

but keep getting the following errors during the upgrade , can you please advise how can I solve this issue

======================================================
"Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry."

W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index)  
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

=====================================

Regards
Fadi

---

### Post by sanderj on 2013-04-07
Support for 11.04 stopped in 2012. See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions) 

So you can't update 11.04 anymore via online sources

---

### Post by fadi3001 on 2013-04-07
So is there any way that I can do that upgrade from other resources rather than online ones ? what is the other options to upgrade Ubuntu from 11.4 ?

---

### Post by sanderj on 2013-04-08
I think you can download Ubuntu 11.10, put it on CD, and use that to upgrade 11.04 to 11.10

---

### Post by fadi3001 on 2013-04-08
Hi [**[COLOR=#000000]sanderj[/COLOR]**]("http://ubuntuforums.org/member.php?u=754333"), 

sorry for the question if that is silly , but what is the upgrade procuder if I have the 11.10 on CD ?

Regards
Fadi

---

### Post by mörgæs on 2013-04-08
An upgrade is risky, and 11.10 is only supported for one month more, after which you need to upgrade again.

I recommend a fresh install of 12.04.2 or 12.10.

---

