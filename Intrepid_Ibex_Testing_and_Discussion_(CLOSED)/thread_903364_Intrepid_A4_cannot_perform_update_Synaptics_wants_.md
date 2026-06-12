---
title: "Intrepid A4 cannot perform update /Synaptics wants to rm 'ubuntu-desktop'"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sofamensch on 2008-08-28
Today was a new update. I installed (Partial Update) it, rebooted. The Update Manager still tells me, that only Partial update is possible.

The Synaptics Package Manager wants to remove 
ubuntu-desktop
update-manager
update-notifier

in exchange for an upgrade of
update-manager-core

Do or Dont?

Thanks, Sofa:guitar:

---

### Post by meborc on 2008-08-28
dont for now... wait a day or two and it will work itself out... keep updating, but dont upgrade

---

### Post by ronacc on 2008-08-28
I did it and I'm still here :lolflag: just make sure those are the only things it wants to remove .

---

### Post by meborc on 2008-08-28
sure, but your system will not upgrade when major changes are made regarding what packages will be included in ubuntu-desktop... thus your system, after upgrading to final, will not be equal to fresh intrepid final install... 

that is all IF there are major changes in the ubuntu-desktop metapackage or not...

i would still wait a few days... all will be well soon ;)

i'm being conservative... i guess your signature says it all :D

---

### Post by Hairy_Palms on 2008-08-28
should all be fine if you let it do what it wants then reinstall ubuntu-desktop and update manager afterwards, this sort of things happened to me a few times

---

### Post by philinux on 2008-08-28
> **sofamensch said:**
> Today was a new update. I installed (Partial Update) it, rebooted. The Update Manager still tells me, that only Partial update is possible.


This is why I never do a partial update.

---

### Post by ronacc on 2008-08-28
I usualy end up with ubuntu-desktop gone anyway because they make it dependent on something I want to get rid of , afterall it is only a "metapackage" ment to drag in a standard set of apps. for me ubuntu-desktop is one of those little annoyances .

---

### Post by Gina on 2008-08-28
I'm getting the same and not doing a partial update.  The new kernel is listed among the unavailable updates but the file size is 2K - evidently the real files are not there.  I can wait - plenty of other things to do :lol:

---

### Post by dawynn on 2008-08-28
Haven't had this particular problem, so I don't know if its applicable in this particular case.

Synaptic wants to make sure everything is in non-broken dependency relationships.  I would assume update-manager is the same way.  So, if adding or upgrading a particular package will break relationships at some point, it will tell you that you must remove them.

Aptitude, on the other hand, is more relaxed about such things.  It recognizes that sometimes you need to upgrade a few different packages in order to get all the relationships working together again.  As long as you're still reviewing packages, it allows relationships to be broken.

So, it is common to find instances where Synaptic may demand packages be removed, but Aptitude will allow you to rearrange things without actually removing packages that you want to keep.

I just did a HH to II transition in Aptitude without removing anything I didn't specifically want.  It may have taken longer than a dist-upgrade, but I didn't have to do much repair after.  Well, the usual cleanup issues -- nVidia, of course -- but no head-scratching wondering which modules got deleted without my knowledge.

Cheers!

---

### Post by BwackNinja on 2008-08-28
Update-manager only does that, update. It will not add extra packages say, when ubuntu-desktop needs them installed to update. That's why whenever something says "partial upgrade" or "some updates cannot be installed" I go to synaptic and select all upgrades (looking closely at what its doing of course). This is why you hear of people telling you to do a "sudo apt-get dist-upgrade".

---

### Post by nanog on 2008-08-28
ubuntu-desktop and its myriad irremovable components is a pain in my nether regions.

---

### Post by dagrump on 2008-08-28
Well the only thing mine wants to remove is console-tools, I tried man console-tools, no entry. I have know idea what is included with console-tools, but I will wait till it doesn't want to remove things.
Basically this install seems to be great if I don't botch crap up, partial upgrades kind of get ugly fast if done w/o caution.

---

### Post by BwackNinja on 2008-08-28
afaik console-tools is replaced by kbd. Look at the description of console tools in synaptic. Its safe to remove as long as you install kbd like it tells you to.

---

### Post by meborc on 2008-08-29
> **ronacc said:**
> I usualy end up with ubuntu-desktop gone anyway because they make it dependent on something I want to get rid of , afterall it is only a "metapackage" ment to drag in a standard set of apps. for me ubuntu-desktop is one of those little annoyances .

i understand totally :)

but you shouldn't advise others to do the same, they might want to end up with a complete intrepid final system...

---

### Post by ronacc on 2008-08-29
I wasn't really advising them to remove it just noting that it would be "safe " to do so , and really anyone that has been testing their way through the alphas will almost certainly end up with a mess of tweaks and workarounds that would be impossible to untangle and so should reinstall after final release for a full standard install .

---

### Post by meborc on 2008-08-29
true... but depending on the way the question was asked by the op, i would not suggest removing ubuntu-desktop :D

anyways, "safe" is a word with many meanings ;)

---

### Post by Gina on 2008-08-29
Academic now - it no longer wants to remove ubuntu-desktop.  OTOH it now won't boot but that's another issue...

---

### Post by ronacc on 2008-08-29
see , I TOLD you to remove ubuntu-desktop :lolflag:
*please note tounge firmly inserted in cheek*

---

### Post by BC7333 on 2008-08-29
Had an issue with 'Partial Update' resolved it with "sudo apt-get dist-upgrade"

---

### Post by ronacc on 2008-08-29
you will find that update manager ,synaptic , apt-get and aptitude all have different ideas about what to "upgrade" .

---

### Post by sofamensch on 2008-08-29
hehe :) ok the truth is that i do feel wiser now, but still not sure what to do :-) I will just leave it like it is for now, runs good for now.

I like my big toy Ubuntu :-)

Thanks for all your response !

---

### Post by sofamensch on 2008-08-31
Edit: After the latest update (with apt-get dist-upgrade) some Xorg configuration must have crashed and it only brings me the console, with some very small resolution, probably 320x260 or less, it doesnt even show me the current input line..

Seems my Nvidia Drivers crashed. Have to work that out for now.

---

