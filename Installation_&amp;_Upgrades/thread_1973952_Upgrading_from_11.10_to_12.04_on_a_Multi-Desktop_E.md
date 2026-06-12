---
title: "Upgrading from 11.10 to 12.04 on a Multi-Desktop Environment System"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by StewartM on 2012-05-05
Greetings,

I have two computers, a desktop with 10.04 and a laptop with 11.10. The laptop (11.10) has the following desktop environments installed:

1) Unity
2) GNOME3 Classic Fallback
3) GNOME3
4) Lubuntu/LXDE 
5) Kubuntu
6) Enlightenment

It was originally a "pure" Ubuntu machine until 11.10 but I installed the other DEs when playing around to see what's available. Right now I'm using mostly KDE for actual use and Enlightenment for sysadmin stuff, though I do use Unity or GNOME 3 on occasion.

The machine boot splash says it's it's Ubuntu, but that's because after I installed the complete Kubuntu package I changed the splash screen back to the Ubuntu splash as I liked that splash screen better. I use GDM as the login screen as I liked that the best between KDM and LightDM.

So--when I push the "upgrade" button, what system(s) will I end up with? I supposed I could end up with Ubuntu or Kubuntu but I'm not sure. Or would I get updates for everything I have currently (which would be the ideal situation).

Does anyone know? Is there any way to find out? The upgrade selection says "Welcome to Ubuntu 12.04" which makes me think it will be Ubuntu but in KDE Muon Center tells me that "A new version of Kubuntu is available".

-StewartM

---

### Post by grahammechanical on 2012-05-05
The developers cannot know every variation that every user does to the OS. The developers design and test the upgrade from a default install of one version of Ubuntu to the next version.

I shared in testing the upgrade path from 10.04 and 11.10 to 12.04 but that was from default installs of 10.04 and 11.10 and not for any of the flavours of ubuntu. Someone else was testing those flavours.

I would guess that whether you click the Ubuntu upgrade or the Kubuntu upgrade you will have problems. Do not expect the other desktop environments to be upgraded either. I guess that they will cause problems if you try to load into one of those environments afterwards.

People have problems upgrading when they have heavily modified the OS. If you had a pure Kubuntu install or a pure Ubuntu install there would be less risk of failure.

You ask:

> Does anyone know? Is there any way to find out?

The answer is to go ahead and try it, yourself. You are the tester.

Regards.

---

### Post by StewartM on 2012-05-06
> **grahammechanical said:**
> 

The answer is to go ahead and try it, yourself. You are the tester.

Regards.

Will do; maybe next weekend, though I'm tempted to upgrade my 10.04 system to 12.04 first even though July is the recommended date for users making that transformation. I am tempted because my webcam has just stopped working with flash on my 10.04 pure Ubuntu box, no matter what browser, even though the same hardware works just fine on two 11.10 Ubuntu machines with the same browsers and the same version of flash. 

I'm thinking that I'll get Ubuntu, as even Muon tells me that I'll get Ubuntu when I open the update prompt and then cancel. But it does not matter, if I get just one DE working I can fix the others. I do have /home on a separate partition so in the worst case, I can do a clean re-install.

I'll let everyone know how it went, just to build the user base.

StewartM

---

### Post by StewartM on 2012-05-14
Well, I did the laptop upgrade yesterday, and all the various desktop environments seem to have been upgraded, not just Ubuntu (which took 3 hours instead of the usual 2, and plus I saw libraries and programs unique to say, KDE, being downloaded). Actually I was rolled back from KDE 4.8.3 to 4.8.2, the former apparently not making it before the freeze date, but that's a simple matter to correct.

So it seems even for a heavily customized system like mine, Ubuntu will upgrade or attempt to upgrade everything. I'll mark this thread "solved".

StewartM

---

