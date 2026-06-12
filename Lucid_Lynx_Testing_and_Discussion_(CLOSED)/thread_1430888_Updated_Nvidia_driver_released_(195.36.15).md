---
title: "Updated Nvidia driver released (195.36.15)"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alexmurray on 2010-03-15
Should fix the fan problems in recent drivers, and hopefully fix a crash on X when resuming from suspend:

Fixed a bug that caused the X server to crash when rendering occurred while the X server was not on the active VT.
Fixed a regression that caused the driver to fail to properly adjust the GPU fan speed on some GPUs.
Fixed a bug that prevented performance level transitions on recent GPUs with SDDR3 and GDDR5 memory.

[http://www.nvnews.net/vbulletin/showthread.php?p=2209577](http://www.nvnews.net/vbulletin/showthread.php?p=2209577)

Anyone able to build it in a PPA?

---

### Post by CodeRage on 2010-03-16
I just went to the link you posted ([http://www.nvnews.net/vbulletin/show....php?p=2209577](http://www.nvnews.net/vbulletin/show....php?p=2209577)) and downloaded the NVIDIA-Linux-x86_64-195.36.15-pkg2.run file, which actually supports my GeForce GTS 360M (running Ubuntu 9.10 64bit, kernel 2.6.31-20-generic). After downloading, I quickly tapped out CTRL+ALT+F2 and did 
```
sudo gdm-stop
``` Then changing to the directory I downloaded the file to, I ran ```
sudo sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run
``` Then I opted to do ```
sudo reboot
``` instead of just restarting the gdm with sudo gdm. 

It did a nice job uninstalling the 195.36.08 driver I was previously using, and squaring away some peace of mind for me knowing the fan issue should be resolved. 

There is only one issue I have, which existed with all previous drivers I had used since purchasing this new Toshiba X505-Q870 over a week ago (185 - recalled 195.36.08 ). That issue is the wacky artifacts displaying on the lower 2/3 of the shutdown screen. I'll be researching into this matter and working hard to resolve it. :) Another thing coming to mind is when I run nvidia-settings, the screen blanks for a second, then the gui comes up. 

Speaking of nvidia-settings, I have witnessed the 'adaptive' setting of powermizer working correctly by watching the levels of 0,1, and 2 change right there in front of my eyes! I have also seen thermal settings adjusting (mostly in the range of 40 - 55 degrees) despite a pretty robustly configured compiz fusion. 

Nice job nVidia, thanks ArronP (at nVidia), and Linux community. :D

---

### Post by Half-Left on 2010-03-16
Just for your information. When you install the NVIDIA driver manually, you don't have to reboot. In OpenSUSE you just have to logout and back in again for the NVIDIA binary driver to work.

I'm not sure why Ubuntu requires a reboot to get the driver working when you install it from the Hardware Manager.

---

### Post by vishalrao on 2010-03-16
i think its now something like "sudo service gdm (re)start" if you catch my drift? (no need to restart)

---

### Post by blakamin on 2010-03-16
With my nvidia laptop, the wacky artifacts are normally a kernel framebuffer issue. "set gfxpayload=keep" normally works for me.

---

### Post by AaronP_ on 2010-03-17
> **CodeRage said:**
> There is only one issue I have, which existed with all previous drivers I had used since purchasing this new Toshiba X505-Q870 over a week ago (185 - recalled 195.36.08 ). That issue is the wacky artifacts displaying on the lower 2/3 of the shutdown screen. I'll be researching into this matter and working hard to resolve it. :)
Somebody tracked this down to a bug in usplash, where it fails to clear the entire screen and instead only draws to 2/3 of it.  I haven't tried blakamin's suggestion, but it sounds plausible.

---

### Post by hype on 2010-03-17
When you install the .run version, you actually get a warning saying something like :
"the pre-installation scripted shipped with your distribution failed" or something like this, right?

I beleive it's safe to go past the warning?
I was a bit affraid of exploding X :)

---

### Post by hype on 2010-03-17
Just installed new version: you actually have to reboot, if not X will crash.

---

### Post by Mazza558 on 2010-03-18
I tried this latest driver and all I get is an error just after the module's being built that nvidia.ko couldn't be loaded. Anyone have any ideas?

EDIT: Never mind, fixed it.

---

### Post by Half-Left on 2010-03-18
> **hype said:**
> Just installed new version: you actually have to reboot, if not X will crash.

It shouldn't do that at all. In every distro I tried over the years, I've always done it the same way:

Stop xorg, run the installer, start xorg or the login manager again.

---

### Post by meborc on 2010-03-18
> **Half-Left said:**
> It shouldn't do that at all. In every distro I tried over the years, I've always done it the same way:

Stop xorg, run the installer, start xorg or the login manager again.

yeah, the beauty of linux... only reboot when kernel updates come through ;)

---

### Post by ubername on 2010-03-18
I am struggling - I can't get X to start at all. After downloading and running sudo sh NVIDIA....

my screen flickers a lot on attempting to start x / gdm and I get a lot of errors ending with
'maximum number of x display failures reached...'
I get 
> Mar 18 18:21:38 USBKarmic kernel: [   46.974822] NVRM: API mismatch: the client has the version 195.36.15, but
Mar 18 18:21:38 USBKarmic kernel: [   46.974825] NVRM: this kernel module has the version 195.36.08.  Please
Mar 18 18:21:38 USBKarmic kernel: [   46.974826] NVRM: make sure that this kernel module and all NVIDIA driver
Mar 18 18:21:38 USBKarmic kernel: [   46.974828] NVRM: components have the same version.

in syslog.

How do I get the kernel module to update? The install process does not indicate errors.

Sorry the reporting of this is a bit patchy - I keep having to boot into the non-working version then back to a working version to post this!

---

### Post by Half-Left on 2010-03-18
> **ubername said:**
> I am struggling - I can't get X to start at all. After downloading and running sudo sh NVIDIA....

my screen flickers a lot on attempting to start x / gdm and I get a lot of errors ending with
'maximum number of x display failures reached...'
I get 

in syslog.

How do I get the kernel module to update? The install process does not indicate errors.

Sorry the reporting of this is a bit patchy - I keep having to boot into the non-working version then back to a working version to post this!

Did you remove the NVIDIA driver first? i.e the one install by the hardware Manager? Also nvidia-common can cause issues.

---

### Post by ubername on 2010-03-18
> Did you remove the NVIDIA driver first? i.e the one install by the hardware Manager? Also nvidia-common can cause issues.

I don't think I had installed the previous drivers from Hardware drivers - I think it was straight from the previous NVIDI...pkg.run

What should I do, bearing in mind I can't get into X?

Thanks for the reply BTW

---

### Post by Half-Left on 2010-03-18
> **ubername said:**
> I don't think I had installed the previous drivers from Hardware drivers - I think it was straight from the previous NVIDI...pkg.run

What should I do, bearing in mind I can't get into X?

Thanks for the reply BTW

Try this: 

```
sudo rmmod nvidia
```

```
sudo nvidia-installer --uninstall
```

Now run the package again.

---

### Post by ubername on 2010-03-18
Just tried that, still same results

> Mar 18 20:43:56 USBKarmic sudo:     john : TTY=tty1 ; PWD=/home/john ; USER=root ; COMMAND=/sbin/rmmod nvidia
Mar 18 20:44:15 USBKarmic sudo:     john : TTY=tty1 ; PWD=/home/john ; USER=root ; COMMAND=/usr/bin/nvidia-installer --uninstall
Mar 18 20:44:44 USBKarmic sudo:     john : TTY=tty1 ; PWD=/home/john ; USER=root ; COMMAND=/bin/sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run
Mar 18 20:44:49 USBKarmic sudo:     john : TTY=tty1 ; PWD=/home/john/Desktop ; USER=root ; COMMAND=/bin/sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run


Mar 18 20:46:32 USBKarmic kernel: [  232.853103] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.08  Thu Feb 25 04:10:13 PST 2010
Mar 18 20:46:32 USBKarmic kernel: [  232.857818] NVRM: API mismatch: the client has the version 195.36.15, but
Mar 18 20:46:32 USBKarmic kernel: [  232.857821] NVRM: this kernel module has the version 195.36.08.  Please
Mar 18 20:46:32 USBKarmic kernel: [  232.857823] NVRM: make sure that this kernel module and all NVIDIA driver
Mar 18 20:46:32 USBKarmic kernel: [  232.857824] NVRM: components have the same version.

Seems like a good track to pursue - if only I could get rid of 195.36.08?

---

### Post by gradinaruvasile on 2010-03-18
> **ubername said:**
> Just tried that, still same results
Seems like a good track to pursue - if only I could get rid of 195.36.08?

Solution here:

[http://www.nvnews.net/vbulletin/showthread.php?t=149052](http://www.nvnews.net/vbulletin/showthread.php?t=149052)

---

### Post by ubername on 2010-03-18
Thanks for all the help so far. I am still getting the problem and I am fairly sure that dkms is part of the problem.
/var/lib/dkms/nvidia-current contains a folder called 195.36.08 (not for 195.36.15) and then two other folders. one for current kernel and one for previous.

but I have tried various uninstalls, rebuilds of initramfs etc. to no avail. 

I must be nearly there and would welcome any further help!

---

### Post by gradinaruvasile on 2010-03-18
Well then remove all nvidia dkms modules with dkms. Then install the driver.

---

### Post by ubername on 2010-03-18
> **gradinaruvasile said:**
> Well then remove all nvidia dkms modules with dkms. Then install the driver.

Sorry to reveal my ignorance, but how would I do that?

---

### Post by sdowney717 on 2010-03-18
so step by step what is the proper procedure to get the driver to install and work?
> -> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   35.091554] vboxnetflt: no symbol version for SUPDrvLinuxIDC
   [   35.091555] vboxnetflt: Unknown symbol SUPDrvLinuxIDC
   [   42.280016] eth2: no IPv6 routers present
   [   53.548534] end_request: I/O error, dev fd0, sector 0
   [   53.572527] end_request: I/O error, dev fd0, sector 0
   [  373.758500] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [  467.184960] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  467.184962] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  467.184963] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  467.184964] NVRM: device(s).
   [  467.184965] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  467.184966] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  467.184966] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  467.184968] NVRM: No NVIDIA graphics adapter probed!
   [  487.302222] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
   [  487.304291] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc:
   initialised FIFO 2
   [  869.812646] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [  923.216759] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  923.216761] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  923.216761] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  923.216762] NVRM: device(s).
   [  923.216763] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  923.216764] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  923.216765] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  923.216766] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by nhasian on 2010-03-19
sdowney717,

let me know if/how you resolved the issue.  I'm getting the same error message as you when trying to install the nvidia driver.

---

### Post by cascade9 on 2010-03-19
I'm suprised how many people are actually interested in a prerelease driver.Its not even beta...fair enough if you want to test it, but I really think that its best to be avoided for the vast majority of uses. Even for people running a development release. ****

---

### Post by meborc on 2010-03-19
> **cascade9 said:**
> I'm suprised how many people are actually interested in a prerelease driver.Its not even beta...fair enough if you want to test it, but I really think that its best to be avoided for the vast majority of uses. Even for people running a development release. ****

I guess the problem right now is that the 2 drivers that are supposed to be stable actually have the showstopper fan bug issue :) so people are really eager to get the next one instead of downgrading to an older driver

---

### Post by cascade9 on 2010-03-19
> **meborc said:**
> I guess the problem right now is that the 2 drivers that are supposed to be stable actually have the showstopper fan bug issue :) so people are really eager to get the next one instead of downgrading to an older driver

Once they are pulled, IMO, its better to downgrade to the last stable drivers (currently 190.53) or maybe the beta drivers (currently 195.30). Its not like there is a massive perfromance difference between the pulled 195.36.03/08 and the 190.53 (I'm guessing less than 1%) or any new features (that I'm aware of, please tell me if I'm wrong). 

I wouldnt trust prerelease drivers at all myself. If they put them up on the nVidia site I might trust them more. Hopefully they do soon, because the 195.36 driver appears to support some of currently unsupported cards, like the 230M and some of the 3xx series. Still no support for the GT230 though nVidia has really made a hash of its support for some of the newer cards....

---

### Post by meborc on 2010-03-19
> **cascade9 said:**
> Once they are pulled, IMO, its better to downgrade to the last stable drivers (currently 190.53) or maybe the beta drivers (currently 195.30). Its not like there is a massive perfromance difference between the pulled 195.36.03/08 and the 190.53 (I'm guessing less than 1%) or any new features (that I'm aware of, please tell me if I'm wrong). 

I wouldnt trust prerelease drivers at all myself. If they put them up on the nVidia site I might trust them more. Hopefully they do soon, because the 195.36 driver appears to support some of currently unsupported cards, like the 230M and some of the 3xx series. Still no support for the GT230 though nVidia has really made a hash of its support for some of the newer cards....

true, true :) but then again we are talking about this in lucid development forum... people are running an alpha (ok, beta today) version of an OS anyway

---

### Post by OliW on 2010-03-19
> **cascade9 said:**
> I'm suprised how many people are actually interested in a prerelease driver.

What an odd thing to say to people in a forum dedicated to pre-release versions of Ubuntu. Everybody here is testing pre-release software for some reason: they want/need the latest and greatest, they want to help test and report bugs or they just plain want to punish themselves.

I know I tick all three of those boxes.


> **cascade9 said:**
> Its not even beta...

No it's not beta, it's what happens **after** beta. It's a release candidate with a different name.


To others wondering how to get it installed, here's my recipe for success:

Step 1: Switch to a TTY and kill X. You can do this with `sudo stop gdm`. If you booted into a failsafeX mode, just select the root console option. If you still have problems, wang up htop and slaughter any remaining X processes.

Step 2: `sudo sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run`

If you have upgraded your kernel to 2.6.33 (as I have), you'll need  `sudo env CC="gcc-4.2" sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run` to avoid the nasty compiler version messages.

Step 3: `sudo start gdm`

---

### Post by Half-Left on 2010-03-19
> **sdowney717 said:**
> so step by step what is the proper procedure to get the driver to install and work?

As usual the nouveau driver is taking ownership, so remove it, blacklist it or rmmod "modulename" any nouveau module from lsmod readout. If you're not experienced enough for this, just wait for the new release to come in the Hardware Manager or update.

---

### Post by chek2fire on 2010-03-19
The new nvidia driver will be upload to repositories or not? Because now we have in repositories the buggy driver with the fan problem.
This is a serious problem for nvidia users and is not correct to have that danger driver in LTS distro.

---

### Post by sdowney717 on 2010-03-19
[http://www.nvnews.net/vbulletin/showthread.php?p=2209577](http://www.nvnews.net/vbulletin/showthread.php?p=2209577)

[http://www.nvnews.net/vbulletin/showthread.php?t=149052](http://www.nvnews.net/vbulletin/showthread.php?t=149052)

from nvnews, I do think this is the fixed driver
Also mentioned dkms issue
- update-initramfs -u

So i switch to console
stop x
rmmod the nv driver
install nvidia driver

what to do if the driver fails and I need the nv driver back?
modprobe nv driver?
I will keep looking into this.

---

### Post by gradinaruvasile on 2010-03-19
> **ubername said:**
> Sorry to reveal my ignorance, but how would I do that?
I done that once, but i just googled around for it and used the man pages. Honestly dont remember exactly, but here is a comprehensive tutorial:

[http://www.linuxjournal.com/article/6896?page=0,1](http://www.linuxjournal.com/article/6896?page=0,1)

---

### Post by 3rdalbum on 2010-03-19
> **sdowney717 said:**
> 
So i switch to console
stop x
rmmod the nv driver
install nvidia driver

what to do if the driver fails and I need the nv driver back?
modprobe nv driver?
I will keep looking into this.

No, the issue is the nouveau driver, not the nv driver. I don't think rmmod'ing the nouveau driver will actually work, because you'll get an error message that "nouveau module is busy".

You need to open the /etc/modprobe.d/blacklist.conf file, and add:

```
blacklist nouveau
```

to the bottom. Then reboot and you can install the nvidia driver.

If the Nvidia driver fails, you need to blacklist 'nvidia', unblacklist 'nouveau', and modify xorg.conf to use 'nouveau' as the driver.

---

### Post by gradinaruvasile on 2010-03-19
> **sdowney717 said:**
> [http://www.nvnews.net/vbulletin/showthread.php?p=2209577](http://www.nvnews.net/vbulletin/showthread.php?p=2209577)

[http://www.nvnews.net/vbulletin/showthread.php?t=149052](http://www.nvnews.net/vbulletin/showthread.php?t=149052)

from nvnews, I do think this is the fixed driver
Also mentioned dkms issue
- update-initramfs -u

So i switch to console
stop x
rmmod the nv driver
install nvidia driver

what to do if the driver fails and I need the nv driver back?
modprobe nv driver?
I will keep looking into this.

The simple solution:
Just stop gdm, rmmod nvidia, delete/rename the /etc/X11/xorg.conf and start gdm again. The default opensource driver will load (be it nv or nouveau).
Deleting xorg.conf is not a problem anymore (and hasnt been since 8.04 or 8.10) - the system just loads its defaults.
Only problem would be if you have (really) customized xorg.conf - in this case you will have to customize it again to replace the "nvidia" with "nv" or "nouveau" and make sure you dont leave other conflicting settings.

---

### Post by Half-Left on 2010-03-19
Using nvidia-xconfig will enable the nvidia driver in there for you if you don't have it enabled.

If you need to change back, just change the driver line.

---

### Post by cascade9 on 2010-03-19
> **OliW said:**
> What an odd thing to say to people in a forum dedicated to pre-release versions of Ubuntu. Everybody here is testing pre-release software for some reason: they want/need the latest and greatest, they want to help test and report bugs or they just plain want to punish themselves.

I know I tick all three of those boxes.

Fair enough, I see your point. For myself, when I go changing things (and I would count alpha OSes as a massive change) I'd prefer a nice stable baseline on other stuff- like hardware drivers. I'm guessing that if your running stable drivers, and you get errors of any kind, you can assume (at least partially) that its the software, not the drivers (and yes, I am aware that drivers are software) 

But I'm not running alpha/beta versions of ubuntu, so my opnion can be discarded ;) (though in some ways, I'm a little ahead, I'm using Sid quite a bit these days) 

> **OliW said:**
> 
No it's not beta, it's what happens **after** beta. It's a release candidate with a different name.


Maybe. AFAIK, there isnt really any defined version of where 'pre-release' is (technically, everything thats not final is pre-release). 

If it was past beta, or even at beta then IMO it should be up on the nVidia site, not being released via forum posts on nvnews. IMO its pre-alpha in this case, though being based on the earlier released then pulled for bugs 195.36.15 might go though to a release version faster than otherwise. 

I'll bet that the current 195.30 get to release version before the 195.36.15, which will then appear as beta. Only time is going to tell on that though.

---

### Post by gradinaruvasile on 2010-03-19
I dont think so. Linux (and i think the other platforms too) drivers are released on nvnews forums (and FTP) days before they appear on the official site.

And i dont know if there will be 195.30 final because it is part of the 195 series, and subsequent versions are numbered differently - for example the corrected 195.36.08 is 195.36.15. Numbers only go up.

I do use this driver on 3 computers, no problems. The nvidia splash image that shows when loading the nvidia module (can be activated in xorg.conf) is not showing beta label - beta versions have the "beta version" red label on the image.

---

### Post by sdowney717 on 2010-03-19
> No, the issue is the nouveau driver, not the nv driver. I don't think rmmod'ing the nouveau driver will actually work, because you'll get an error message that "nouveau module is busy".

You need to open the /etc/modprobe.d/blacklist.conf file, and add:

Code:

blacklist nouveau

to the bottom. Then reboot and you can install the nvidia driver.

yes, thankfully, This worked.
On reboot after the blacklist, of course you get the major x cant start error so then simply select from the presented menu option 

boot to console mode
login in with your user and password
find your nvidia install file and run it

run the installer from command line like this, (I renamed it and you must make it executable before you can execute it)

sudo ./nvidia1953615.run
then
sudo reboot

as it installs, follow the prompts, you will get errors for symbolic links, etc. I got like 10 various file errors before the the installer actually finished the install. first off sort of discouraging to see all those.

On rebooting, I had to go to nvidia settings control panel and set my resolution. I then said apply, then preview. I select all, copy, opened xorg.conf and pasted over the contents. In the past I had to always do this since it could never save the changes.

now it is running 195.36.15

---

### Post by AaronP_ on 2010-03-19
> **cascade9 said:**
> If it was past beta, or even at beta then IMO it should be up on the nVidia site, not being released via forum posts on nvnews. IMO its pre-alpha in this case, though being based on the earlier released then pulled for bugs 195.36.15 might go though to a release version faster than otherwise. 
OliW is right, 195.36.15 is essentially a release candidate.  Getting the driver posted on nvidia.com requires jumping through a few more hoops than are necessary for posting on nvnews.net.  195.36.15 should be up on nvidia.com next week-ish (no promises, though!)

---

### Post by cascade9 on 2010-03-19
Its out already LMAO. **[Linux Display Driver Version 195.36.15]("http://www.nvidia.com/object/linux_display_amd64_195.36.15.html") [IMG]http://www.nvidia.com/content/DriverDownload/includes/images/us/recommended.jpg[/IMG]** 												195.3615 												March 19, 2010
Shows what I know ;) I'm going to have to have a look at the nvidia dev process, it doesnt work the way I was told it did :|

---

### Post by monkman on 2010-03-19
> If you have upgraded your kernel to 2.6.33 (as I have), you'll need `sudo env CC="gcc-4.2" sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run` to avoid the nasty compiler version messages.

i even installed gcc-4.2, but that doesn't work. the installation is crashing and freezing my system with some flashing "&#8364;" symbols...

ubuntu 9.10 64bit

---

### Post by monkman on 2010-03-19
i'm fine here with the 2.6.32 kernel and the nvidia 190.53 driver. that installed pretty fine.

---

### Post by sdowney717 on 2010-03-19
> Version:
	
195.36.15 Certified
Release Date:
	
2010.03.19
Operating System:
	
Linux 64-bit
Language:
	
English (U.S.)
File Size:
	
40.0 MB 

yes it is out and certified for use. I am running the 32 bit version.

scott@scott-desktop:~$ uname -r
2.6.32-16-generic

---

### Post by Half-Left on 2010-03-19
195.36.15 has just dropped into the updates. No need for a manual install now.

Really guys, you should have just waited.

---

### Post by 5735guy on 2010-03-20
How To Install Nvidia 185.xx, 190.xx and 195.xx Drivers In Ubuntu, From A Launchpad Repository
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

### Post by sdowney717 on 2010-03-20
I had a problem with 195.36.15 giving me white horizontal lines
So I dropped back to 195.30 and the lines no longer appear.

this guy said it destroyed his card, and for me it also has issues. So too risky for me.
[http://www.nvnews.net/vbulletin/showthread.php?t=149129](http://www.nvnews.net/vbulletin/showthread.php?t=149129)

---

### Post by atlee on 2010-03-21
> **3rdalbum said:**
> No, the issue is the nouveau driver, not the nv driver. I don't think rmmod'ing the nouveau driver will actually work, because you'll get an error message that "nouveau module is busy".

You need to open the /etc/modprobe.d/blacklist.conf file, and add:

```
blacklist nouveau
```to the bottom. Then reboot and you can install the nvidia driver.

If the Nvidia driver fails, you need to blacklist 'nvidia', unblacklist 'nouveau', and modify xorg.conf to use 'nouveau' as the driver.

@3rdalbum -->

Your a legend, this actually worked.
copy blacklist.conf to desktop, edit it, add blacklist nouveau to the end, save it
open terminal goto desktop dir, sudo cp back to /etc/modprobe.d folder
restart
open terminal
sudo stop gdm
sudo sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run
installed fine
restart using sudo start gdm, gfx crashed for me with a diff error but restarted computer and all is successful

Thanks man.

---

### Post by atlee on 2010-03-21
> **Half-Left said:**
> 195.36.15 has just dropped into the updates. No need for a manual install now.

Really guys, you should have just waited.

It's definitely not in updates not from my end.

---

### Post by seenthelite on 2010-03-22
I installed Beta 1 and have 195.36.15 as the recommended driver and it works too.

---

### Post by atlee on 2010-03-22
> **seenthelite said:**
> I installed Beta 1 and have 195.36.15 as the recommended driver and it works too.

it didn't work for me, clean install on a geforce 9800gt x-server crashed, if installing recommended proprierty driver still everytime x-server crashed, even restarting it did nothing, i had to blacklist nouveau driver then reinstall the driver from nvidia.com site.

---

### Post by jd65pl on 2010-03-23
> **3rdalbum said:**
> No, the issue is the nouveau driver, not the nv driver. I don't think rmmod'ing the nouveau driver will actually work, because you'll get an error message that "nouveau module is busy".

You need to open the /etc/modprobe.d/blacklist.conf file, and add:

```
blacklist nouveau
```

to the bottom. Then reboot and you can install the nvidia driver.

If the Nvidia driver fails, you need to blacklist 'nvidia', unblacklist 'nouveau', and modify xorg.conf to use 'nouveau' as the driver.

Thanks 3rdalbum, this worked for me

---

### Post by nickhopkins07 on 2010-03-23
Does anyone know if this release soves the problem of the previous 195.xx driver 'breaking' the audio over HDMI on ION machines? cheers.

---

