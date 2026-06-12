---
title: "Lotus notes dependencies issues on Jaunty"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by khm on 2009-03-19
Hi,

I just upgraded to Jaunty and I'm having problems installing Lotus Notes 8.  I have a debian package for it, but it's saying that it depends on 

Error: Dependency is not satisfiable: libgnome-desktop-2 (>= 2.11.1)

I know I can force the install, but apt won't like it and I won't be able to install other packages or updates. So is there a way to fix this?

Thanks!

---

### Post by Bachstelze on 2009-03-19
The name of this package changed in Jaunty (it is now called [font="monospace"]libgnome-desktop-2-11[/font]). Only thing you can do is modify your package so it depends on the new one.

---

### Post by khm on 2009-03-19
> **HymnToLife said:**
> The name of this package changed in Jaunty (it is now called [font="monospace"]libgnome-desktop-2-11[/font]). Only thing you can do is modify your package so it depends on the new one.

How does one change a package's dependencies?

---

### Post by khm on 2009-03-23
...anyone?

---

### Post by CRCarl on 2009-03-25
It's not too hard. 

1. Unpack the .deb (It's just an archive) 
```
 ar -x packagename.deb
```

2. Unpack the control.tar.gz file
```
control.tar.gz
```

3. Find the file named control. In the file you will see the depends line. Modify that, replacing libgnome-desktop-2 (>= 2.11.1) with libgnome-desktop-2-11. 

4. Pack everything back up with 
```
dpkg -b directory packagename.deb
```

Easy peaze. Really good article here - [http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html)

---

### Post by chrisccoulson on 2009-03-25
libgnome-desktop-2 wasn't just renamed to libgnome-desktop-2-11 for fun. It was renamed because this library underwent a SO version change during the Jaunty cycle. This means that applications built against the old version need to be rebuilt against the new version to work properly. Lotus notes depends on that particular SO version for a very good reason. Manually changing the dependency to depend on the newer SO version (as advised by others) is really not a very good idea, and may mean that the application experiences unexpected behaviour, random crashes, or may not even work at all.

The safest workaround at this stage is to manually install libgnome-desktop-2 from Intrepid. This should be installable with no dependency issues, and should install alongside libgnome-desktop-2-11 without any conflicts (libgnome-desktop-2 will remain installed on Jaunty machines upgraded from Intrepid anyway, as the upgrade won't remove older versions of libraries that you have installed).

---

### Post by chrisccoulson on 2009-03-25
I suspect that this actually needs the Hardy version of libgnome-desktop-2

---

### Post by olivesandtrees on 2009-03-25
I have installed Lotus Notes 8.5 on Jaunty and I'm not getting any dependency errors, but Lotus Notes seems to freeze up after opening.  It just sits there using about 20% of my CPU and none of the tabs ever open.

After reading a little more on this it may have to do with certain desktop visual effects or perhaps Compiz?  I didn't see anything really specific.

Any help on this issue would be appreciated.

---

### Post by CRCarl on 2009-03-25
I think we can all agree that stuff like this happens with an alpha. The best mid to long term solution is likely to be opening a ticket with IBM to get a Jaunty supported release. 

In the mean time I don't see any harm in experimenting. Could help make the ticket to IBM more informative. 

We have all soft linked a *.so.4 file to *.so.2 (or whatever) when an application has an unresolvable dependency, sometime it works, sometime it doesn't.

---

### Post by ktp on 2009-03-25
Been running Notes in 64-bit with no issues.

---

### Post by chrisccoulson on 2009-03-26
> **CRCarl said:**
> We have all soft linked a *.so.4 file to *.so.2 (or whatever) when an application has an unresolvable dependency, sometime it works, sometime it doesn't.

Again, the filenames changed because the library versions are incompatible with each other. Sym-linking is not a very good thing to do, is quite wreckless, and not the sort of advice that you should be giving out on this forum. If an application needs an older version of a library, it is much safer to install the older version. As I pointed out earlier, tha packaging of libraries when the SO version number changes is handled in such a way that you can install multiple versions of the library alongside each other, without conflicts. (hence the *.so.x and *.so.y naming of the SO files. The deb package name is generally named to reflect the SO version number too)

I tried installing Hardy's libgnome-desktop-2 on Jaunty last night. It installs with no dependency problems and no conflicts on libgnome-desktop-2-11.

---

### Post by mariner09 on 2009-03-26
I've been running Notes 8.5.1 on Jaunty for a couple of months now with no issues.

When I tried installing with a single meta-package, it complained about the dependency, but when I installed the 5 individual packages they were fine.

I use compiz and Notes is fine.  You need to make sure you have ms fonts and luxi fonts installed in order for everything to render properly.

---

### Post by carrozza on 2009-03-30
> **mariner09 said:**
> I've been running Notes 8.5.1 on Jaunty for a couple of months now with no issues.

When I tried installing with a single meta-package, it complained about the dependency, but when I installed the 5 individual packages they were fine.

I use compiz and Notes is fine.  You need to make sure you have ms fonts and luxi fonts installed in order for everything to render properly.

Hi, where did you find version 8.5.1 ?

I found only 8.5 trial for Linux.

I'll try to find the fonts you mentioned, too, because I see everything monospaced right now. :-)

---

### Post by hotstovejer on 2009-04-17
Totally. Where are you guys getting the .deb from? Or are you compiling from source?

Thanks!

Jeremy

---

### Post by ktp on 2009-04-17
> **hotstovejer said:**
> Totally. Where are you guys getting the .deb from? Or are you compiling from source?

Thanks!

Jeremy

I think with 8.5 maybe 8.0 it is packaged as deb and rpm.

---

### Post by ktp on 2009-04-17
> **carrozza said:**
> Hi, where did you find version 8.5.1 ?

I found only 8.5 trial for Linux.

Most likely business partner.

> **carrozza said:**
> 
I'll try to find the fonts you mentioned, too, because I see everything monospaced right now. :-)


```
sudo apt-get install ttf-xfree86-nonfree
```

Recently i have been using androids font and love it.

```
sudo apt-get install ttf-droid
```

[http://www.stefanoforenza.com/get-androids-fonts-on-ubuntu-how-to/](http://www.stefanoforenza.com/get-androids-fonts-on-ubuntu-how-to/)

---

