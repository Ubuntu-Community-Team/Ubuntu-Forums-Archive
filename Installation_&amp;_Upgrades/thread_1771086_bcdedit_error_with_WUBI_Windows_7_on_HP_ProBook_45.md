---
title: "bcdedit error with WUBI Windows 7 on HP ProBook 4530s laptop"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by yusbutt on 2011-05-30
Hay guys ...

I have got new HP ProBook 4530s core i3 with genuine Windows 7 Home premium (64-bit) and tried to install Ubuntu 11.04 with WUBI, I also tried to install by saving this ISO [http://releases.ubuntu.com/natty/ubuntu-11.04-desktop-i386.iso](http://releases.ubuntu.com/natty/ubuntu-11.04-desktop-i386.iso) in same directory where I saved WUBI but during mid (mid to end) of installation I always get error like following attached screen shot.

Please note: I am running WUBI as an Administrator and also I copied this screen shot from forum because I am almost getting same error during installation.

Looking for a speedy response. Please provide some easy solution because I am not as expert as you guys are .. LOL! :D

---

### Post by Rubi1200 on 2011-05-30
Hi and welcome to the forums :-)

The first thing to check is whether there is an entry for Ubuntu in the boot configuration:

You can right click on "Computer", Properties, Advanced system settings, Startup and Recovery settings and make sure that Ubuntu is listed under the "Default operating system dropdown" (don't set it as the default). Then check the "Time to display list of operating systems" and make sure it is 15 or 30.

Also, check in the Ubuntu folder and make sure there is a folder labelled Disks and make sure the root.disk and swap.disk are there.

---

### Post by yusbutt on 2011-05-30
Hay thank you very much for a prompt response.
I'll definitely act upon what you said and let you know about the outcomes.

Chreers.

---

### Post by yusbutt on 2011-05-30
Hay,
Just want you to know that I have checked Advanced system properties and found only windows 7 in the drop down, I am going to attach the screen shot, please check.

And the second thing you mentioned just flew over my head and I didn't get it ... :(

Please let me know how to fix the problem now? Awaiting reply.

---

### Post by Rubi1200 on 2011-05-30
Hi,
please go to the Disk Management utility on Windows and take a screenshot of how Windows sees your disks and then post it here.

Thanks.

---

### Post by yusbutt on 2011-05-30
Here attached is the screen shot of disk management, I am trying to install Ubuntu in D drive.

---

### Post by Rubi1200 on 2011-05-30
Hi,
the problem you are experiencing stems from the fact that your disks are dynamic. In situations like this, it is not only inadvisable, but most likely also impossible to install Ubuntu whether with Wubi or normally.

It might be possible to install Ubuntu normally on an external disk and choose to boot from there, but I would rather someone else confirms if that is possible in this situation before you go ahead and try it.

---

### Post by yusbutt on 2011-05-30
ohhhh ... means its so hard for me to have Ubuntu on my lappy??? :(
Anyways ... thanks a lot for you time ... :)

Cheers!

---

### Post by Rubi1200 on 2011-05-30
Take a look at this thread about dynamic disks in Windows:
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

The forum members who responded there, oldfred and srs5694, know more about this than most and I would definitely heed their warnings and advice.

Sorry to be the bearer of bad news. However, if an external disk is beyond your budget how about a USB stick of say 16GB? You could then install Ubuntu there and set it up to use persistence, meaning the ability to save settings, install software etc. It is not ideal, but at least you could run Ubuntu.

---

### Post by yusbutt on 2011-05-30
Thanks a lot for the kind advices, I'll definitely go for an external hard dive or USB. :)

take care
bye

---

### Post by Rubi1200 on 2011-05-30
One final warning; if you do decide to do this please make sure not to mount drives from the hard drive itself. Ubuntu would likely use the MBR  partition table and ignore the dynamic drive information with the possibility of unpredictable results. Moreover, mounting for write access could lead to  data loss.

If you decide to try this method with an external medium and have any questions when starting, feel free to ask here and we will try and help.

---

### Post by nikoss on 2011-06-05
I recently installed ubuntu 11.04 in my 4530s with windows 7 preinstalled.

the problem is that there are 4 primary partitions and so you must delete one of them and make an extended partition and some logical into this.

here is the solution I found in order to keep HP diagnostics and BIOS extensions:

[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/HP-ProBook-4520s-Dual-Boot-between-Win7-64-bit-and-Ubuntu-10/td-p/407219](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/HP-ProBook-4520s-Dual-Boot-between-Win7-64-bit-and-Ubuntu-10/td-p/407219)

---

