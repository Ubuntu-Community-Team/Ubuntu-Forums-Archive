---
title: "gpg key problems..?"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by jepsen.klaus on 2007-02-09
Sorry to ask such a quistion. 

But I'm having some problems with my sourcelist, is get errors when i run "sudo apt-get update", it's missing some keys.. 

So i have been trying to open my sourcelist and find out if there is any keys, and when I open a Terminal and uses following commands to add the keys, I just get next following errors.. 

Commands :
# sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys Key
  # "gpg: "Key" not a key ID: skipping" (is the respons from the Terminal)

# sudo gpg --export --armor KEY | sudo apt-key add - xxxxxxx

Then I get following errors.. 

# gpg: WARNING: nothing exported
# gpg: no valid OpenPGP data found.


Is there anyone here that can help me ?? :)

After running "sudo apt-get update" in a Terminal, will my sourcelist end like this.. 

Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz)  404 Not Found [IP: 88.191.250.18 80]
Reading package lists... Done
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://kubuntu.org](http://kubuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://kubuntu.org](http://kubuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Where do i find and add these missing keys ??

---

### Post by machoo02 on 2007-02-09
Hi,

When you try to add in keys using GPG, you need to replace KEY with the actual key, and not just leave in the word key.  Also, most of those repositories should have instructions on how to add their keys right on the page.  Follow these links for the [beryl-project]("http://ubuntu.beryl-project.org/") and [medibuntu]("http://medibuntu.sos-sts.com/repository.php") repositories. For the kubuntu.org ones, put this into a terminal:```
 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

cheers!

---

### Post by martbd on 2007-02-23
Error still occurs as follows W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems

---

### Post by Dave67 on 2007-05-14
I am getting the same thing from medibuntu and I am using medibuntu's directions for adding the key and below in bold that is what they stated to type.

**main@main-desktop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -0- | sudo apt-key add - **
wget: invalid option -- 0
gpg: no valid OpenPGP data found.
main@main-desktop:~$

there is something wrong with what they tell us to type if not it would work,  the error tells us that the -0- option it does not like, plus what is that for?

I am using dapper 6.06

---

