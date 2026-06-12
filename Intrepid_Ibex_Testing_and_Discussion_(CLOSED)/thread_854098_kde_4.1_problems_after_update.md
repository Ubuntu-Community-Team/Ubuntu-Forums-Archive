---
title: "kde 4.1 problems after update"
date: 2008-07-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jbernardo on 2008-07-09
Hi,
I´ve updated from hardy with kde 4.1 beta 2 to intrepid. I had some problems (kismet had a maemo reference in postinst, etc.) but managed to upgrade everything and clean up the ppa packages. But now, I have three problems with kde:
- kopete doesn' t show, either as a window or in system tray;
- system tray shows transparent boxes where the app icons should be, making me guess which app is which "hole" in the panel;
- calling a app with kdesudo gives me a xauth error ('couldn't query security extension on display ":0"').

Any one else seeing these? Or are they artifacts of the ppa->intrepid kde migration?

---

### Post by xebian on 2008-07-09
> **jbernardo said:**
> Hi,
I´ve updated from hardy with kde 4.1 beta 2 to intrepid. I had some problems (kismet had a maemo reference in postinst, etc.) but managed to upgrade everything and clean up the ppa packages. But now, I have three problems with kde:
- kopete doesn' t show, either as a window or in system tray;
- system tray shows transparent boxes where the app icons should be, making me guess which app is which "hole" in the panel;
- calling a app with kdesudo gives me a xauth error ('couldn't query security extension on display ":0"').

Any one else seeing these? Or are they artifacts of the ppa->intrepid kde migration?

IMHO it's best to start fresh with Intrepid especially if you use KDE.  The repos are in a big mess, and needs a huge cleanup.  The Hardy packages has the -kde4 suffix and were merged into Intrepid before the new packages without the -kde4 were put in.  Now you have all sorts of dependency hell.

---

### Post by caryb on 2008-07-09
> The repos are in a big mess, and needs a huge cleanup. The Hardy packages has the -kde4 suffix and were merged into Intrepid before the new packages without the -kde4 were put in. Now you have all sorts of dependency hell.

I fully agree I had the eerups with all the errors & broken packages surrounding the Hardy kde4 hangovers! the best thing I did was to rebuild my Pc


Cary

---

### Post by jbernardo on 2008-07-09
I think I' ll take the easiest path - remove all kde stuff and install kubuntu-desktop again. If that doesn't work, then booting from the install CD and doing a fresh install might be the best option.

---

### Post by Seisen on 2008-07-09
> **jbernardo said:**
> Hi,
I´ve updated from hardy with kde 4.1 beta 2 to intrepid. I had some problems (kismet had a maemo reference in postinst, etc.) but managed to upgrade everything and clean up the ppa packages. But now, I have three problems with kde:
- kopete doesn' t show, either as a window or in system tray;
- system tray shows transparent boxes where the app icons should be, making me guess which app is which "hole" in the panel;
- calling a app with kdesudo gives me a xauth error ('couldn't query security extension on display ":0"').

Any one else seeing these? Or are they artifacts of the ppa->intrepid kde migration?

I have the same problem with kdesudo giving the xauth error but I upgraded without adding kde4 packages from the PPA in Hardy.

---

### Post by caryb on 2008-07-09
Because Hardy has kde3 & kde4 packages the packages for kde4 have to be delimited as kde4 packages, In Intrepid kde4 is default they don't have to to be renamed & by default are called by proper names. At some time you will have to get rid of the .kde4 packages in Intrepid & while you have conflicting distro packages you will run into problems as I did. At some time you will have to bite the bullet & fix the problem it may as well be earlier than later as reporting bugs will be difficult for you as you won't know if they are generic problems or isolated to you.



2c Cary

---

### Post by jbernardo on 2008-07-10
Well, I purged and reinstalled all kde and kubuntu packages and associated libs, and still have two of the problems - adept* is broken, and the icons in the system tray are still corrupt. I fixed kopete by removing the kopeterc file.

---

### Post by daflame on 2008-08-03
> **jbernardo said:**
> Well, I purged and reinstalled all kde and kubuntu packages and associated libs, and still have two of the problems - adept* is broken, and the icons in the system tray are still corrupt. I fixed kopete by removing the kopeterc file.

Same here.  I also did everything in my power to set things straight, but I suspect that there is a config blowing everything up still lingering somewhere.  I wish I knew where.

Hmmm...  I think I may have found out a few answers.  If you use dpkg-divert --list at a command prompt you may find a few broken diversions.  I found a couple, but I'm not sure that fixes anything though.  It did let me reinstall my broken libgl1-mesa-glx.  If I remove and readd my system tray now the icons reappear, but I'm not sure that will help me on a reboot.  Here's hoping.

---

### Post by caryb on 2008-08-03
I tried to install kde4-core but there are missing dependencies & I think that may be the root to our problem.


Cary

---

### Post by caryb on 2008-08-03
After yesterdays upgrades I lost my utilities on the taskbar, Batt monitor, network mangler etc


Cary

---

### Post by Kevbert on 2008-08-03
> **caryb said:**
> After yesterdays upgrades I lost my utilities on the taskbar, Batt monitor, network mangler etc


Cary
Same problem here.  Also I've made a copy of all the terminal messages displayed for the upgrade from kernel -4 to -5 (attached).  The seems to be one or two problems with the upgrade in Kubuntu, including 'unable to delete read only files.  Sorry I can't be more specific as I can't open the file in Kate or OpenOffice after the reboot - guess it's time to re-install from scratch.
In Ubuntu it seems that some of the updates are unavailable (as I've been getting http 404 errors) switching servers seems to only partially help and the number of files seems to be inconsistent (I've tried Main, GB and US servers).  It may just be that some haven't been updated yet.

---

### Post by Kevbert on 2008-08-03
Me again.  Well that was good.  I couldn't even upload the attachment (though it looked as if it uploaded OK ???)  The text file was too big >19.5kB so I've had to tar it.

The errors include;
```
Unpacking replacement kdelibs5-data ...                                         
Unknown media type in type 'all/all'
```
and 
```
rm: cannot remove `rfcomm0-': Read-only file system            
mknod: `rfcomm0-': Read-only file system                       
makedev rfcomm0 c 216 0 root dialout 0660: failed

```

These errors occur a large number of times.
Should I raise a bug report or two.

---

### Post by stari4ek on 2008-08-04
after today's update of kde4libs I can't start any kde4 programs. ktorrent, gwenview...

They hangs somewhere in infinite loop with 100% processor load.

---

