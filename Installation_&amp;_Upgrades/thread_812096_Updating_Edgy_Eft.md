---
title: "Updating Edgy Eft"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by safetycritical on 2008-05-29
I'm trying to update my AMD64 Edgy Eft installation (I want to update to the latest version of Unbuntu) but I get the following message when I try and update
[COLOR="Red"]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.12r-11ubuntu2.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.12r-11ubuntu2.1_amd64.deb)
  404 Not Found [IP: 91.189.88.46 80][/COLOR]

My Source.List file is 
[COLOR="Green"]## Uncomment the following two lines to fetch updated software from the network

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted
## deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe


## deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
[/COLOR]

Hope you can help I don't want to have to do a clean install !!!

---

### Post by logos34 on 2008-05-29
you can't update to Hardy from edgy.  Fresh install is the only way (unless you want to upgrade one release at a time -- edgy-->feisty feisty-->gutsy gutsy--hardy

---

### Post by safetycritical on 2008-05-29
I'm prepared to go through the edgy-->feisty feisty-->gutsy gutsy--hardy path. It's just that I can't update "edgy"!!

---

### Post by hal8000 on 2008-05-29
Try changing the repository for a different server. A 404 or file not found error may just mean that your particular repo has not been updated.

---

### Post by newlinux on 2008-06-06
I'm having similar problems... did you find a repo that works? I can't update my edgy machines.

---

### Post by avtolle on 2008-06-06
> **safetycritical said:**
> I'm prepared to go through the edgy-->feisty feisty-->gutsy gutsy--hardy path. It's just that I can't update "edgy"!!
[https://help.ubuntu.com/community/UpgradeNotes#head-4b642102f96e5f9788ca164311d65cd2caa5df44](https://help.ubuntu.com/community/UpgradeNotes#head-4b642102f96e5f9788ca164311d65cd2caa5df44) and the links therein should get you going. HTH.

---

### Post by Slim Odds on 2008-06-06
Edgy has expired!!

[http://ubuntuforums.org/showthread.php?t=817409](http://ubuntuforums.org/showthread.php?t=817409)

I think there needs to be a sticky about this. It just keeps coming up over and over.

---

### Post by avtolle on 2008-06-06
> **Slim Odds said:**
> Edgy has expired!!

[http://ubuntuforums.org/showthread.php?t=817409](http://ubuntuforums.org/showthread.php?t=817409)

I think there needs to be a sticky about this. It just keeps coming up over and over.
Maybe there needs to be a sticky on this; however, it seems the OP has figured this out, and wants to upgrade.

---

### Post by logos34 on 2008-06-06
> **Slim Odds said:**
> 
__________________
24 beers in a case, 24 hours in a day. Coincidence? I think not!

hah!

Definitely not! :)

---

### Post by newlinux on 2008-06-06
> **Slim Odds said:**
> Edgy has expired!!

[http://ubuntuforums.org/showthread.php?t=817409](http://ubuntuforums.org/showthread.php?t=817409)

I think there needs to be a sticky about this. It just keeps coming up over and over.

That's actually what I thought, but believe it or not, my searches didn't turn up a thread on it, so I wanted to make sure. When I upgrade, I'll probably wipe clean and start over.

Thanks

---

### Post by Kevbert on 2008-06-06
If you want to download any of the Ubuntu releases you can find them [here]("http://releases.ubuntu.com/").  Now going to look for the old repos. Individual packages can be found [here]("http://packages.ubuntu.com/").

---

