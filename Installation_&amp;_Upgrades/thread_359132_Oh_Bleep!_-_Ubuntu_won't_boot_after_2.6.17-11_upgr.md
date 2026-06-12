---
title: "Oh Bleep! - Ubuntu won't boot after 2.6.17-11 upgrade"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by cybrkup on 2007-02-11
I loaded the new 2.6.17-11 kernel yesterday and after rebooting earlier today - or at least trying to - I can't get past a command prompt for Kubuntu. I'm no expert, but GRUB appears to be loading. I get the option of what OS to use (I'm back to XP for now). It give me the option to go to 2.6.17-10 or 2.6.17-11 and recovery mode for both. None work fully.

Once I select one I see the regular KDE loading screen, but then it goes to a command prompt and I am asked to enter my logon id / password. That is the extent of my abilities to load ubuntu past that. I entered GRUB in the command prompt and tried to BOOT, but it errored out saying that I need to load a Kernel. I'm not sure how. 

Anybody got any suggestions on where to go now? I really don't want to have to reinstall. That seems like such a microsoft solution. 

The only other item that I think might be related is that two days ago I used a command to autoclean - something like that anyway. It was suggested by another ubuntu user as part of an install guide for sound in kaffine. That deleted a bunch of programs I actually use, although I have no idea if that actually caused this problem. I would tend to think not. 

Thanks in advance!

CybrKup

---

### Post by mikewhatever on 2007-02-11
That is not an infrequent problem these days, caused by the kernel update. Let me guess, do you have an nvidia graphic card?
What happens is, you system actually boots, but there is no GUI. Do you get any messages like 'xserver could not start'? As I said, many people experienced similar troubles. There should be a way to fix it though. By the way, here is the official message.
> Due to an unavoidable ABI change the Ubuntu 6.06 and Ubuntu
6.10 kernel updates have been given a new version number, which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

---

### Post by Patrick K on 2007-02-11
Here is how I got the GUI to work with nvidia drivers. If you are booting to a command prompt, type "nano /etc/X11/xorg.conf". This will start the nano editor with the xorg.conf file. Go to the line with "nvidia", it's nearer the bottom than the top. Change "nvidia" to "nv". I had to add "BusID	   "PCI:1:0:0"" but you may not need to. I didn't get a GUI without it. This will run the GUI on the generic nvidia driver.

After sorting out some other issues, I downloaded the newer ENVY script "envy_0.8.1-0ubuntu6_all.deb" installed it and ran it outside the GUI. I didn't let it automatically update xorg.conf. I did that myself. (Every time I have let ENVY do that I have had problems.) After changing "nv" to "nvidia" and making sure the bus ID is there, I rebooted and the nvidia drivers are working. One thing, the bus ID may be different on your system or might not be needed. Mine is an APG card if your's is PCI Express, I haven't a clue what would go there. You can try the bus ID I used. If it doesn't work, you're no worse off, just take it out. The GUI might run without it. HTH

---

### Post by cybrkup on 2007-02-11
Yep, I do have an NVIDA card. PCI, 5200 series. Unfortunately, I do not get any error msgs. That would make things a lot easier to figure out what the problem is. Next time I may not upgrade as readily.

I will give those suggestions a shot. Thanks for the detective work. 

Worst case I can always go back to my onboard video card just to get things running and then reinstall the nvidia drivers later. 

Thanks again!

CybrKup

---

### Post by cybrkup on 2007-02-11
My efforts thusfar have been fruitless so I would like a little more explicit help, if possible. 

I actually am getting an error msg: "Error 8: Kernel must be loaded before booting." I only get this once I use the command prompt to go to grub and boot. Of course, this was pretty obvious to begin with. 

I tried doing changing the xorg.conf file, but after that I couldn't figure out how to download the envy-0.8.1... file and install it. 

What I did try is to reinstall the nvidia drivers, remove the 2.6.17-11 build, switch to my onboard video controller, and to rebuild the xorg.conf file. None of those worked. 

BTW, my xorg.conf file already that the PCI:1:0:0 line in there. 

Can you please either tell me exactly how to download the necessary upgrade files or otherwise resolve this issue?

---

### Post by kweiner on 2007-02-11
I just ran into the same problem.  After the upgrade to 2.6.17-11, my system boots but X won't start.  The error message says:

FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!

Please help - I don't know where to go from here.

---

### Post by kweiner on 2007-02-12
> **kweiner said:**
> I just ran into the same problem.  After the upgrade to 2.6.17-11, my system boots but X won't start.  The error message says:

FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!

Please help - I don't know where to go from here.

I fixed my system by:

Changing from nvidia to nv driver in xorg.conf, rebooting, and then
going into synaptic, uninstalling linux-restricted-modules-2.6.17-10-generic, and installing linux-restricted-modules-2.6.17-11-generic.  After that I changed the driver from nv back to nvidia and rebooted once more.  Whew!  I am glad I was able to recover.

---

### Post by lojic on 2007-02-12
I was able to fix my Nvidia related X problem by installing the restricted modules for the -11 kernel as well.

It seems like a bug that the update didn't automatically ensure the restricted modules for -11 was installed if restricted modules for -10 were installed.

Anyone know the best place to report this?

---

### Post by Patrick K on 2007-02-12
Editing xorg.conf to "nv" is the trick to getting the GUI running again. After that installing the drivers is a piece of cake. 

You're lucky, in a way. My system would boot at all. The upgrade change the partition names and GRUB couldn't find menu.lst. I had to use the livecd and GParted to find out what the name of / was changed to then edit GRUB at boot up. During this time I didn't have internet access, so I was on my own. From the command line I edited xorg.conf (nvidia to nv) and got X running. 
I then edited menu.lst and was able to boot directly to the GUI. /home was still out of whack but I finally got that fixed.

---

### Post by cybrkup on 2007-02-12
I did try editing the xorg file to use nv instead of nvidia, but it didn't work. That solution seems pretty simple so I'm not sure why it didn't work. 

Now I have a much bigger problem though. I spent so much time jacking with my computer that I somehow royally messed it up. I can't boot to windows now and when I tried to reinstall off the ubuntu cd gparted wont work. It just keeps going forever without finding my drives. Not good. :(

---

### Post by halfvolle melk on 2007-02-12
Can you still boot into recovery mode? If so run this command
```
dpkg reconfigure xserver-xorg
```
That should bring back basic functionality of X and then you can take it from there.

---

### Post by mikewhatever on 2007-02-12
It looks like the problem now is how to rescue Windows. Have you tried booting into Windows using Windows installation CD? If you can get into recovery console and type 'fdisk /mbr', hopefully it would fix Windows boot process. Another good tool can be downloaded form [www.bootdisk.com](www.bootdisk.com). I was going to try to solve the new kernel issue on my laptop, but now, I'll think twice before.

---

### Post by lojic on 2007-02-12
> **lojic said:**
> I was able to fix my Nvidia related X problem by installing the restricted modules for the -11 kernel as well.

It seems like a bug that the update didn't automatically ensure the restricted modules for -11 was installed if restricted modules for -10 were installed.

Anyone know the best place to report this?
I forgot to give credit to the original poster who saved me from trying a more complicated solution:

[http://ubuntuforums.org/showpost.php?p=2133441&postcount=343](http://ubuntuforums.org/showpost.php?p=2133441&postcount=343)

Just to clarify exactly what I did:
1) booted into the -10 kernel
2) used synaptic to install linux-restricted-modules-2.6.17-11-generic
3) booted into the -11 kernel which then worked fine

So I didn't need to mess with xorg.conf since booting into the -10 kernel had a working GUI.

---

### Post by cybrkup on 2007-02-12
> Can you still boot into recovery mode? If so run this command
Code:

dpkg reconfigure xserver-xorg

That should bring back basic functionality of X and then you can take it from there.

I saw that in another post elsewhere and tried it with no success. I don't remember the exact error msg (I did this late last night), but it was something along the lines of the file was broken and not recoverable. 

I can get into recovery mode, but at this point I want to start clean. I just installed Xubuntu on what used to be my Windows drive but now I can get to my data drive on HDA. I posted a new thread on this here: [http://www.ubuntuforums.org/showthread.php?t=359750]("http://www.ubuntuforums.org/showthread.php?t=359750")

---

### Post by IgnorantGuru on 2007-02-12
If someone can answer a few questions for me I'd appreciate it - trying to get a handle on what's happening here.

I'm using Kubuntu Edgy with a GeForce 6200TD 128M AGP.  I recently did a kernel update through Adept Notifier and X wouldn't start.  Got the "error running install command for nvidia".  I rolled the system back using a partition image I had, so now I'm back to the pre-upgrade point.  Here is what I have listed in Adept Notifier:

```
linux-headers-2.6.17-10   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-headers-2.6.17-10-generic   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-headers-2.6.17-11   (install)
    Candidate version: 2.6.17.1-11.35

linux-headers-2.6.17-11-generic   (install)
    Candidate version: 2.6.17.1-11.35

linux-headers-generic   (upgrade)
    Candidate version: 2.6.17-11
    Installed version: 2.6.17-10

linux-image-2.6.17-10-386   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-image-2.6.17-10-generic   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-image-2.6.17-11-generic   (install)
    Candidate version: 2.6.17.1-11.35

linux-image-generic   (upgrade)
    Candidate version: 2.6.17.11
    Installed version: 2.6.17.10

linux-libc-dev   (upgrade)
    Candidate version: 2.6.17.1-11.35
    Candidate version: 2.6.17.1-10.33

linux-restricted-modules-2.6.17-10-386   (upgrade)
    Candidate version: 2.6.17.7-10.1
    Installed version: 2.6.17.6-1

linux-restricted-modules-common   (upgrade)
    Candidate version: 2.6.17.7-11.1
    Installed version: 2.6.17.6-1

nvidia-glx   (upgrade)
    Candidate version: 1.0.8776+2.6.17.7-11.1
    Installed version: 1.0.8776+2.6.17.6-1
```

My questions:
Why is Adept trying to upgrade the kernel and install the new kernel at the same time?  Is this right?  Do I want two kernels?

Why is Adept trying to upgrade the restricted modules to both 2.6.17-10 and 2.6.17-11?

What do I do?  Should I deselect some of these?  Or should I upgrade it all and then remove something?

FYI, after the last upgrade I tried
```
apt-get install nvidia-glx nvidia-kernel-common
```

It said I had the latest versions already.  So I removed them and installed them, but no change - nvidia module wouldn't load.

Also, I looked for /lib/modules/2.6.17-10-generic/kernel/drivers/video/nvidia.ko  and it was missing.  There was a nvidiafb.ko instead.  Normal?

Would I be better to wait until this is fixed so the system doesn't get messed up for future upgrades?

Thanks for any suggestions.

---

### Post by BLTicklemonster on 2007-02-12
Thanks for the info, guys, I'm going to try this out tonight.

---

### Post by karachuonyo on 2007-02-12
I too had a similar problem with the system failing to start X server after the upgrade. However i was able remove the old nvidia glx and restricted module headers and re-installing nvidia drivers.  I'm not sure the code quoted above "dpkg reconfigure xserver-xorg". is correct, I've only ever used 
code
 dpkg reconfigure -phigh xserver-xorg 
  
to restore basic gui functions.

---

### Post by BLTicklemonster on 2007-02-13
Tried booting again. Of course, I was stuck at the blinker again after being told that X would not start and why.

So I pressed ctrl+alt_F1 (out of frustration more than anything else) and voila, I was at the command line log in. So I didn't have to go to recovery mode.

I logged in, ran sudo dpkg-reconfigure xserver-xorg (never phighed it before, so I don't know exactly what that does...) and set my card to nv and ran all the way through the baloney, and started x and of course was confronted with a nasty desktop, but a desktop all the same.

I downloaded a new version of envy, installed it, pressed ctrl+alt+F1, logged in, entered envy at the command line, and ran the installation program, then started x, but my display looked like crap still. Aha, sudo gedit /etc/X11/xorg.conf and added 1600x1200 to my screensize at 24 colors, then changed my driver from nv to nvidia, saved, rebooted, and was welcomed with a beeyootiful desktop.

Woot woot.

Now to configure.pl vmware and anything else that's dorked out on me.

---

### Post by BLTicklemonster on 2007-02-13
> **IgnorantGuru said:**
> If someone can answer a few questions for me I'd appreciate it - trying to get a handle on what's happening here.

I'm using Kubuntu Edgy with a GeForce 6200TD 128M AGP.  I recently did a kernel update through Adept Notifier and X wouldn't start.  Got the "error running install command for nvidia".  I rolled the system back using a partition image I had, so now I'm back to the pre-upgrade point.  Here is what I have listed in Adept Notifier:

```
linux-headers-2.6.17-10   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-headers-2.6.17-10-generic   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-headers-2.6.17-11   (install)
    Candidate version: 2.6.17.1-11.35

linux-headers-2.6.17-11-generic   (install)
    Candidate version: 2.6.17.1-11.35

linux-headers-generic   (upgrade)
    Candidate version: 2.6.17-11
    Installed version: 2.6.17-10

linux-image-2.6.17-10-386   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-image-2.6.17-10-generic   (upgrade)
    Candidate version: 2.6.17.1-10.34
    Installed version: 2.6.17.1-10.33

linux-image-2.6.17-11-generic   (install)
    Candidate version: 2.6.17.1-11.35

linux-image-generic   (upgrade)
    Candidate version: 2.6.17.11
    Installed version: 2.6.17.10

linux-libc-dev   (upgrade)
    Candidate version: 2.6.17.1-11.35
    Candidate version: 2.6.17.1-10.33

linux-restricted-modules-2.6.17-10-386   (upgrade)
    Candidate version: 2.6.17.7-10.1
    Installed version: 2.6.17.6-1

linux-restricted-modules-common   (upgrade)
    Candidate version: 2.6.17.7-11.1
    Installed version: 2.6.17.6-1

nvidia-glx   (upgrade)
    Candidate version: 1.0.8776+2.6.17.7-11.1
    Installed version: 1.0.8776+2.6.17.6-1
```

My questions:
Why is Adept trying to upgrade the kernel and install the new kernel at the same time?  Is this right?  Do I want two kernels?

Why is Adept trying to upgrade the restricted modules to both 2.6.17-10 and 2.6.17-11?

What do I do?  Should I deselect some of these?  Or should I upgrade it all and then remove something?

FYI, after the last upgrade I tried
```
apt-get install nvidia-glx nvidia-kernel-common
```

It said I had the latest versions already.  So I removed them and installed them, but no change - nvidia module wouldn't load.

Also, I looked for /lib/modules/2.6.17-10-generic/kernel/drivers/video/nvidia.ko  and it was missing.  There was a nvidiafb.ko instead.  Normal?

Would I be better to wait until this is fixed so the system doesn't get messed up for future upgrades?

Thanks for any suggestions.

Well, nobody answered you, so I'll make something up so you'll have something to ponder until someone comes along with the right answer.

You see, these little elves in your computer know that if you install a new kernel, there could be problems, so they keep an old kernel laying around so you can boot to it instead of the new one, if you do have problems. Like my problem, if I hadn't had my old kernel to boot to, I'd been in a bind. So leaving that old kernel is a great idea. (not sure how to get rid of it once you decide you can live without it, though, unless it's a simple as removing it using synaptic).

Now the video drivers are dependent upon your kernel, and sometimes the new kernel upgrade will be such that you will need to install your video driver again so that it will jive with your kernel. Shame there's no kernel upgrade program (made by tseliot... I bet a ham sandwich and a bag of chips he could make one) that would automatically pick up on the video driver problem and install a new one for you, but I'm sure that won't be necessary down the road with all the wizards at canonical get things ironed out. I mean they want Ubuntu to be a mainstream desktop, so certainly that will be a primary consideration, to make kernel upgrades go off without leaving ANYONE staring at their screen wondering what they were thinking when they made that post here about how they just yesterday completely removed windows from their computer, you know. whew.

Adept is trying to load what your sources.list tell it to load, which is why you're trying to load restricted modules. The rest... I'm not so sure of.

Make sense? Maybe not the exact answer you wanted, but close enough for government work...

---

### Post by IgnorantGuru on 2007-02-13
Thanks - I think I'm getting a handle on that multiple kernel business.  In my case, grub is still loaded from my old SUSE partition, so I don't think I'll have that option.

From what I've read it sounds like if I do the update and then explicitly install the -11 restricted modules it might work.  I think I'll wait a bit (in case they fix it) and then give it another whirl.

---

### Post by IgnorantGuru on 2007-02-13
Well so much for waiting a few days.  :)  I want to try beryl and figured no point doing so with old kernel/video driver.

For the record, I first upgrade the -10 kernel and headers, but didn't install anything for -11, including the new nvidia-glx.  Rebooted and all was well.

Then I installed the -11 offerings in Adept.  Rebooted and X failed to start.  Then in console

```
sudo apt-get install linux-restricted-modules-2.6.17-11-386
```

Rebooted and all appears to be well - no dreaded EE's in X log.

BTW if anyone knows why I should install linux-restricted-modules-2.6.17-11-generic in addition to -386, please tell me.

So it appears that the Adept Notifier is for whatever reason not installing the new restricted modules when it does the kernel upgrade - seems like broken behavior to me.

---

### Post by Pollywoggy on 2007-02-13
> **Patrick K said:**
> Editing xorg.conf to "nv" is the trick to getting the GUI running again. After that installing the drivers is a piece of cake. 

You're lucky, in a way. My system would boot at all. The upgrade change the partition names and GRUB couldn't find menu.lst. I had to use the livecd and GParted to find out what the name of / was changed to then edit GRUB at boot up. During this time I didn't have internet access, so I was on my own. From the command line I edited xorg.conf (nvidia to nv) and got X running. 
I then edited menu.lst and was able to boot directly to the GUI. /home was still out of whack but I finally got that fixed.

I had what I believe to be the same problem after I upgraded.  I rebooted to a BusyBox (initramfs) prompt and that is where the machine left me, with some error about not finding a tty.

This happened to me twice and I discovered after my third install that the problem was my fstab somehow had been changed to use some sort of numeric ID's in place of the traditional /dev/hdN.  My fix, not necessarily the right fix, was to change my fstab back to the traditional format.  I rebooted successfully after that.

I did not use the official upgrade method, which I did not know about since I am new to Ubuntu (but not to Linux).  Perhaps that is where I went wrong.

---

### Post by Dragonstar on 2007-02-13
I guess my problem is related to this, although I have ati graphic card. After the kernel upgrade my system worked fine, or so I thought. I didn't have 3d-acceleration so I noticed my system was missing the new version of restricted modules. I installed them and boom, X didn't start anymore. I tried to fix the problem by reading these forums. Uninstalled fglrx-driver and restricted modules and then instelled them again, but with no results. I now also have this same problem if I use kernel- and restricred modules-version -10.

So now my X won't start if I have proper restricted modules installed, without them X starts but I don't have direct rendering. Help?

---

### Post by IgnorantGuru on 2007-02-13
When you don't have direct rendering, take a look in /var/log/Xorg.0.log and see what the errors are, or post it here.  

"Install the driver manually" worked well for me from here...
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by Dragonstar on 2007-02-14
Now I have managed to start X with restricted modules installed. But for X to start I have to disable "composite disable" from xorg.conf, so I still don't have direct rendering. What's wrong with that? 

To original problem. There's no errors (EE) in my Xorg.0.log when X won't start. Although that log is mumbo jumbo to me I'll paste the end of it, in case of it means something:

```
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb78d4000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.28.8
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17-11-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [agp] Mode=0x1f000a1b bridge: 0x1106/0x0282
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xd0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe8000000 FBMappedSize: 0x00701000
(II) fglrx(0): Splitting WC range: base: 0xe8000000, size: 0x701000
(II) fglrx(0): Splitting WC range: base: 0xe8400000, size: 0x301000
(II) fglrx(0): Splitting WC range: base: 0xe8600000, size: 0x101000
(==) fglrx(0): Write-combining range (0xe8700000,0x1000)
(==) fglrx(0): Write-combining range (0xe8600000,0x101000)
(==) fglrx(0): Write-combining range (0xe8400000,0x301000)
(==) fglrx(0): Write-combining range (0xe8000000,0x701000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
```

I'd paste the whole log, but the forum says it's too long.

---

### Post by IgnorantGuru on 2007-02-14
That log looks good.

Also " In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI."

It is correct to have this in xorg.conf:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

fglrxinfo should report something like this, in which case you're good...
```
$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

---

### Post by Dragonstar on 2007-02-14
Yes, but atm if I put that "composite disable" thing to xorg.conf and have linux-restricted-modules installed my X won't start. The log I pasted is from that case.

---

### Post by IgnorantGuru on 2007-02-14
If X won't start there must be another error in Xorg.0.log - can you post it as a txt attachment (add txt to the end of the filename)?

Or type startx and see what it says.

---

### Post by Dragonstar on 2007-02-15
Here's the whole log: [http://draspu.user.fi/Xorg.0.log.old]("http://draspu.user.fi/Xorg.0.log.old")

Where did you mean I should try that startx? I tried it in recovery mode and there's some text on screen before X gives black screen, but I have no time to read it. Although I can remember that there's some text there when X starts ok. When X don't start, it freezes the whole system. I can't do anything, no ctrl+alt+f1 or ctrl+alt+backspace or anything. I can only reset my whole computer.

---

### Post by IgnorantGuru on 2007-02-15
Only two anomalies I see in that log...

(==) AIGLX enabled
(II) Loading extension GLX

I would add this to the end of xorg.conf
```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

Then try it.

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

This is odd... almost like you have two video devices in xorg.conf   (Edit: On second thought, I don't think so - this may be normal.  But no harm rebuilding xorg.conf below).  It is finding PCI:1:0:0, which is probably correct.

As a sanity check, you might want to backup xorg.conf, then run
```
sudo dpkg-reconfigure xserver-xorg
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

Then add this to xorg.conf:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

That will rebuild xorg.conf from scratch.  Do a reboot and see what the result is.  If you post a Xorg.0.log again, please include the xorg.conf too.

It sounds like X is starting - that's why you're getting the blank screen.  But it sounds like it's freezing up.

One alternative is to remove the ATI driver and linux-restricted-modules, and use the manual driver installation method - Method 2 here... [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Just use the latest ATI driver from their website corresponding to your card...
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

I had good results with that - the newer driver cleared up freezes on my laptop.  But that was using the -10 kernel, so your mileage may vary.

---

### Post by Dragonstar on 2007-02-15
Tried all that. Nothing worked. :( Tried also that method 2. It's quite same as using envy I guess? Also tried installing drivers with that. Here's xorg.0.log when installed with method 2: [Xorg.0.log_method2]("http://draspu.user.fi/Xorg.0.log.old_method2"), in case that helps.  And yes sorry, forgot to paste that xorg.conf. Here it is: [xorg.conf]("http://draspu.user.fi/xorg.conf")

---

### Post by IgnorantGuru on 2007-02-15
conf looks good, and log looks unremarkable except:

(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xe8000000/27, 0xfbe00000/16, I/O @ 0xe000/8, BIOS @ 0xfbd00000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xf0000000/27, 0xfbf00000/16

I don't recall seeing a double entry like that on my systems.  It seems X thinks you have two video cards in your machine.  If you do, I would remove one, get things working, then try to add the second.  If you don't, I can't explain why that's appearing.  It may or may not have something to do with your problem.  Regardless, it appears X is happy with the device it does configure (1:0:0).

Other than that I'm out of ideas.  It's usually at this point that I backup /home and reinstall from scratch.  Install everything EXCEPT the video drivers.  Then backup the partition, then test various driver installations, rolling back the partition as necessary between each attempt.  Details here...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

There's probably a more elegant solution but it's beyond me.  Sometimes in situations like this the series of attempts to fix the problem will get things deeper in trouble - hence the partition backup suggestion.  Sorry I couldn't be of more help but let me know how it goes - I'd be interested to know what finally fixes it.

You could also try posting it to a new thread and see if you can catch the eye of someone smarter than me.  ;)  If so, refer to this thread so they can see the history.

---

### Post by Dragonstar on 2007-02-15
I only have one video card, but if I recall right windows also thinks that I have two of them. Pretty strange indeed.

This is actually second time I have this "composite disable" problem. Just first didn't know it's again about that. Guess I'll open a new thread for this one. I'm just afraid that I'll have to do that reinstall thingie again, that just sucks. Thx for your help anyway :)

---

### Post by IgnorantGuru on 2007-02-15
Sounds good.  FWIW, I'm not convinced composite disable has anything to do with your problem...

Without composite disable, ATI driver fails as expected, and rendering is handled by mesa.

With composite disable, ATI driver is set to do rendering...  but then freezes.

That fact that it appears to work without composite disable is probably because it's only half working.

---

### Post by Dragonstar on 2007-02-18
My problem was finally fixed. The solution was to add the following to the module section of xorg.conf:

```
    SubSection  "extmod"
        Option  "omit xfree86-dga"
    EndSubSection
```

I'm glad that I didn't have to reinstall :)

---

### Post by koanhead on 2007-02-19
I had a very similar problem immediately after dist-upgrading to Edgy.

     I have a pcchips m848lu mobo w/256mb and agp8x. I was using my PCI Geforce2 card from my previous computer (note: that's vanilla pci, not pci-express) and I noticed right away after installing Breezy that any use of glx would hang the system. I switched from "nvidia" to "nv" in xorg.conf and the machine ran that way just fine until I "upgraded" to Edgy. After that using X at all would hang the machine after a few minutes, regardless of the driver used (even "vesa"!)

     My suspicion was and is that the PCI-based card does not coexist well with the agp bus, even when the agp bus is nominally not in use. My computer does not have onboard video. I reported the situation as a bug both to launchpad and to nvnews.net ([http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)). 

     Problems of this sort are very common with the nvidia drivers it seems, and I'm sure the same is true with ATI. IMHO this sort of thing is inevitable at the interface of proprietary closed-source drivers and FOSS software.

      Anyway, I was advised to "blacklist" the agpgart kernel module in /etc/modules.d. I tried that, and several other methods to prevent agpgart from loading, but without success. If you have an option in the BIOS to disable the agp bus, that might help you. As for me, I finally broke down and just bought an agp card for my machine (an old GeForce 256). Now it works, but without any 3d acceleration :(

---

