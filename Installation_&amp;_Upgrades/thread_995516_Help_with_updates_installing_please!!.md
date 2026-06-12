---
title: "Help with updates /installing please!!"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by bridges0123 on 2008-11-27
Ok so i'm new to the whole unix/linux system so any help is appreciated. ok so on to my question, i just put ubuntu on my computer and for some reason i'm not getting the update balloon at the top of my screen for downloading updates, is there a way to make that show up/ does it download all updates? or do i have to go online and download every single little package? also how do you install programs on a computer after i unzip them? thanks!!! 

-bridges

---

### Post by taurus on 2008-11-27
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by bridges0123 on 2008-11-27
i get a message like this

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_US
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by brigadoon on 2008-11-27
Can you manually check for updates through the Ubuntu interface? Go to the top menu bar an select...

System/Administration/Update Manager

Let us know if it activates.

---

### Post by taurus on 2008-11-27
Make sure you close down synaptic, add/remove, or update-manager before you run those two commands from a terminal.

---

### Post by bridges0123 on 2008-11-27
ok so now i feel dumb but i says fully up to date, but why can't i install any of the things in synaptic package manager?? like every time i click on stuff in there or in update manager it says downloading 1-2-3-4-5-6/6 but how do i install those things? like it keeps downloading the same thing but doesn't ever install them it seems, sorry about all the questions i'm really new to this whole OS but i really wanna get it.

---

### Post by cdtech on 2008-11-27
> i just put ubuntu on my computer and for some reason i'm not getting the update balloon at the top of my screen for downloading updates, is there a way to make that show up/ does it download all updates?
If you go to "System > Administration > Software Sources" select the "Update" tab. There you can be notified of updates.
[ATTACH]94445[/ATTACH][ATTACH]94446[/ATTACH]
> also how do you install programs on a computer after i unzip them?
There are no installable packages with a zip extension. You may need to unzip the file into a separate directory and use the "Package Manager" to install it. Use the right mouse button and select open with "Package Manager" (after you unzip it into it's own directory).

Check the "Add/Remove" before you download zip files, see if it exsist there first.

---

### Post by taurus on 2008-11-27
What are you trying to install?

---

### Post by bridges0123 on 2008-11-27
ok nevermind through messing with the update manager i got it to go and now it's installing a thousand some odd files thanks for all your help!!!

---

### Post by bridges0123 on 2008-11-28
ok nevermind i figured it out. i think i've got the downloading and installing of programs now, thanks a million!

---

### Post by forkandles on 2008-11-28
bridges0123,
Glad you got things sorted.
I will give Vuze a try. Thanks.

---

