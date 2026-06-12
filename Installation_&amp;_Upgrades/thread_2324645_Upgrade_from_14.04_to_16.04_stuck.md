---
title: "Upgrade from 14.04 to 16.04 stuck"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by Le3eVolfoni on 2016-05-15
Hello,

I am upgrading the family computer from 14.04 to 16.04. The upgrading stopped during the installation of the upgrade, and I don't know what to do to make it go further. My ubuntu is in French, I will to try to translate everything the best I can.

During the configuration of ```
liblwp-protocol-https-perl (amd64) 
``` the small terminal that is in the same window showed ```
_n modifié grub : _
``` (in english, *n modified grub :* I suppose). I can write, I tried y, yes, n, no in both french and english, I tried tab, escape... Everytime, once I press enter, the same line comes back.

And here are the 3 last entries of the terminal with which I launched the ugrade:

```
/usr/bin/diff: /etc/grub.d/10_linux.dpkg-dist aucun fichier ou dossier de ce type
/usr/bin/diff: /etc/grub.d/20_linux_xen.dpkg-dist aucun fichier ou dossier de ce type
/usr/bin/diff: /etc/grub.d/30_uefi-firmware.dpkg-dist aucun fichier ou dossier de ce type
```

*"Aucun fichier ou dossier de ce type"* means [I]"no such file or directory"
[/I]
I have no idea what to do next.. Any help would be highly appreciated.

---

### Post by Bucky Ball on 2016-05-15
*Thread moved to **Installation & Upgrades**.*

How are you trying to upgrade? What command did you use?

Can you hit control+c in a terminal and that stops the process? Can you do other things on the computer and it's just the terminal that 'locked'? If you're completely locked out and can't shutdown, can you hit control+alt+F1 and that gets you to a CLI (a big terminal) where you can log in?

When you say it stopped during upgrade, could you see it was downloading files and suddenly stopped with these errors or you tried to upgrade and it stopped very soon after?

So many questions!

---

### Post by Le3eVolfoni on 2016-05-15
Thanks for the quick answer.

I upgraded using* sudo update-manager -d* as I did with my own laptop. The computer didn't freeze, nor did the upgrading window, it only seems to be stuck, asking the same thing over again. The process of upgrading is actually almost over, packages are downloaded, the installation is around 95%, the two last steps are "cleaning" and "restart". I don't really want to try ctrl-c, the process being close to be done I am afraid it would end up with an half upgraded unbootable machine.

---

### Post by Bucky Ball on 2016-05-15
Oh. Well let it roll til it finishes. I'm confused. You have two terminal windows open, one is working as it should and upgrading and the other is simply sitting there not doing anything??? Then forget about the inactive one, let the upgrade finish and reboot the machine. See what happens when the upgrade is done.

---

### Post by deadflowr on 2016-05-15
It may be that the clean up page is hiding somewhere.
I'd press "super + W" and see if it show there.
Or try "Shift+Super+W", as it might be in another workspace.

Super+W runs the scale/spread command and will show all open windows, whether minimized or in other places.

You can simply press the keys again to go back to normal.

I've had that page hide on me before.
That's why I suggest it as something to look into.
Could be off though.
Hope it helps

---

### Post by Le3eVolfoni on 2016-05-15
There is one usual terminal with which I entered the line to start the upgrade. This terminal is now inactive, nothing is moving, and the last lines are 
> /usr/bin/diff: /etc/grub.d/10_linux.dpkg-dist aucun fichier ou dossier de ce type
/usr/bin/diff: /etc/grub.d/20_linux_xen.dpkg-dist aucun fichier ou dossier de ce type
/usr/bin/diff: /etc/grub.d/30_uefi-firmware.dpkg-dist aucun fichier ou dossier de ce type

And there is the window with the upgrading process, process that is not active, and in this window a small terminal, the one with "n modified grub:". Nothing is active since now more than an hour.

---

### Post by Le3eVolfoni on 2016-05-15
I tried super-w and I had no hidden window. But for a reason I ignore I ended up closing my session. So now the upgrade window is gone, so is the terminal. According to Details my ubuntu is now 16.04. The process wasn't over, I am affraid the computer won't boot if I turn it off. Would you know a way to check and/or repair an unfinished upgrade ?

---

### Post by oldfred on 2016-05-15
If you do not have those grub files, it cannot run the internal sudo update-grub to add new kernels to grub menu.

The main question is whether it has run the update, and not just the grub update.
Do you have an proprietary drivers like nVidia or ppa's in this system. They almost always cause issues, that stall update.

Have you run Boot-Repair before? If you reboot and it does not work, then you need Boot-Repair's advnaced mode and the uninstall (perhaps nothing) and reinstall of grub which should reinstall all of grub again, so those missing files are added.

       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

There is also this, but not sure how active they are. If you can handle the English we will try to help.

 French Forums
 [www.ubuntu-fr.org](www.ubuntu-fr.org)

---

### Post by Le3eVolfoni on 2016-05-15
I do have nvidia propietary drivers installed. I changed the grub menu using grub customizer as well. I have the pipelight ppa and that's it. I know boot repair (I always have a live cd somewhere). I am not sure only the grub menu is to be repaired. I guess the only way to know it to try to restart the computer. I do it and I let you know.

---

### Post by grahammechanical on 2016-05-15
The 16.04 release notes say this:

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

### Post by oldfred on 2016-05-15
You may need nomodeset for nVidia until you reinstall the correct version of proprietary driver from Ubuntu repository.
I do not think an upgrade reinstalls the nVidia driver. 

I know grub customizer creates its own scripts in the grub script file. That can confuse things also, and may be part of issue.
ls -l /etc/grub.d
All the files with proxy in the name are from grub-customizer.

---

### Post by Bucky Ball on 2016-05-15
> **Le3eVolfoni said:**
> I do have nvidia propietary drivers installed.

Did we miss this? If you have proprietary drivers for graphics installed during upgrade it can cause issues. Best to switch off PPAs and third-party drivers, update/upgrade the system, then do the OS release upgrade. (Anything I'm forgetting?).

Did you have any PPAs or non-open source drivers happening when you attempted the upgrade?

---

