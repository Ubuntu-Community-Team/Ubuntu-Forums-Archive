---
title: "No resume image, doing normal boot..."
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by zajjar on 2007-04-25
After a fresh installation of Ubuntu 7.04, on a console "1" (ctrl+alt+F1) i see following error/warning:

<cut>
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/cfb91b2e-b730-41a6-be45-03f36ef48b07) = hda6(3,6)
kinit: trying to resume from /dev/disk/by-uuid/cfb91b2e-b730-41a6-be45-03f36ef48b07
kinit: no resume image, doing normal boot...
</cut>

(hda6 is a SWAP partition)

System normally works, but I want to fix that problem.
How can I do it?

-- 
regards,
zajjar

---

### Post by kpkeerthi on 2007-04-25
It is not an error it is a normal info message. The kernel is trying to find if you have hibernated your system last time so it can resume. If not, boots normally.

---

### Post by zajjar on 2007-04-25
Thank you very much kpkeerthi for this explanation. Now it's clear :)

-- 
regards,
zajjar

---

### Post by DJ_Peng on 2007-04-25
Sweet. I was wondering about this myself. Is there any way to disable this and gain a few seconds of load time? I don't use hibernation (I think I have it disabled in my power settings) so there's really no use for it if it can be disabled.

---

### Post by jagrav on 2007-05-01
As is mentioned in another thread here, one way to get rid of this message is to edit menu.lst in /boot/grub and change the line,

# defoptions=quiet splash

to

# defoptions=quiet splash noresume

and then run,

sudo update-grub


After doing this, I no longer get this message. Hope this helps.

---

### Post by platypuss72 on 2008-03-01
hi all 

i ahve been hunting and found the solve on another post 

[http://ubuntuforums.org/showthread.php?t=636268#post3922624](http://ubuntuforums.org/showthread.php?t=636268#post3922624)

it works great ...

---

