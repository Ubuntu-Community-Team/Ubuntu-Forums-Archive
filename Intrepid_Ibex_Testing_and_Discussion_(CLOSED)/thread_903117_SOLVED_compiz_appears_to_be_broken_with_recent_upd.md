---
title: "SOLVED: compiz appears to be broken with recent updates"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mattisking on 2008-08-28
Just a heads up... but the last set of updates I installed today, including the new kernel, appears to have killed my ability to run compiz for the moment with my ATI X800 All in Wonder (open drivers).

Update: The problem has been resolved by tonight's updates. Thanks.

---

### Post by jbernardo on 2008-08-28
Might not be the kernel, but rather the changes to X. I've booted both into 2.6.27 and 2.6.26 on my acer aspire one since updating 1 hour ago, and even though I get the login dialog, kde4 isn't able to present the desktop, showing either "noise" or the background. Looks like something was broken either in compositing or something related.

Edit: from the list of installed packages, I'd say the breakage is probably in the libglu1/libgl1-mesa* packages. I am going to download and install the previous versions (~rc3) to test this.

---

### Post by jbernardo on 2008-08-28
Confirmed, downgrading to the ~rc3-1ubuntu4 versions of libgl1-mesa-glx, libgl1-mesa-dri and libglu1-mesa gives me back kde4 desktop, and will probably fix compiz.

As posted below by hardhu and mattisking, you can either get them from /var/cache/apt/archive, or if they're not there download the packages from [http://archive.ubuntu.com/](http://archive.ubuntu.com/). Then you need to install them with "sudo dpkg -i libg*deb" inside the directory where you put the packages.

---

### Post by hardhu on 2008-08-28
> **jbernardo said:**
> Confirmed, downgrading to the ~rc3-1ubuntu4 versions of libgl1-mesa-glx, libgl1-mesa-dri and libglu1-mesa gives me back kde4 desktop, and will probably fix compiz.


Thanks a lot for your post, I also had the same problem with kde4 desktop and I solved following your suggestion. May I ask you how did you find that the culprits were exactly those packages? And how did you manage the downgrade (I downloaded the older versions of the packages from archive.ubuntu.com and installed them manually using dpkg).

---

### Post by jbernardo on 2008-08-28
Well, since it affected compiz and kde4, I thought first it might be either X changes or GL/mesa changes. As two different graphic adapters were involved, at least (mine is a intel), either the changes were in X core or were in GL/mesa. After that, I checked which packages I had updated today (listed /var/cache/apt/archives in date order) and found out these. Downloaded them from archive.ubuntu.com and installed using dpkg, as you did, as they weren't in the archives dir.
Quite simple, as there were only a handful of updates today, and the other major update, the kernel, could be testes by booting into the older kernel.

---

### Post by doktormiod on 2008-08-28
What repository do you use? I've got the same problem but, unfortunately I can't change the package version, there's only "7.1-1ubuntu1" :/

---

### Post by mattisking on 2008-08-28
> **doktormiod said:**
> What repository do you use? I've got the same problem but, unfortunately I can't change the package version, there's only "7.1-1ubuntu1" :/
To downgrade a package, it's usually easiest to go to your /var/cache/apt/archives and do a directory listing. Then you can use dpkg -i <filename> to install the version of the old package if it's still there. It usually will be unless you've taken the time to clean out your archive (apt-get clean)

---

### Post by doktormiod on 2008-08-28
Fortunately the packages were still there, thanks for help :-)

---

### Post by hardhu on 2008-08-28
> **doktormiod said:**
> Fortunately the packages were still there, thanks for help :-)

If you couldn't find the packages in the cache archive, you can find older version of them at [http://archive.ubuntu.com/](http://archive.ubuntu.com/)

---

