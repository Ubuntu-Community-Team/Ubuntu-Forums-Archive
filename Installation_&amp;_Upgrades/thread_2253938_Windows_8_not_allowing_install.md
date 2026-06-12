---
title: "Windows 8 not allowing install"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by jordan31 on 2014-11-23
I have an HP Elite iCore 7 2.7ghz 8gb RAM that originally ran Windows 7 and now runs Windows 8, very slowly, always freezing apps.

I attempted to install Ubuntu, but once the Ubuntu loading screen appears off of the boot disc, nothing happens...

I can't get to any install screen, and I have attempted to change the BIOS settings, per a solution I found on another forum, but to no avail...

Can you help?

All the best,

new user

---

### Post by oldfred on 2014-11-23
Is this hardware both UEFI and BIOS or just BIOS?
And is Windows installed in UEFI or BIOS boot mode?

Post this from terminal in live installer:

sudo parted -l

If UEFI this will not tell much:
sudo fdisk -lu

---

### Post by jordan31 on 2014-11-23
Here is a screen shot of my disk mgmt set up (I believe it is BIOS but I am an inexperienced user):

[ATTACH=CONFIG]258160[/ATTACH]

---

### Post by oldfred on 2014-11-23
Looks like a typical BIOS install with all 4 primary MBR(msdos) partitions used.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by jordan31 on 2014-11-23
This is awesome... I am beyond grateful! I'll jump in to the full circle feature - and - reference the other links, as they will be needed, too.

Happy Thanksgiving, and I thank you sincerely!!! I will reply to tell of success...

---

