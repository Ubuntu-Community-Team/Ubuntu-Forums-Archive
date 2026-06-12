---
title: "Problem parsing dependency Replaces"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by NLS___87 on 2007-09-15
Hi!

```

$ sudo apt-get check
Reading package lists... Error!
E: Problem parsing dependency Replaces
E: Error occurred while processing libvorbisfile3 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

how can I solve this problem? I can't upgrade/install/remove packages :(

Sorry for my bad english :(

---

### Post by Pumalite on 2007-09-15
[http://ubuntuforums.org/showthread.php?p=3317509#post3317509](http://ubuntuforums.org/showthread.php?p=3317509#post3317509)

[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

---

### Post by NLS___87 on 2007-09-15
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?p=3317509#post3317509](http://ubuntuforums.org/showthread.php?p=3317509#post3317509)

[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

It didn't work:

```
$ sudo dpkg --clear-avail && sudo apt-get update
Get:1 http://ubuntu.dcc.fc.up.pt gutsy Release.gpg [191B]
Ign http://ubuntu.dcc.fc.up.pt gutsy/main Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy/restricted Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy/universe Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy/multiverse Translation-en_US
Get:2 http://ubuntu.dcc.fc.up.pt gutsy-updates Release.gpg [191B]
Ign http://ubuntu.dcc.fc.up.pt gutsy-updates/main Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-updates/restricted Translation-en_US
Get:3 http://ubuntu.dcc.fc.up.pt gutsy-security Release.gpg [191B]
Ign http://ubuntu.dcc.fc.up.pt gutsy-security/main Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-security/restricted Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-security/universe Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-security/multiverse Translation-en_US
Get:4 http://ubuntu.dcc.fc.up.pt gutsy-proposed Release.gpg [191B]
Ign http://ubuntu.dcc.fc.up.pt gutsy-proposed/restricted Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-proposed/main Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-proposed/multiverse Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-proposed/universe Translation-en_US
Get:5 http://ubuntu.dcc.fc.up.pt gutsy-backports Release.gpg [191B]
Ign http://ubuntu.dcc.fc.up.pt gutsy-backports/restricted Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-backports/main Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-backports/multiverse Translation-en_US
Ign http://ubuntu.dcc.fc.up.pt gutsy-backports/universe Translation-en_US
Hit http://ubuntu.dcc.fc.up.pt gutsy Release
Hit http://ubuntu.dcc.fc.up.pt gutsy-updates Release
Hit http://ubuntu.dcc.fc.up.pt gutsy-security Release
Hit http://ubuntu.dcc.fc.up.pt gutsy-proposed Release
Hit http://ubuntu.dcc.fc.up.pt gutsy-backports Release
Hit http://ubuntu.dcc.fc.up.pt gutsy/main Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy/restricted Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy/main Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy/restricted Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy/universe Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy/universe Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy/multiverse Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy/multiverse Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-updates/main Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-updates/restricted Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-updates/main Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-updates/restricted Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/main Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/restricted Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/main Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/restricted Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/universe Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/universe Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/multiverse Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-security/multiverse Sources
Hit http://ubuntu.dcc.fc.up.pt gutsy-proposed/restricted Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-proposed/main Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-proposed/multiverse Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-proposed/universe Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-backports/restricted Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-backports/main Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-backports/multiverse Packages
Hit http://ubuntu.dcc.fc.up.pt gutsy-backports/universe Packages
Fetched 5B in 0s (6B/s)
Reading package lists... Error!
E: Problem parsing dependency Replaces
E: Error occurred while processing libvorbisfile3 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

Note: ubuntu.dcc.fc.up.pt is an official ubuntu mirror, on a portuguese science college.

---

### Post by Pumalite on 2007-09-15
You are using Gutsy, Gutsy is in testing. Try your luck at this sub-forum:Development (Gutsy Gibbon)

---

### Post by NLS___87 on 2007-09-15
[http://ubuntuforums.org/showthread.php?t=551736](http://ubuntuforums.org/showthread.php?t=551736)

---

### Post by Pumalite on 2007-09-15
I guess they weren't much help...uh? Myself, I told you everything I new. Someone will come along that knows more.

---

### Post by NLS___87 on 2007-09-15
> **Pumalite said:**
> I guess they weren't much help...uh? Myself, I told you everything I new. Someone will come along that knows more.

I created that topic after you said me to go to the  Development (Gutsy Gibbon) forum... :)

---

### Post by Pumalite on 2007-09-15
Good for you!

---

