---
title: "Upgrade - do I need to backup data ?"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by FDPOD on 2008-09-20
Hi,

I would really like to update from 7.04 -> 7.10 -> 8.04 with the **Systems>Administration>UpdateManager** - Procedure.

All the security updates run stable and I'd like to know if this upgrade process is also stable enough to run it without a full backup first ?

Does it carry over all the installed programs and modifications I've done to the system so far ?

Tx
FD

---

### Post by overdrank on 2008-09-20
> **FDPOD said:**
> Hi,

I would really like to update from 7.04 -> 7.10 -> 8.04 with the **Systems>Administration>UpdateManager** - Procedure.

All the security updates run stable and I'd like to know if this upgrade process is also stable enough to run it without a full backup first ?

Does it carry over all the installed programs and modifications I've done to the system so far ?

Tx
FD

Hi and I would say always back up data. There is always a chance that the update can be interrupted or fail. If you have a separate home partition then your settings should be save. I would also say that upgrading that far I would do a clean install. If I were upgrading from 7.10 to 8.04 I might try but not from Feisty. Just my opinion. :)

---

### Post by FDPOD on 2008-09-20
Thanks for the info.
I have no problem doing a clean install.

Just to be sure I understood right - the n00b in me has to ask:
All the separate programs and packages that I installed (i.e. NVidia Driver, NTFS Read/Write support, VW Ware, Wine-Stuff, Weather Icons in taskbar, dual CPU icons in taskbar, Favorites, ....) during my 'playing around' with 7.04 are all going to be saved with my HOME folder backup ?

My issue is: Do I need to reinstall all the programs after the fresh install again or is it 'just' copying the home folder back to the newly installed partition going to be sufficient.

If I have to reinstall everything it's going to be a major PITA.... :lolflag:
and I kind of figured I could as well give it a shot with the Auto-Update.
(If I backup the HOME folder I wouldn't be worse off ....:-D

If HOME is on a separate partition vs. just a HOME folder in a current partition - would that make a difference ? - It's currently in the same partition :(

---

### Post by mkvnmtr on 2008-09-20
I can't answer if all your programs are saved I thought it was just your settings. I had to do a reinstall and did not save anything. I think you should back up your whole system and then try to upgrade. You seem to have a lot invested in your system. If it doesn't work you can put it back the way it was and check and plan some more to get transfered to 8.04. For me it has been easier to just install again but I am not a power user.

---

### Post by FDPOD on 2008-09-20
Well, to be on the safe side  - I'll prepare a backup of the whole system ....[-o<   (HOME needs to get backup'd anyway again ...)

In the meantime - anybody having clicked the **Upgrade** -Button - were your programs & settings saved through the process or not ?! 

I'd run the 7.04 to 7.10 upgrade to see how it works but I don't want to screw it up with that simple click. 
But I also shy away from putting in too much effort into tracking down all the customization I have done so far. :)

***@mkvnmtr:*** Did you try an upgrade and it failed so that you had to do a reinstall ?

---

### Post by Pumalite on 2008-09-20
Overdrank is right; a clean install is always better than an upgrade. You can make an image of your present system and store it on a USB. Also make sure you have your system fully updated if you venture an upgrade. All third parties should be removed from your sources.list.

---

### Post by mkvnmtr on 2008-09-20
Yes I tried to upgrade and couldn't. Finally had to reinstall. I did not lose anything trying from 6.06 to 6.10 it just put me back into 6.06.  I think from 7.04 one time it got messed up and I reinstalled when I could not upgrade to 7.10. My experience might not relate to yours because I am using a ppc Mac. Going to 8.04 the repositories did not have the files I needed and I had to use back ports. It was only difficult because I am sort of slow sometimes.

---

### Post by cariboo on 2008-09-21
When doing an new install create a separate home folder, this way all your settings are always there and you just have to reinstall the programs with out having to reconfigure them. If you never clean out /var/apt/archive you can use synaptic to create a list of programs you normally install. Go to System-->Administration--Synaptic Package Manager-->File-->Generate Package Download Script.

I have been doing clean installs of all the intrepid alphas and I usually delete all of the configuration files except for .mozilla and .mozilla-thunderbird but it seems I keep forgetting to instal one or two packages, so I'm going to try the install script and see how it works.

Jim

---

### Post by Pumalite on 2008-09-21
If you keep up with the updates; you must have Intrepid Ibex Alpha 6 in all of them. I do. I started in Alpha1

---

### Post by FredoV on 2008-09-21
> **cariboo907 said:**
>  . . .

If you never clean out /var/apt/archive you can use synaptic to create a list of programs you normally install. Go to System-->Administration--Synaptic Package Manager-->File-->Generate Package Download Script.

Thank you, Jim! That is a good idea: always have a Package Download Script with all the stuff you have on your machine!

Again: Thank you!
:-)

---

### Post by FDPOD on 2008-09-24
Geez, it sounded so nice ...:)
> **cariboo907 said:**
> ... System-->Administration--Synaptic Package Manager-->File-->Generate Package Download Script.
... 
The file this creates is only 10 bytes. And it contains one line : #!/bin/sh  :(

> **cariboo907 said:**
> ... If you never clean out /var/apt/archive 
...  
...and I never did anything like that ...
Unfortunately I do not even have the referenced */var/apt/ * folder at all ...:confused:

Am I missing a part ....:?:

---

