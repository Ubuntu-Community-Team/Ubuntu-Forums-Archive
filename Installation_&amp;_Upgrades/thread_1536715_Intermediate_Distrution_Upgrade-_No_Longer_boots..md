---
title: "Intermediate Distrution Upgrade- No Longer boots."
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2010-07-22
Currant Status: 07.24.10 Completed in last post.
 
**Summary:** After intermediate upgrade, Ubuntu Lucid LTS 10.04 64bit Desktop Edition will "NOW" not run in any Graphics mode on my machine.
 
**General;** Ubuntu has been my favorite OS to live on, play and relax. I have to use other OS'es, but I choose Ubuntu as "mine". I can go around it safely and tweak it to my own likings and needs. It has also been a great tool to exchange things between other OS'es. 
 
**History:** I started with Ubuntu Karmic Koala 9.04 64bit Desktop Edition. Last March, I upgraded to Ubuntu Lucid LTS 10.04beta 64bit Desktop via the Update Manager, using Ubuntu's instructions... as a Beta Tester. I kept up with Updates and everything had been fine.
 
All went well, albiet minor adventures that gave me oportunities for enriched challenges and training. Overall, since the early days of that, my system has been very stable and reliable- Until last Saturday through Yesterday...
 
**Problems:** First thing I noticed is that there were some security updates Friday. Saturday when I came up into Ubuntu, it came up in error saying it had to come up in a low graphics mode. I shut down the system and restarted. It came up fine and I thought nothing more of it at the time...
 
Second, I tried to install Ubuntu Lucid LTS 10.04 64bit Server Edition on another drive. My other drives were isolated. Although the install said it was successful, on reboot, it would not boot the system. It would get a purple splash on my screen, then either lockup or go to a text based screen dump. *Server Platforms* said this was a text based OS and couldn't explain the purple flash or the error... I shelved this project until later and thought nothing more of it.
 
I checked for updates through the weekend (even though there usually isn't any on weekends), and as usual it said everything was up-to-date.
 
Third, Monday the "Update Manager" said there was too many updates to do at once, that it needed to do a partial update. I selected, but it couldn't complete, because it said that there was conflict on a KDE package that it said it needed to remove, but couldn't because it was in a blacklist. It further said that this could have resulted from a DEV vervion of Ubuntu.
 
Fourth, I upgraded some packages through the Synaptic Package Manager, to try to reduce the number of packages that the Update Manager was trying to update. All those packages said they updated fine. I then went back to the Update Manager and it still said it needed to do a partial update... but it completed and said it was successful. I noticed that the top of the dialog box was tiltled "Distrubution Upgrade." I noticed that some of the files seemed to be an xorg upgrade... After the update, I had to do other things, so I shut down my system.
 
That was the last time this machine has been able to start Ubuntu. When Ubuntu tried to startup, it said it had to boot in a low graphics mode, but could not- it blasted the monitor with vertical purple and red lines.
 
I had a copy of the Ubuntu Lucid LTS 10.05 64bit Desktop Edition LiveCD on my other machine. I burned a CD and tried. The only mode I can get to boot from the CD (on my machine) is in a text console- no xwindows system. On starting up an xwindows system will blast the grahics of the monitor, then (sometimes) continue to a monitor test-based screen dump that flashes by until the system locksup. 
 
This was the last screenful of one of the errors:
```

[    9.073882] [<ffffffffa010de4e>] nueveau_ramht_insert+0xee/0x300 [nouveau]
[    9.073882] [<ffffffff8113662f>] ? kmalloc+0x1bf/0x1f5/0x270 [nouveau]
[    9.073882] [<ffffffffa111240c>] nouveau_gpuobj_channel_init+0xe7/0x560 [nouveau]
[    9.073882] [<ffffffffa011240e>] ? nouveau_notifier_init_channel+0xfc/0x120 [nouveau]
[    9.073882] [<ffffffffa010bed7>] nouveau_channel_alloc+0x2d2f7/0x570 [nouveau]
[    9.073882] [<ffffffffa010a9e5>] nouveau_card_intit_channel+0xfe/0x120 [nouveau]
[    9.073882] [<ffffffffa00659bd>] ? drm_vblank_init+0a12d/0x1eo [drm]
[    9.073882] [<ffffffffa010ae02>] nouveau_card_init+0x312/0x350 [nouveau]
[    9.073882] [<ffffffffa010b0c9>] nouveau_load+0x219/0x5f0 [nouveau]
[    9.073882] [<ffffffffa00677cf>] drm_get_dev+0x15f/0x270 [drm]
[    9.073882] [<ffffffff81080cf0>] ? do_work_for_cpu+0x0/0x30
[    9.073882] [<ffffffffa0168b00>] nouveau_pci_probe+0x17/0x20
[    9.073882] [<ffffffff812ce6f7>] local_pci_probe+0x17/0x20
[    9.073882] [<ffffffff81080d08>] do_work_for_cpu+0x18/0x30
[    9.073882] [<ffffffff81084fa6>] kthread+0x96/0xa0
[    9.073882] [<ffffffff810141ea>] child_rip+0xa/0x20
[    9.073882] [<ffffffff81014f10>] ? kthread+0x0/0xa0
[    9.073882] [<ffffffff810141e0>] ? child_rip+0x0/0x20
[    9.076311] Clocksource bsc unstable(delta=4686959989 ns)

```I hand copied and typed this out, as there was no way to dump the error to a file...
 
**Ideas/Theories:** I'm thinking that this failure may be a intermediate upstream xorg issue- where xorg may be having problems with multiple instances of a graphics card. 
 
This machine has two SLI-bridged "XFX nVidia Geforce 6800GT Ultra SLI" video cards. Alan Coopersmith helped me resolve some issues with Solaris/OpenSolaris when I had problems with an upstream xorg change that lost compatibility with multiple instances of a video card- where SLI technology exists. Furhter upstream updates of xorg regained this compatibity. 
 
**Question:** Is this where my problems are coming from now with Ubuntu Lucid LTS 10.04 64bit Desktop Edition?
 
**Please Help!!!** ](*,)

---

### Post by MAFoElffen on 2010-07-22
In the absence of any advice, More Info and Questions...
 
I had previously added Debian.org to my software source list.  I didn't see this as a problem at the time as Ubuntu is Debian based.  I'm wondering if during the Synaptic Package Manager's Update package process, if it could have update da package depenciy and caised this error...  I don't know as of yet and I'm reaching for answers.
 
Going through my journal, I did add a few packages this weekend.  These packages were mostly games for my fiance.
 
One other package was ZFS-Fuse.  Had been working with ZFS-Fuse.net on issues with 0.6.9, but as of Saturday... I've been waiting on resolution of a Bug report.
 
Xorg.  I know that my past issues were confirmed after I physically removed one of the two video cards and retested.  I'll do that and see if Ubuntu comes. Up.
 
After it comes up, I'll backup the xorg config, xorg log and xorg error log and grab them to go through...  If it doesn't come up, I'll boot it from a working linux LiveCD and grab them.

---

### Post by MAFoElffen on 2010-07-22
Okay.  I removed one of my video cards.  Ubuntu will still not boot from my hard drive... But it is now "different"...

It still says it needs to come up in a Low Graphics mode.  From there I could review tht the xorg log:
```
X Orgxserver 1.7.6 Release Date 2010-3-17

X Protocol Version 11, Revision 0

Build Operating System Kernel build 2.6.2427-server x86 Ubuntu

Current OS Linux 2.6.32-23 generic#37 SMP FriJun 11 08.03.20 UTC 2010 x86_64

Kernel Command Line=/boot/vmlinux-2.6.32-23-generric root=UUID=8024e731-87f9-4956-aee1-538294713ce ro qiet splash

Build date 16 June 20 9.34,29 AM

xorg-server 2:1.7.6-2ubuntu7.2
Current version of pixman: 0.16.4

(...It goes on to identify, test and init drivers for the Monitor, vidoeo card, keybourd and mouse- with no errors!!!)

```There were no errors found there.  In fact I also reveiwed the Startup Error Log- and also found no errors.  I reviewed the xorg.conf and it was all default kind of stuff for a default nvidia drver....

Upon booting that system in low graphics, it did go to the Ubuntu Splash Screen with the roaming red dots... where it locks up (dots still roaming- left to right)!

But-  It now boots from the LiveCD image!~!!!  Everything on this machine told me I was getting past xorg before it locked.  On the LiveCD, it will not boot with multiple-instances of the same video card- but it will on the same machine with one video card.

Okay,  I'm lost again!!! HELP!!!

---

### Post by MAFoElffen on 2010-07-22
So.  There was a recent "Distribution Upgrade."   In the xorg log, it says it has a newer biuld for the kernel and for xorg.  Somewhere in all that, I lost compatibility with Ubuntu... Or conversely Ubuntu lost compatiability with me.

It seems from recent other posts from users, I am not alone with these "new" problems.

What do I do now?  Anyone?

---

### Post by MAFoElffen on 2010-07-23
Intermediate Success and Failure:
(still in the absence of anyone's advice from here...)
 
Without the second video card, not only did the LiveCD start working--- But Ubuntu Server can now boot. This was strange, as "Server Platforms" told me thiat the Server Edition was text based, so that it couldn't lock up by not initializing a graphics mode. I guess there is a problem in that.
 
When I latter went into Ubuntu Desktop on my machine- Instead of continuing to boot in a low graphics mode, I went to diagnose problem. tehn I went into a tty based terminal console. I then typed in "startx" and it booted into the xwindows system!!!
 
After getting into xwindows, I then got a system message saying:
```
An error occurreed, please select Package Manager from 
the right click menu or apt-get in a terminal to see what is wrong.  
The error meassage was: " Error: BrokenCount . 0" This usaully 
means that your installed packages have unmet dependencies.
```
When I started up the Sysnaptic Package Manager, it had another error message saying:
```
You have 2 broken packages on your system!
Use the "Broken" filter to locate them.
```
In the left Status filter was now added a "Broken Package" filter. The 2 broken packages were kdelibs5 and libkdegnomes5, which were installed during the past 10.04beta upgrade. It said there were upgrades to these packages, but it could not because each was trying to overwrite '/usr/share/man8/kdeinit4.8.gz'. ...So I removed the two packages.
 
I went to the Update Manager, where it said that it could only do a partial update because of the number of updates. When I started the update it said it could not verify a number of packages because of missing certificates. Reviewing these packages- they were mostly packages that were there from the beta release of 10.04. I continued.
 
It said (again) that it was doing a "Distribution Upgrade" and had two errors. The first ws a grub update. It let me review the differences, then continued saying that if it didn't work that I "might" have to run "update-grub".
 
The second error was a message saying that they was a problem with a dependency based boot application and gave me instructions to repair. I copied the instructions and continued. It said it finished with errors, but asked me to reboot.
 
I should have ran "update-grub" before I rebooted!!! I probly should have also repaiered that dependency based application. Now it locks up on boot after the grub menu, saying that device "8024e731-87f9-4956-aee1-5382947413ce" can not be found. The only other option in the Grub menu (for the OS) is rescue mode, which locks up after findind storage devices...
 
Now I'm lost again.

---

### Post by MAFoElffen on 2010-07-24
There doesn't seem to be a clear migration path from Ubuntu Lucid LTS 10.04 beta Desktop to 10.04.1....  Most of my problems seem to arise from missing certificates and authentication errors.

It was time to start over with a fresh install.  I backed up my home directories and source files.  I made a list of packages... Then reinstalled from a LiveCD. 

I had to download NVidia's drivers agaiin... and run "nvidia-xconfig" to start and configure them.  When i get through "installing" packages and configuring it to where I had things, I'll put my second SLI card back in, rerun "nvidia-conf" for "sli enable" and see what happens....

Oh well.  At least I have a "clean" system again. LOL

---

### Post by MAFoElffen on 2010-07-24
I installed my second SLI card (SLI-bridged) and reconfigured "nvidia-config".  Installed all my packages and such back into a clean new system...

All in Ubuntu Lucid LTS 10.04.1 is working fine for now.  I can (again) multi-boot WIN7, Windows Vista, OpenSolaris... But not Ubuntu Lucid LTS 10.04 Server Edition.

I know (now) that the server edition will not boot with "multiple instances of the same card."  I can't get help on that from anyone on the "Server Platforms" forum as they don't see that as a "server" issue.  Even thogugh they said that that edition is a "text-based only distro", it's generic/default video driver can't get around that.

I'm wondering if I could somehow install a current NVidia driver into the server edition(?)  Just thinking out loud.  This thread "problem" is solved.
:popcorn:

---

