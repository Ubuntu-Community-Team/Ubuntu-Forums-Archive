---
title: "What is HAL's replacement?"
date: 2009-01-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-18
Hi all, 
      I heard there was a move to replace HAL? I had come across the same on the forum somewhere but have forgotten the same? What is it ?

---

### Post by Neon Lights on 2009-01-18
I believe DeviceKit is set to replace HAL, though I may just be confusing everything.

---

### Post by talkingwires on 2009-01-18
Dave. HAL is being deactivated and manual control will revert back to Dave.

*"Oh my god, it's full of stars!"*

---

### Post by ronacc on 2009-01-18
I'm sorry  I can't do that  Dave.

---

### Post by gnomeuser on 2009-01-18
[DeviceKit](http://lists.freedesktop.org/archives/hal/2008-May/011560.html) is the HAL replacement.

David Zeuthern' DeviceKit/DeviceKit-disks presentation slides:
[http://people.freedesktop.org/~david/devkit-presentation-davidz-aug2008.pdf](http://people.freedesktop.org/~david/devkit-presentation-davidz-aug2008.pdf)

Richard Hughes' DeviceKit-power presentation slides:
[http://lists.freedesktop.org/archives/devkit-devel/attachments/20080819/2a77ebbc/attachment-0001.pdf](http://lists.freedesktop.org/archives/devkit-devel/attachments/20080819/2a77ebbc/attachment-0001.pdf)

---

### Post by bash on 2009-01-18
Hey gnomeuser, since you normally got the magic elves getting you the in-the-know info, I remember reading (I think it was hughsie saying) that they changed from DeviceKit replacing HAL completly, to DK just taking over some jobs from HAL, while HAL will be kept around since it still has it use cases in the other areas. 

You know more about that or in general maybe have a link to what the mid-/long-term play is for DK <-> HAL?

---

### Post by chrisccoulson on 2009-01-18
DeviceKit is in universe for Jaunty. Some Gnome stuff already depends heavily on DeviceKit (eg, gnome-power-manager 2.25.x). I think that the plan is to package this in a PPA somewhere for Jaunty and keep the old gnome-power-manager for this release. There will eventually be a transition to DeviceKit, but probably not in a single release. A lot of stuff depends on HAL at the moment.

---

### Post by gnomeuser on 2009-01-18
> **bash said:**
> Hey gnomeuser, since you normally got the magic elves getting you the in-the-know info, I remember reading (I think it was hughsie saying) that they changed from DeviceKit replacing HAL completly, to DK just taking over some jobs from HAL, while HAL will be kept around since it still has it use cases in the other areas. 

You know more about that or in general maybe have a link to what the mid-/long-term play is for DK <-> HAL?

HAL and DeviceKit can been installed in parallel which is important to facilitate a transitioning as apps are being ported. Key enterprise distros will still be supporting HAL for many years to come so it is not going away anytime soon in that regard. However the plan is so far as I am informed to switch to 100% DeviceKit and obsolete HAL eventually, it will happen over a long time though, many apps to convert and some design to finalize. Original estimates called for this to be done by F11, that is likely not going to be enough time, F12 is more likely.

---

### Post by cb951303 on 2009-01-18
whats with all the *kit names? webkit, policykit, packagekit and now devicekit?

---

### Post by lswb on 2009-01-18
> **cb951303 said:**
> whats with all the *kit names? webkit, policykit, packagekit and now devicekit?

Yeah, it sounds like something you have to put together yourself, not something that works out of the box.

---

### Post by Gina on 2009-01-18
> **ronacc said:**
> I'm sorry  I can't do that  Dave.I could just hear HAL's voice when I read that :lolflag:

---

### Post by DavidONE on 2009-01-18
> **ronacc said:**
> I'm sorry  I can't do that  Dave.

That's *my* line. :)

---

### Post by bash on 2009-01-18
> **chrisccoulson said:**
> DeviceKit is in universe for Jaunty. Some Gnome stuff already depends heavily on DeviceKit (eg, gnome-power-manager 2.25.x). I think that the plan is to package this in a PPA somewhere for Jaunty and keep the old gnome-power-manager for this release. There will eventually be a transition to DeviceKit, but probably not in a single release. A lot of stuff depends on HAL at the moment.

As far as DK-power and the new g-p-m is concerned, the plan so far seems to be to keep it around in a special PPA for Jaunty and to integrate it as default in Jaunty+1. Hopefully DK-disks and the new gnome-partition-utility will also be ready by then.

> **gnomeuser said:**
> HAL and DeviceKit can been installed in parallel which is important to facilitate a transitioning as apps are being ported. Key enterprise distros will still be supporting HAL for many years to come so it is not going away anytime soon in that regard. However the plan is so far as I am informed to switch to 100% DeviceKit and obsolete HAL eventually, it will happen over a long time though, many apps to convert and some design to finalize. Original estimates called for this to be done by F11, that is likely not going to be enough time, F12 is more likely.

Ah ok. What I see of DK so far (especially DK-disks and -power) seems like a neat thing to me. 

> **cb951303 said:**
> whats with all the *kit names? webkit, policykit, packagekit and now devicekit?

Except for Webkit all the other *kits are RedHat projects (or at least with one or more lead-devs connected to RedHat). So maybe it's a new trend over there ;)

Oh and you forget the new ConsoleKit.

---

### Post by Slug71 on 2009-01-18
Wow, we're starting to use a few stuff from Fedora/Red Hat.
Not that it's theirs but they use it - Packagekit
Theirs                               - Plymouth(9.10)
                                     - VolumeControl
                                     - Devicekit
Hopefully we'll get Anaconda too.

@Gnomeuser, 
Do you know if Fedora will start using the Smart Package Manager backend for Packagekit in F11/F12?

---

### Post by lswb on 2009-01-18
> **Slug71 said:**
> Wow, we're starting to use a few stuff from Fedora/Red Hat...


try "grep -r redhat /etc 2>>/dev/null" sometime.

ubuntu uses LOTS of stuff that was developed/maintainted by fedora.

---

### Post by Slug71 on 2009-01-18
> **lswb said:**
> try "grep -r redhat /etc 2>>/dev/null" sometime.

ubuntu uses LOTS of stuff that was developed/maintainted by fedora.

Thanks,
Wow, definitely more than i thought!

---

### Post by gnomeuser on 2009-01-18
> **Slug71 said:**
> 
Do you know if Fedora will start using the Smart Package Manager backend for Packagekit in F11/F12?

No, and I am not aware of any plans of ever doing this. You can though install it from our repos so I guess you could use it by choice (at least I see the packagekit-smart package in the official repos).

that being said, there isn't a roadmap for many versions ahead. If someone was to write up the feature and put the effort into bringing it to fruition then that feature could be proposed to our engineering commitee and it would be accepted or rejected based on evaluation. So put the effort into making this happen and give good rational as to why this would benefit Fedora longterm and it happens..

---

### Post by Slug71 on 2009-01-18
> **gnomeuser said:**
> No, and I am not aware of any plans of ever doing this. You can though install it from our repos so I guess you could use it by choice (at least I see the packagekit-smart package in the official repos).

that being said, there isn't a roadmap for many versions ahead. If someone was to write up the feature and put the effort into bringing it to fruition then that feature could be proposed to our engineering commitee and it would be accepted or rejected based on evaluation. So put the effort into making this happen and give good rational as to why this would benefit Fedora longterm and it happens..

Thanks,
Was just curios since you guys are always keen to adopt new things and i got the impression from Smarts website and seeing all the people from different projects/distros involved that it might become the cross-distro backend like Packagekit is on its way to become the cross-distro frontend. Specially since Packagekit which is fairly new itself already has backend support for another new project.

---

### Post by Slug71 on 2009-01-18
Does anyone know if Devicekit will be installed by default for Jaunty?

I installed it earlier and it hasnt broken anything which has got to be a good thing.

---

### Post by bash on 2009-01-19
[quote=Slug71]Does anyone know if Devicekit will be installed by default for Jaunty?[/quote]

As far as DK-power and the new g-p-m is concerned, the plan so far seems to be to keep it around in a special PPA for Jaunty and to integrate it as default in Jaunty+1. Hopefully DK-disks and the new gnome-partition-utility will also be ready by then.

---

### Post by Slug71 on 2009-01-19
> **bash said:**
> As far as DK-power and the new g-p-m is concerned, the plan so far seems to be to keep it around in a special PPA for Jaunty and to integrate it as default in Jaunty+1. Hopefully DK-disks and the new gnome-partition-utility will also be ready by then.

Thanks,
DK and DK-power is in Synaptic which is where i installed it from but noticed DK-disks was missing.

---

### Post by forcecore on 2009-01-21
DK must be in 9.04, it is quite critical in some cases.

---

### Post by chrisccoulson on 2009-01-21
> **forcecore said:**
> DK must be in 9.04, it is quite critical in some cases.

Critical for what? DeviceKit is not ready to be shipped with a stable distribution yet, and won't be for some time.

---

