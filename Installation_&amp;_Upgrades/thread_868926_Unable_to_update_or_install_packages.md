---
title: "Unable to update or install packages"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by eagle136 on 2008-07-24
Hi, I guess I have the wrong sources but I am unable to upgrade any pakages on my "edgy" box.  errors:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages
  404 Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages
  404 Not Found [IP: 194.169.254.10 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources
  404 Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
  404 Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages
  404 Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources
  404 Not Found [IP: 194.169.254.10 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages
  404 Not Found [IP: 194.169.254.10 80]

What's gone wrong?

Also if I upgrade to a newer ubuntu release will any of the configuration settings I have be overwritten?
Thanks

---

### Post by Kevbert on 2008-07-24
If you navigate to the web address you'll see that the archive for edgy is no longer there.  The archive only has dapper, feisty and gutsy (old superceded) releases available.  Edgy was removed on 10th June ([[COLOR="Red"]see here[/COLOR]]("http://packages.ubuntu.com/")).

---

### Post by eagle136 on 2008-07-24
That was what I thought ... so how do I update the Edgy distribution?  How do I upgrade to a later version without losing ocnfiguration settings already present?  Is the simple answer to backup, backup and then backup again and then install over the top?
Thanks

---

### Post by GeekBug on 2008-07-28
To update Edgy, you need to edit the file sources.list so that it points to the Ubuntu Old-Release directory.

The sources.list file is located at:

/etc/apt/sources.list

You need to change the file so it looks like this:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-proposed main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-proposed main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-backports main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-backports main restricted


That will point the update-manager software to the right place and allow you to get the final updates for Edgy.

Run the Update Manager and then hit check. Download all updates. After the Update Manager does it's work it will ask you to reset your computer. Go ahead and reset. Re-run Update Manager and hit Check again. No more updates should come up, but a button to upgrade should appear on the top.

If you want to upgrade to Feisty, please continue reading ...

Hit the upgrade button. Do not do anything else after you hit the upgrade button. You need to edit the sources.list again before you continue.

Go ahead and change the sources.list file with this code (I noticed that the author of this thread is from GB, so you will need to change anything us to gp):

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe



Once you have saved this into your sources.list file, go ahead and continue with your upgrade to feisty. It should all be downhill from here.

I'm not good at explaining things with words, so if you need any further help or explanations please let me know.

---

### Post by Sef on 2008-07-28
> The sources.list file is located at:

/etc/apt/sources.list

That should read ```
gksudo gedit /etc/apt/source.list
```

---

