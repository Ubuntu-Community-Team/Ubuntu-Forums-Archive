---
title: "Update problem: Failed to fetch bzip2:/var/lib/apt/lists/partial"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by zintinos on 2014-04-22
Hey everyone !

I'm an ubuntu user since a couple of years but this is the first time I use the forum. 
While i was updating to Ubuntu 14.04 the update-manager gave me this error message:

***W:Failed to fetch bzip2:/var/lib/apt/lists/partial/it.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages Hash Sum mismatch, E:Some index files failed to download. They have been ignored, or old ones used instead.***

I tried to search for a solution and I found 

[B][I]rm -rf [COLOR=#333333][FONT=Ubuntu]/var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]apt/lists/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]partial/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*[/FONT][/COLOR]
update-manager -d
[/I][/B]
Anyhow it didn't work, and I didn't find any other solution on the web.

thank you in advance for the help
cheers
Ian

---

### Post by zintinos on 2014-04-22
The Problem solved by its self ! probably the servers where overwhelmed by requests ?!

cheers Ian

---

