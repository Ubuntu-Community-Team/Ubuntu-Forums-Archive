---
title: "Ubuntu 11.04 update issue"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by cornelius80 on 2011-09-01
Hi all,

Could anyone help me with this update problem, please?
In the command line, I typed "sudo apt-get update" and the following was encountered. 

W: Failed to fetch gzip:/var/lib/apt/lists/partial/id.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources Hash Sum mismatch

Funny thing is, this has not occurred before.

Please help.

Thank you.

regards,
Cornelius:confused:

---

### Post by garvinrick4 on 2011-09-01
```
sudo rm /var/lib/apt/lists/* -vf 
```
```
sudo apt-get clean all 
```
```
sudo apt-get update
```

---

### Post by cornelius80 on 2011-09-03
Thanks garvinrick4,..however, I have encountered another error after entering those commands.

Any ideas?

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://id.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  404  Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by garvinrick4 on 2011-09-03
```
gksudo gedit /etc/apt/sources.list
```
find the offending line. And put a # (comment sign) in front of that line and hit save.
 
#Below is the offending line. 
[[COLOR=#000000]http://id.archive.ubuntu.com/ubuntu/...source/Sources[/COLOR]]("http://id.archive.ubuntu.com/ubuntu/...source/Sources")
 
Then:
```
 
sudo apt-get update

```

---

