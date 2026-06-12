---
title: "Problem with Synaptic Mgr"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by kwandtke on 2008-06-30
I hope I'm putting this in the right section. OK, so I was running Gutsy for several months and all was well. After Hardy came out, I saw in Synaptic it was available so figured I'd let it handle the update. All seemed to go well and Hardy has been working fine with one exception.

Synaptic Mgr will not run ... Now I've many years working with Windows and only a short time with Linux so I'm still putting all the pieces.  I assume Synaptic Mgr in addition to running off the menu is also the piece that handles day-to-day updates right?  So after the main update to Hardy the next time I get on I see the little message that says 36 updates or whatever ... I fire it off, tell it to apply them and when I come back SM is just sitting, nothing seems to have updated and SM itself is unresponsive. Will minimize but not finish and i can not close it. In system mge it shows the process as sleeping.  I also have tried (after a reboot) to load an application from the menu .. pretty much the same thing .. it fires up and acts like it's going to run then nothing.  Is there a way to re-load it? Something similar to a  REPAIR or something? I've used apt-get to install a couple of things I was looking at and that seems to work fine so I'm not sure if it's fair to say that SM is just a gui front end to apt-get .. but?  

Any help would be great .. I hope to not have to re-load .. I'm starting to use my new desktop(as opposed to before where I was experimenting, testing .. getting my feet wet but still leaving all my data or at least the primary copy on a Windows box) so a reload would be a little more painful than the time ... thanx in advance

---

### Post by dburnett77 on 2008-06-30
Don't xkill the "Another Synaptic is running..."

You can't do it both at once.

---

### Post by avtolle on 2008-06-30
I believe that it is update manager that handles the day to day updates. From what you are reporting, you are having problems both with the update manager (which handles updating the computer) and with Synaptic Package Manager (which handles installation of new packages, not updates, to your system). You have also reported some success with doing installation from the command line using the "sudo apt-get" method. 

First, what error messages (if any) do you get from the update manager when trying to update? I'm also curious about any error messages you might get from Synaptic when trying to install a new package.

From terminal, try this ```
sudo aptitude update && sudo aptitude safe-upgrade
```and post any error messages you get.

---

### Post by kwandtke on 2008-06-30
> **avtolle said:**
> I believe that it is update manager that handles the day to day updates. From what you are reporting, you are having problems both with the update manager (which handles updating the computer) and with Synaptic Package Manager (which handles installation of new packages, not updates, to your system). You have also reported some success with doing installation from the command line using the "sudo apt-get" method. 

First, what error messages (if any) do you get from the update manager when trying to update? I'm also curious about any error messages you might get from Synaptic when trying to install a new package.

From terminal, try this ```
sudo aptitude update && sudo aptitude safe-upgrade
```and post any error messages you get.

Thanx .. I'll try this tonight .. as to error msgs .. none .. it (update manager) acts like it is beginning OK .. shows me the updates available .. then I select either all or even one .. starts out with "preparing" .. or whatever ... and thats it .. stops there ... or rather just seems to freeze there.

---

### Post by kwandtke on 2008-07-04
Well I did the command and then rebooted the system .. seemed to fix up Synaptic as once back in I went in and loaded a random application and it worked fine.

Update Manager is still hosed tho .. shows me patches, I select them and say install and the hour glass turns into that "spinning" icon and thats it... System monitor says it's sleeping ...

Anyone have any ideas?

---

