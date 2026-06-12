---
title: "can't get current 20.04 updates, so can't upgrade to 22.04"
date: 2022-04-30
forum: Installation &amp; Upgrades
---

### Post by likux on 2022-04-30
When I run update-manager or apt-get update, I get this error message:

                        Reading package lists... Done
 W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
 W: Failed to fetch [http://repo.mysql.com/apt/ubuntu/dists/focal/InRelease](http://repo.mysql.com/apt/ubuntu/dists/focal/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
 W: Some index files failed to download. They have been ignored, or old ones used instead.

Then, when I select "upgrade" it tells me I have to install all current updates before upgrading, so I am stuck.
Thanks,
Alan Shank
Woodland, CA, USA

---

### Post by GhX6GZMB on 2022-04-30
Try changing the update server URL.

---

### Post by ubfan1 on 2022-04-30
See [https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction) fifth bullet under Upgrade Checklist.  Disable the third party repos, update, dist-upgrade then you should be able to try the 22.04 upgrade. Afterwards, add the third party repos, ... etc.

---

### Post by likux on 2022-05-25
> **ubfan1 said:**
> See [https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction) fifth bullet under Upgrade Checklist.  Disable the third party repos, update, dist-upgrade then you should be able to try the 22.04 upgrade. Afterwards, add the third party repos, ... etc.

I tried removing all the mysql packages in Update Manager, and the error from (apt update) went away, but I still got the same error message when I tried to upgrade to 22.04

Please install all available updates for your release before upgrading.

I just tried it both ways again, with and without mysql updates -- same result.
I am stuck on 20.04!

Thanks,
Alan Shank

---

### Post by grahammechanical on 2022-05-25
> Then, when I select "upgrade" it tells me I have to install all current updates before upgrading, so I am stuck.

What command are you running to force the online upgrade from 20.04 to 22.04? The link given in the third post says this:

> Upgrades from one LTS to the next LTS release are only available after  the first point release. For example, Ubuntu 18.04 LTS will only upgrade  to Ubuntu 20.04 LTS after the 20.04.1 point release. If users wish to  update before the point release (e.g. on a subset of machines to  evaluate the LTS upgrade) users can force the upgrade via the -d flag.

Unless you have a special reason to upgrade to 22.04 then it is best to wait until 22.04.1 is released in six months time. If Software & Updates>Updates tab to set to notify of new Ubuntu versions as long-term support versions then the OS will give notification at the right time.

Regards

---

### Post by likux on 2022-05-26
> **grahammechanical said:**
> What command are you running to force the online upgrade from 20.04 to 22.04? The link given in the third post says this:



Unless you have a special reason to upgrade to 22.04 then it is best to wait until 22.04.1 is released in six months time. If Software & Updates>Updates tab to set to notify of new Ubuntu versions as long-term support versions then the OS will give notification at the right time.

Regards

I used "sudo update-manaager -c -d". Then, when the Update Manager window comes up, I click "Upgrade". The -d should allow me to upgrade, right?  This doesn't seem to me to address my issue. If I wait six months for 22.04.1, is there any reason to expect I won't have this same issue, related to the mysql repository? 
Thanks,
Alan Shank

---

### Post by likux on 2022-05-27
I used:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 467B942D3A79BD29

and got the mysql to update.
I have decided to wait for 22.04.1, as you suggest.
Thanks,
Alan Shank

---

