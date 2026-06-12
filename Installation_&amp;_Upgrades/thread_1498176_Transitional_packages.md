---
title: "Transitional packages"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by SoFl W on 2010-05-31
In the Synaptic Package manager I will come across packages that will have some variation of "This is a transitional package, it is safe to remove" 

I never knew if it was really safe to remove the packages or not and I am unsure if there is a safe way to remove packages that are no longer needed.  Today inside the Synaptic Package manager I clicked to remove a transitional package and it said it would also remove "ubuntu-desktop and "ubuntu-studio-desktop"  This makes me think that you shouldn't remove these packages where the package descriptions say "Safe to remove"

Is there a safe command line option to remove all transitional packages?
Is it really safe to do so? 
Should I just leave it alone... "If it isn't broke don't fix it"?

---

### Post by arrange on 2010-05-31
I think a transitional package can be safely removed UNLESS 
 * another package depends on it
 * another script checks for its existence in the system (though i've seen such scripts (generally), they are not standard IMO)

If unsure, keep them. They do no harm and occupy tiny space.

---

### Post by SoFl W on 2010-05-31
Okay thank you.  That is what I have been doing and after I received that warning about removing the desktop I figured it was best.  Still wondering why it would say it was safe to remove.

---

### Post by arrange on 2010-06-01
> **SoFl W said:**
> ...  Still wondering why it would say it was safe to remove.
As I don't know which packages you are talking about I can't say but the maintainer might not be aware that "his" package was included in *ubuntu-desktop* as a dependency.

---

### Post by SoFl W on 2010-06-01
It was "sreadahead" that said it would also remove ubuntu-desktop.

---

### Post by arrange on 2010-06-01
If you are interested, you can post here the output of```
sudo apt-get -o Debug::pkgDepCache::Marker=true -o Debug::pkgProblemResolver=true remove sreadahead
```When it asks you for confirmation of the removal say **no**, but copy the output here. Plus your release of Ubuntu.

---

### Post by SoFl W on 2010-06-01
Tghank you arrange, out of curiosity I went ahead and did what you asked.


**ubuntu studio 9.10**
```
$ uname -a
Linux computer_name-Udesktop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux

$ sudo apt-get -o Debug::pkgDepCache::Marker=true -o Debug::pkgProblemResolver=true remove sreadahead
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  MarkDelete sreadahead < 1:0.90.3-2 > ( admin ) FU=1
Starting
Starting 2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on sreadahead
  Considering sreadahead 10002 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change sreadahead
  MarkDelete ubuntu-desktop < 1.175 > ( metapackages ) FU=1
Investigating ubuntustudio-desktop
Package ubuntustudio-desktop has broken Depends on sreadahead
  Considering sreadahead 10002 as a solution to ubuntustudio-desktop 0
  Removing ubuntustudio-desktop rather than change sreadahead
  MarkDelete ubuntustudio-desktop < 0.64 > ( universe/metapackages ) FU=1
Done
The following packages were automatically installed and are no longer required:
  melt libmlt++2 kdenlive-data libmlt-data libmlt1
Use 'apt-get autoremove' to remove them.
[B]The following packages will be REMOVED:
  sreadahead ubuntu-desktop ubuntustudio-desktop[/B]
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 139kB disk space will be freed.
```

---

### Post by SoFl W on 2010-06-01
I did the auto remove and received this error:  
```
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kdenlive-data libmlt++2 libmlt-data libmlt1 melt
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 15.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 249355 files and directories currently installed.)
Removing kdenlive-data ...
Removing libmlt++2 ...
Removing libmlt-data ...
Removing melt ...
Removing libmlt1 ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...

```I am using gnome, but a while ago, I did install kdenlive.  I am sure I have used autoremove recently, and when I believe when I upgraded from ubuntu to ununtu studio is when kdenlive disappeared.  (I had a lot going on in my life at the end of last year, so some details are fuzzy)  
I originally installed 9.4, I believe my next step was upgrading to ubuntu studio (not a clean install) and then upgrading to 9.10 (again not a clean install)

I see other people complaining about the "Unknown media type in type" error and from what I briefly read it is a bug.

---

### Post by arrange on 2010-06-01
*ubuntu-desktop* in 9.10 depends on *sreadahead*, which in turn was changed into a metapackage, but only in the *karmic-updates* repository. So I guess it is a tiny little bug that it was marked to be "safely removable". :)

---

### Post by SoFl W on 2010-06-01
Thanks.  I am glad I didn't try to fix what was working.

---

