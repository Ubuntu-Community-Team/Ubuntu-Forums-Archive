---
title: "AN INSTALLATION WORKAROUND: Here's what I reccommend if you're having trouble..."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by mbmccormick on 2007-04-21
I've spent the last three days trying to install Ubuntu 7.04. First of all, I cannot get the upgrade utility to work properly. I get an error that says "...sources.gz cannot be downloaded. This may be a network issue." No. It's not a network issue. I tried to download the package without the utility. Worked fine. So then I figured that a fresh install would be nice anyways. So I decided I would wipe everything out. Download the ISO, burn, reboot. I get to a menu, I select "Install". Get a splash screen, and then it crashes and says "cannot access tty, job control turned off", and I'm left with a BusyBox command line. So I did some searching, and found that I needed to insert a floppy disk into the drive to get around this. So I did, and it worked, until I get to where it wants to start the GUI. Nope. NVIDIA graphics card not supported. Ok. So I rebooted, with the floppy, modified some boot parameters and got to a command line. Setup networking manually, download the NVIDIA drivers, modified the xorg.conf file and then manually started X. Worked. Great! Went to install, ran through some menus, hit the go button, walked away (how dare I...), and came back to find that it froze. So... New plan...

WORKAROUND: I just downloaded the alternate install ISO (with the recovery tools, low ram install, OEM settings, etc.). Burn, reboot, install in text mode. Worked perfectly! What is wrong with this picture? I honestly don't know how someone who is an avid Linux user is expected to figure this out, let alone someones grandmother... I just hope this is all fixed by the time the next LTS release is out, or Ubuntu may be getting some bad PR.

Anyways, I hope this helps some of you who are in my shoes...

---

### Post by graydon40 on 2007-04-21
What did you put on the disk to get up and going ? I'm having the same problem .... 
thanks  graydon

---

### Post by hal8000 on 2007-04-21
WORKAROUND: I just downloaded the alternate install ISO (with the recovery tools, low ram install, OEM settings, etc.). Burn, reboot, install in text mode. Worked perfectly! What is wrong with this picture? I honestly don't know how someone who is an avid Linux user is expected to figure this out, let alone someones grandmother... I just hope this is all fixed by the time the next LTS release is out, or Ubuntu may be getting some bad PR.

Anyways, I hope this helps some of you who are in my shoes...


I have install problems because I have FreeBSD and Solaris as Primary partitions. Why DOES
Ubuntu have to use Gparted !! It does not recognise UFS2 or BF partitions so I am forced to install in text mode, but there is no text install mode in Feisty.

Please do tell where you downloaded the alternative iso. I can only see downloads for the full
697M ISO image of Ubuntu 7.04.

With 6.10 and lower versions text install was always available.
The only linux distro now with a perfect install routine is Pardus Linux. I hope someone can give me the URL for the alternate install ISO. Thanks in advance.

---

### Post by dobuntu on 2007-04-21
> **hal8000 said:**
> Please do tell where you downloaded the alternative iso. I can only see downloads for the full 697M ISO image of Ubuntu 7.04.

With 6.10 and lower versions text install was always available.
The only linux distro now with a perfect install routine is Pardus Linux. I hope someone can give me the URL for the alternate install ISO. Thanks in advance.


When you are in the main download page ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)), just below the "start download" button, there is a check box: if you check it, you'll get the alternate CD ISO

Alternatively, you can find all sorts of ubuntu versions starting from here:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Ciao!
dom

---

