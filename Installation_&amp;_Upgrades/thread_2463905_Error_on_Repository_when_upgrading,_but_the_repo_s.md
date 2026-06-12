---
title: "Error on Repository when upgrading, but the repo seems not to exist in configuration"
date: 2021-06-21
forum: Installation &amp; Upgrades
---

### Post by simcax1 on 2021-06-21
I am trying to upgrade to 21.04, but receive this error:
W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., W:GPG error: [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32, E:The repository 'http://dk.archive.ubuntu.com/ubuntu bionic-updates InRelease' is not signed., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., W:GPG error: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32, E:The repository 'http://archive.canonical.com/ubuntu bionic InRelease' is not signed.

I have done a "grep InRelease *" in the /etc/apt directory as well as the /etc/apt/sources.list.d dir, and it comes up empty:

&#10140;  apt grep InRelease *
grep: apt.conf.d: Is a directory
grep: auth.conf.d: Is a directory
grep: preferences.d: Is a directory
grep: sources.list.d: Is a directory
grep: trusted.gpg.d: Is a directory
&#10140;  apt cd sources.list.d 
&#10140;  sources.list.d grep InRelease * 
&#10140;  sources.list.d 

So I am a bit puzzled as to where this repo is configured? How do I get past this? 

Running: 
&#10140;  sources.list.d lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.10
Release:	20.10
Codename:	groovy

---

### Post by deadflowr on 2021-06-21
The InRelease files are located in /var/lib/apt/lists.
These comes when you download the apt updates.

But as you're not even using bionic, I'd look through the sources.list(s) and disable or remove any references to it (bionic) in there/those.

Also, you might consider moving up to the latest release 21.04 since 20.10 is about to hit end of life soon.
It only had 9 months of support from it's time of release in October 2020.

---

### Post by ActionParsnip on 2021-06-21
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32

```
will import the key for the repository

---

### Post by simcax1 on 2021-06-21
I tried that, and it times out. For good measure I tried it again, and it times out still. This is the output:

&#10140;  apt sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
Warning: apt-key is **deprecated**. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
Executing: /tmp/apt-key-gpghome.GF5BJRo2Hf/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
gpg: keyserver receive failed: Connection timed out

---

### Post by simcax1 on 2021-06-21
Thx :-) I just tried remming out all mentions of bionic, but still receive the same error on trying to upgrade. Will check to see if I left out some lines - maybe just rightly try to delete them insted of commenting them out.

---

### Post by simcax1 on 2021-06-21
> **deadflowr said:**
> The InRelease files are located in /var/lib/apt/lists.
These comes when you download the apt updates.

But as you're not even using bionic, I'd look through the sources.list(s) and disable or remove any references to it (bionic) in there/those.

Also, you might consider moving up to the latest release 21.04 since 20.10 is about to hit end of life soon.
It only had 9 months of support from it's time of release in October 2020.

Yeah! Now it seems to work :-) I at least got past the previous error. I backed up all the sources files, and removed any mention of "bionic" from the files, and it seems to have done the trick - thanks!

---

