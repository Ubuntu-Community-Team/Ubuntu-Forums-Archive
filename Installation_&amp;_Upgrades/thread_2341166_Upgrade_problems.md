---
title: "Upgrade problems"
date: 2016-10-25
forum: Installation &amp; Upgrades
---

### Post by mr2131 on 2016-10-25
The upgrade from 16:04 to 16:10 has failed several times. This is one of the error messages I received:

```
W:Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386', 
W:The repository 'http://us.archive.ubuntu.com/ubuntu lucid-backports Release' does not have a Release file., 
W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
W:[http://ppa.launchpad.net/christoph-egger/unknown-horizons/ubuntu/dists/saucy/Release.gpg:](http://ppa.launchpad.net/christoph-egger/unknown-horizons/ubuntu/dists/saucy/Release.gpg:) Signature by key 1A23E3BDE1AE87588D2A588152DD2361FA075CC4 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/oneiric/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/oneiric/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/raring/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/raring/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
W:[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/saucy/Release.gpg:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/saucy/Release.gpg:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1), 
E:Failed to fetch [http://packages.medibuntu.org/dists/lucid/InRelease](http://packages.medibuntu.org/dists/lucid/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?), 
E:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.26 80], 
E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Any ideas on what I should do next?

mr2131

---

### Post by Impavidus on 2016-10-25
There is a warning that you cannot download Google Chrome 32 bit, which is because Google dropped support for the 32 bit version of Chrome. Stop using Chrome or do a fresh install of a 64 bit Ubuntu (if your hardware can handle it).

There are some warnings about PPAs. Best to disable all PPAs before attempting an upgrade.

There are some errors about something that has to come from the lucid repositories. That's an old and now unsupported release. The repositories have closed. Better disable those repositories.

---

### Post by QIII on 2016-10-25
mr2131:

Please use code tags when posting the output of commands issued in the terminal.  Code tags preserve formatting (which keeps the "smiley faces" out) and makes your post far easier to read.

To use code tags, you may:

1.  Click the # button in the tool bar above the text input box, move your cursor between the code tags and either type or paste your text.

2.  Type or paste your text, highlight it and then click the # button in the tool bar above the text input box.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

