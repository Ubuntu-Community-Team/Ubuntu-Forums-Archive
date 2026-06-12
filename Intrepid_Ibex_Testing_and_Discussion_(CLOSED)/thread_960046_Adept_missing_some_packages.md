---
title: "Adept missing some packages"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jynyl on 2008-10-27
The Adept manager in Kubuntu 8.10 rc only shows some packages.
For example, a search on kscreensaver returns "no matches found", yet Synaptic finds a few matching this.
[IMG]http://www.hewett.co.nz/junk/AdeptMissingSome.png[/IMG]

Is this a bug in Adept, or do I need to adjust something somewhere?


TIA

Peter

(Fresh install of Kubuntu 8.10 rc, updates to 27 Oct.)

---

### Post by TheUnabeefer on 2008-10-27
To tag onto this thread, I am not fond of the lack of alphabetization when browsing packages.  It's hard to find similar or related packages if it's scattered in no particular order.

I think I like the older Adept better.

---

### Post by xerosis on 2008-10-27
You probably need to do a 'sudo update-apt-xapian-index'

---

### Post by Joe on 2008-10-27
This was definitely a bug in the last beta release and I remember seeing a bug report for it although I can't seem to find it now.  I thought it got fixed in one of the updates between the last beta release and the RC release though.

---

### Post by dualscreenman on 2008-10-27
That's because that is Adept Installer, which installs applications. kscreensaver is a package, and was never installable by Adept Installer. You need to use Adept Manager for package managing.

---

### Post by jynyl on 2008-10-28
> **dualscreenman said:**
> That's because that is Adept Installer, which installs applications. kscreensaver is a package, and was never installable by Adept Installer. You need to use Adept Manager for package managing.

Thanks.
It isn't obvious that there are 2 different packages; Adept Installer and Adept Manager.  And I can't find Adept Manager anywhere in Kmenu (although it does show up if you use the search field in Kmenu).  Adept Installer appears twice, once under the Computer tab and also under the Applications tab.

Certainly a trap for young players.

---

### Post by dualscreenman on 2008-10-28
That is strange, Adept Manager shows up in the System submenu for me.

---

### Post by caryb on 2008-10-28
It is really sad when apps are updated & loose functionality, I would run adept 2 if it would run on my machine. I am forced to use Synaptic because of the deficiencies of v3 adept. I don't know if it filters or is just lame but I find the search in the new adept to be problematic.




Cary

---

### Post by jynyl on 2008-10-29
> **dualscreenman said:**
> That is strange, Adept Manager shows up in the System submenu for me.

Thanks, where does it appear?
I can find a "Package Manager" under Applications > System, but can't find "Adept Manager" anywhere.

The point is that Adept Installer appears to be the application we should use (it appears conspicuously twice in Kmenu), but there is no indication that it is only showing part of the story, or that there is another, full feature tool available.

---

