---
title: "impossible installation : &quot;packages have unmet dependencies&quot; and &quot;broken packages&quot;"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by SCheva on 2018-05-08
Hello everyone :)

I try to install "muse", and I have this message :
```
The following packages have unmet dependencies:
 muse : Depends: liblo7 (>= 0.26~repack) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

I'm really sorry but even looking on the forum I have not been able to correct this problem. This is not the first installation that blocks due to broken package.

**This is the result of `apt-get install -f` :**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
```

**The result of `sudo apt-get update --fix-missing` ends with :**
```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/chrome/deb stable Release: The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
W: The repository 'http://download.ebz.epson.net/dsc/op/stable/debian lsb3.2 Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net/voldyman/markmywords/ubuntu xenial Release: The following signatures were invalid: BADSIG 837E86B594DF3268 Launchpad PPA for Akshay Shekher
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
E: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages  Writing more data than expected (2627 > 492) [IP: 2001:860:f70a::2 80]
W: Failed to fetch http://ppa.launchpad.net/voldyman/markmywords/ubuntu/dists/xenial/Release.gpg  The following signatures were invalid: BADSIG 837E86B594DF3268 Launchpad PPA for Akshay Shekher
E: Failed to fetch http://linux.teamviewer.com/deb/dists/stable/main/i18n/Translation-en  403  Forbidden [IP: 2600:9000:2007:9000:1c:3aaa:b100:93a1 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

**The result of `apt-get update` ends with :**
```
W: http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg: Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)
E: Failed to fetch http://linux.teamviewer.com/deb/dists/stable/main/i18n/Translation-en  403  Forbidden [IP: 2600:9000:2007:f000:1c:3aaa:b100:93a1 80]
E: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages  Writing more data than expected (2627 > 492) [IP: 2001:860:f70a::2 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I do not know in which direction to look.

Many thanks :)

---

### Post by rsteinmetz70112 on 2018-05-08
You could try starting Synaptic and seeing if it identifies any "broken" packages then re install them. Sometimes it can fix things apt-get can't
It seems the problem is with some of your repositories. 
Check your repositories and make sure all are correctly identified. You seem to have a fair number of third party repositories

---

### Post by TheFu on 2018-05-08
Well, if you run each of those commands in the reverse order, that would be better.
update
upgrade
and if there are issues, follow the instructions output.

Also, remove any 3rd party packages and 3rd party PPAs to get the core stuff consistent again.

Then try installing only the packages you need.

BTW, **aptitude** has a better dependency resolver than other APT front-ends.  If you don't like the suggested solution, reject it and it will probably provide another and another and another.

We've all been in "apt-hell" at some point. It isn't THAT unusual, but whenever .deb files are installed manually, it will almost always lead to apt-hell in 3-6 months as that package holds back dependencies.

Welcome to the forums.

---

