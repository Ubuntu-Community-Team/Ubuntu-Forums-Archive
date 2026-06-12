---
title: "Could Not Download ALL Repository Indexes"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by jleach87 on 2008-03-26
Alight, last night I installed unbuntu 7.10 as a dual-boot on an HP dv1000 also running XP pro.

Everything works great except for being able to download ANY repository updates.  I have spent about 2 hours reading threads and haven't been able to find anything that would solve my problem.

I have changed the server in Software Sources to the main server. Everyone of the downloads fails.  I don't understand why, I can copy and paste the link into a web browser and the directory comes up as it should.

here is my sources.list contents....any help would be greatly appreciated...





# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

---

### Post by Oldsoldier2003 on 2008-03-28
System>Administration>Software Sources
Then check the first four repos on the front tab, then set your download source.

then in a terminal
```

sudo apt-get update
sudo apt-get upgrade
```

paste any error messages you receive and we'll try to get you sorted out

---

