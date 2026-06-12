---
title: "Update Manager fails to update"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by aakmal on 2013-03-17
Would appreciate any guidance on the following:

-I am running Ubuntu 12.04 LTS
-An icon consisting of a red exclamation point has appeared on the horizonal desktop bar, and tells me update information is outdated
-When running update manager, updates are downloaded. But appear to fail to install. I do not always get an error message, but
 Update manager tells me last update was some time in the past, even though I have just run an update.

The original cause of my troubles began when I rashly deleted some files to fix a perceived earlier problem:

sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en 
sudo rm /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages 

Any guidance on how to get my updates working again would be greatly appreciated. Thank you.

---

### Post by sanderj on 2013-03-17
Open a terminal, and run:

```
sudo apt-get update
```

and post the output here

---

### Post by aakmal on 2013-03-17
Here is the tail of the ouput from sudo apt-get update:



Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.


Thanks.

---

### Post by cortman on 2013-03-17
Looks like you have a GPG error. Ubunt uses a GPG (encryption protocol) key to check and make sure the server it's getting the updates from is genuine. Instructions on fixing this [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

---

### Post by aakmal on 2013-03-17
Yes! that worked.

Thank you very much, cortman and sanderj.

---

