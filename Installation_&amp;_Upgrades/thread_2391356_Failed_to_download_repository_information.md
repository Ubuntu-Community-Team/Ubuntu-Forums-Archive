---
title: "Failed to download repository information"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by simon114 on 2018-05-08
Good Evening,

Ive just done a fresh install of 18.04 and got everything pretty much as I want it, but when I try the software updater, I get the following message

```
E:The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
W:Skipping acquire of configured file 'contrib/binary-i386/Packages' as repository 'http://download.virtualbox.org/virtualbox/debian bionic InRelease' doesn't support architecture 'i386', 
E:The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu bionic Release' does not have a Release file.

```

So I changed the Download Mirror and still get the same result

Also when I try to untick a repository in Software and Update/Other software tab in greys out on me

Then when I close the Software and updates window i get this message

```
The information about available software is out-of-date
To install software and updates from newly added or changed sources, you have to reload the information about available software.
You need a working Internet connection to continue.
```

I can confirm that the internet is working perfectly



Any ideas please thank you.

---

### Post by ubfan1 on 2018-05-08
When your software and update/other software goes grey, move the window, to see if the authorization pop-up is under it.  You need to enter your password for such changes, and I have see the password window buried before.

---

### Post by oldos2er on 2018-05-08
If you visit [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) you'll see no bionic repo exists yet.

---

