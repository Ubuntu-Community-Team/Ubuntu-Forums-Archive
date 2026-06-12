---
title: "Green Check Marks on Files"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2009-10-12
I just installed some updates and noticed there were green check marks appearing on all my files and folders. Anyone else see this or am I loosing it? 8-[

---

### Post by emarkay on 2009-10-12
Yea me too!  

I was going to say something about this...  :)

Ugly!

---

### Post by VMC on 2009-10-12
If you right-click on any one of those files and look at the tab Emblems. Is the default "green check" checked? If so that's the problem. Somehow you managed to "green check" all your files.

---

### Post by emarkay on 2009-10-12
> **VMC said:**
> If you right-click on any one of those files and look at the tab Emblems. Is the default "green check" checked? If so that's the problem. Somehow you managed to "green check" all your files.

OK, it means "Ubuntu One Synchronized" - well I looked a U1 a few weeks ago and there were many issues - I haven't logged into it - so HOW does it KNOW what is synchronized and HOW DO I DISABLE it?

---

### Post by FuturePilot on 2009-10-12
> **VMC said:**
> If you right-click on any one of those files and look at the tab Emblems. Is the default "green check" checked? If so that's the problem. Somehow you managed to "green check" all your files.

I haven't done anything to my files. After installing updates they magically appeared. I saw them appear right in front of my eyes. However one of the emblems is check: "ubuntuone-synchronized". What's even weirder is I haven't even authenticated this computer to Ubuntuone yet. Something has marked every single file with this emblem and not just in my /home, They're showing up on / too :shock:

---

### Post by emarkay on 2009-10-12
Well????   :)

---

### Post by Laibcoms on 2009-10-12
> **emarkay said:**
> Well????   :)

Well.. it is a bug then :p  Now to search the bug list if someone reported this already.. ;)

EDIT: reported it, since I can't find any.
EDIT: Here: [https://bugs.launchpad.net/bugs/450024](https://bugs.launchpad.net/bugs/450024)

---

### Post by mc4man on 2009-10-12
Is due to the update of one of these three packages

> Upgraded the following packages:
python-ubuntuone-client (0.96.0-0ubuntu1) to 1.0.0-0ubuntu1
ubuntuone-client (0.96.0-0ubuntu1) to 1.0.0-0ubuntu1
ubuntuone-client-gnome (0.96.0-0ubuntu1) to 1.0.0-0ubuntu1


On my main machine no issue

On a tester before updating those packages first went to Applications -> internet -> ubuntuone and clicked on it.( never have touched ubuntuone before on either machine ) At the main screen just closed it out, did not set up a launchpad account.

Ran the updates, rebooted and all files, folders are green checked

Edit : removed the ck. marks by removing ubuntuone-client-gnome and rebooting, took 2 reboots and they're gone

---

### Post by ranch hand on 2009-10-12
Or, and this is a guess as I am back on 9.04, you could uncheck the green check check.  There is probably a way to do this from the mother directory and have it effect the ones inside it.

ubuntu-bug ubuntu-one (or whatever the proper syntax is for Ubuntu One) would be a good idea too.

---

### Post by john_brown_jr on 2009-10-12
The link to the bug in Launchpad: [https://bugs.launchpad.net/ubuntuone-client/+bug/450006](https://bugs.launchpad.net/ubuntuone-client/+bug/450006)

---

### Post by VMC on 2009-10-13
> **john_brown_jr said:**
> The link to the bug in Launchpad: [https://bugs.launchpad.net/ubuntuone-client/+bug/450006](https://bugs.launchpad.net/ubuntuone-client/+bug/450006)

Thanks Noel. I signed "this bud affects me too".

---

### Post by Laibcoms on 2009-10-13
> **john_brown_jr said:**
> The link to the bug in Launchpad: [https://bugs.launchpad.net/ubuntuone-client/+bug/450006](https://bugs.launchpad.net/ubuntuone-client/+bug/450006)

Marked my earlier bug report ( [https://bugs.launchpad.net/bugs/450024](https://bugs.launchpad.net/bugs/450024) ) as duplicate of 450006.

---

### Post by FormerSlacker on 2009-10-13
Same here. I uninstalled all ubuntu one related packages, and the check marks are gone.

---

### Post by mc4man on 2009-10-13
> uninstalled all ubuntu one related packages, and the check marks are gone.

re-installed to testing install, didn't affect my real install but decided to dump ubuntuone on that install anyway, have no intentions of ever using.

After a reboot today marks are back, the ubuntuone-client-gnome package seems to be main culprit

---

### Post by hanzomon4 on 2009-10-13
[It was this update I think]("https://bugs.launchpad.net/ubuntuone-client/+bug/440839")

---

### Post by emarkay on 2009-10-13
Still there after this morning's update.

QUESTION: Is this how it's SUPPOSED to be, now?

---

### Post by taavikko on 2009-10-13
> **emarkay said:**
> Still there after this morning's update.

QUESTION: Is this how it's SUPPOSED to be, now?

[https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/450112](https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/450112)

---

### Post by rifak on 2009-10-13
i can confirm also that when all ubuntuone packages are purged, the emblems are removed.

---

### Post by rburkartjo on 2009-10-13
tks for the info

---

### Post by rifak on 2009-10-13
the fix for the green, ubuntuone checkmark emblem has been added to the repos as version 1.0.1. if you have purged the package, a reinstallation of of them will do the trick (this is what i did). if you never uninstalled them, then an update should be sufficient.

---

### Post by null_pointer_us on 2009-10-13
The most recent update (1.0.1) of ubuntuone-client fixed this for me. It involved removing some gnome related package and adding a python related package, but that went well. Rebooting (after updating) eliminated the green check marks although restarting X might have worked.

---

### Post by QQi on 2009-10-13
^
thanks

updating

---

### Post by FuturePilot on 2009-10-13
Yep, the update fixed this.

---

### Post by rburkartjo on 2009-10-14
yes the newest updates removed them

---

