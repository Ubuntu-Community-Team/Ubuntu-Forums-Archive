---
title: "Replace W10 with Ubuntu 14.04 LTS."
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by dtree46 on 2016-11-25
Want to completely get rid of W10. Tried a few ways and were unsuccessful.
Had to reinstall W10 three times now.
Is there complete instructions or tutorial on how to do this?
If so, can someone please direct me to them.

dlw

---

### Post by QIII on 2016-11-25
Hello!

Which "few ways" have you tried?

---

### Post by yancek on 2016-11-25
Why have you re-installed it three times if you are trying to get rid of it?
Use a partition manager and delete and/or format the windows partitions if you don't want it.  If you want to install Ubuntu you can do that with the installation media, erase disk and install Ubuntu.

---

### Post by dtree46 on 2016-11-25
Well... Inserting a Ubuntu disk (16.04LTS) it ran so far and stopped due to an error. Did not say which error.
Using 14.04LTS, could not install because of an Nvidia 746 graphics card. Downloaded the Nvidia driver but Ubuntu had to be running enable to install it.
Changed to internal graphics card, that did not work. Did a couple other things I can not remember. Been trying this for about a month or so, off and on.
Had to reinstall W10 so there was an OS on the box.

I think the problem is multiple. MS's ERI(?) sys, Legacy sys and graphics card; probably more than I am not aware of.

Also had to reinstall W10 due to some kind of virus or malware which hit again two days ago.
That and the fact that I've haven't used W very much since 2000. Ran dual boot for a couple of years at first.

---

### Post by RobGoss on 2016-11-25
How are you installing Ubuntu USB or DVD?

How did you create your media installation what software did you use?

Post the specs for your machine it will help others trouble shoot your problem. 

You mentioned there was a error, what was that error message you got when you tried to install Ubuntu

---

### Post by dtree46 on 2016-11-25
> **RobGoss said:**
> How are you installing Ubuntu USB or DVD?  DVD

How did you create your media installation what software did you use? Wrong, see next post.

Post the specs for your machine it will help others trouble shoot your problem.  HP Envy 750-170, 24gb ram, 512gb SSD, 2 x 1tg HD's.

You mentioned there was a error, what was that error message you got when you tried to install Ubuntu Do not remember. Been about 2 weeks ago.

---

### Post by oldfred on 2016-11-25
Is system UEFI or BIOS?
And if UEFI you need to install Ubuntu in UEFI boot mode which is more complicated than the old BIOS mode as it now offers 3 boot modes. UEFI with Secure boot (Windows standard), standard UEFI and CSM or emulation of BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Is system came with Windows 10 or is upgrade from Windows 8, it is UEFI. If upgrade from Windows 7 most likely BIOS, but could be UEFI.

Lots of details on UEFI in link in my signature. If you  have UEFI worth reviewing, much may not apply.

What brand/model system. Many have unique requirements.

And with nVidia card you will need nomodeset to boot installer & first boot or until you install nvidia driver from Ubuntu's repository. Do not install from nVidia with .run file.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by dtree46 on 2016-11-26
16.04LTS finally installed from the DVD. W10 gone bye bye. 
Thanks for all your efforts.

dlw

---

### Post by RobGoss on 2016-11-26
Glad you were able to get Ubuntu installed if you have resolved your issue you can mark this thread as solved by using the **Thread tool** at the top of this post

---

