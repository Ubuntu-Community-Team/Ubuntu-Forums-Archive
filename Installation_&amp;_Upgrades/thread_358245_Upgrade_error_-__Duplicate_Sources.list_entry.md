---
title: "Upgrade error -  Duplicate Sources.list entry"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by JarG0n on 2007-02-10
Help!

I received an upgrade message at the upper right corner like I normally do, however I received this error message.  How can I fix this?

[I]
"An error occured

The following details are provided:

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
"[/I]

---

### Post by JarG0n on 2007-02-10
I also get this error when reloading packages in Synaptic.
[I]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)[/I]

---

### Post by JarG0n on 2007-02-10
Can anyone help? :(

---

### Post by etank on 2007-02-10
Try commenting out the restricted and universe entries and then doing ```
sudo aptitude update
``````
sudo aptitude upgrade
```
if it is all clean then add back one of the entries and try it again.

---

### Post by zeddock on 2007-03-26
It appears this issue was fixed for me today when I did an UPDATE.  Afterwards there were no errors about dups, etc.


zeddock

---

### Post by zorkerz on 2007-03-29
I get errors about duplicates only when there are new updates. Any ideas?

---

### Post by moeFinley on 2007-05-27
I've been getting a similar message since upgrading to Fiesty.

```
W: Duplicate sources.list entry http://gb.archive.ubuntu.com feisty-security/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com feisty-security/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
```

Can I just delete one of the files?  What are these files?

I've checked sources.list and I don't have any duplicates in there.

Thanks for any help

---

