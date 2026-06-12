---
title: "Nvidia drivers stopped working in Karmic"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MKdx on 2009-08-19
Hello

I recently got some new hardware and figured that I'd like to go with Karmic - I was with Hardy before that. I've been using Karmic since alpha3 release and it's working fine for the most part.

The main issue I have is that nvidia propriety drivers doesn't seems to work now. My nvidia card is the same one I used with Hardy.

I can see the card, and Jockey is able to detect it. It also works with nouveau.
```
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at fd000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [44] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel modules: nvidia,nvidiafb
```

I installed the driver through Jockey at first, however it doesn't get activated. When you reboot it will fail to startx and you are in tty1 now. Changing xorg.cfg and rebooting should get you back to gdm. However we're back to the starting point.

I've tried the latest nvidia driver 190, older ones 96, 71, others 173, 180, but the same thing happens.

Any idea what might be the problem?

---

### Post by MKdx on 2009-08-19
In Jokcey-log:
```
2009-08-19 13:38:37,554 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d073ec>
2009-08-19 13:38:37,569 DEBUG: reading modalias file /lib/modules/2.6.31-6-generic/modules.alias
2009-08-19 13:38:38,341 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2009-08-19 13:38:38,349 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2009-08-19 13:38:38,532 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2009-08-19 13:38:38,543 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173 (and other ones)
....
2009-08-19 13:38:38,617 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
....
2009-08-19 13:38:39,251 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2009-08-19 13:38:39,313 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-08-19 13:38:39,334 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2009-08-19 13:38:39,335 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
....
2009-08-19 13:38:39,600 DEBUG: all custom handlers loaded
2009-08-19 13:38:39,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d073ec> about HardwareID('modalias', 'pci:v000010DEd00000322sv00000000sd00000000bc03sc00i00')
2009-08-19 13:38:40,841 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-08-19 13:38:40,936 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-08-19 13:38:40,941 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-08-19 13:38:40,942 DEBUG: NVIDIA legacy driver not currently supported
2009-08-19 13:38:40,943 DEBUG: ignoring unavailable handler xorg:nvidia-71([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-08-19 13:38:40,947 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2009-08-19 13:38:40,997 DEBUG: got handler xorg:nvidia-96([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-08-19 13:38:41,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
...
* After that it will be series of:
2009-08-19 13:38:41,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d073ec> about HardwareID('modalias', .....)
2009-08-19 13:38:42,606 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': ....., 'jockey_handler': 'KernelModuleHandler'}
* before it ends with:
2009-08-19 13:38:52,546 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia
2009-08-19 13:38:52,731 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})
```

Further digging gives:
```
nvidia (173.14.16): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.

nvidia (96.43.10): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.

nvidia (71.86.08): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.
```

I'm not sure where to go from here though.

---

### Post by jfernyhough on 2009-08-19
First off remove all of the nvidia drivers. You only need one set installed, if you have more than one they will conflict and it all gets very gunky.

Next we need to check which series supports your 5200. According to [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606) you need the 173 series. Now, depending on when these were updated last they may or may not work with the latest kernel version. Version 173.14.18 was released in March so won't have support for 2.6.31. Hence they won't work with the default Karmic kernel! (unless there's a patch on the forum, I haven't looked). You might have success if you install kernel 2.6.30 and use that instead (it's in the repos).

Otherwise you might consider upgrading to a more recent card. ;)

In summary:
1) Remove all nvidia drivers. Restart just to be safe (check your xorg.conf, ' $ sudo dpkg-reconfigure -phigh xserver-xorg ' makes a nice baseline).
2) Install nvidia-173 and kernel 2.6.30. You may need to add driver "nvidia" to your ConfiguredVideoDevices section of xorg.conf.
3) Reboot and select the new old kernel.

---

### Post by dinxter on 2009-08-19
unfortunately all that jockey shows is that the nvidia driver has not been built or installed. i'd make a guess that the dkms build of the nvidia source is failing somewhere, the failure log should be in 
/var/lib/dkms/nvidia/185.18.14/2.6.31-6-generic/x86_64/log/make.log

though obviously this will vary on your nvidia version and current kernel
if not, try running
1. dkms status
then using the information from that run
2. dkms build -m nvidia -v <version goes here> -k <current kernel>
for example, on my computer i would get,
$dkms status
nvidia, 185.18.14, 2.6.31-6-generic, x86_64
so i would run
$ dkms build -m nvidia -v 185.18.14 -k 2.6.31-6-generic

if htis fails it will let you know and generate a make.log file, this should tell you where the problem is

---

### Post by dinxter on 2009-08-19
not sure which package is the one needed by your card but
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/391768](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/391768)

there may be problems with 173 too, i dont know. there seems to be a patch for 96 in that bug report though

---

### Post by dinxter on 2009-08-19
seems to be the proc->owner deprecation bug that nvidia 180 suffered from, if you have problems with patching from the bug report  i'll have a look at a ppa fix, probably tomorrow

---

### Post by dinxter on 2009-08-19
yep, thats the one with 173 too
/var/lib/dkms/nvidia/173.14.16/build/nv.c:721: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;

its a deprecated function thing with 2.6.31 kernels, shouldn't be too tricky too patch, the 180 has been done for exactly the same reason

---

### Post by dinxter on 2009-08-20
i've attached patches for 96 and 173 to the bugs below
[Bug #398893]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/398893")
[Bug #391768]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/391768")
i'll also add fixed packages to the ppa
[https://launchpad.net/~dinxter/+archive/ppa](https://launchpad.net/~dinxter/+archive/ppa)

[nvidia-graphics-drivers-96 -  6.43.10-0ubuntu3~dinxter2       ]("https://launchpad.net/%7Edinxter/+archive/ppa/+sourcepub/703770/+listing-archive-extra")
[        nvidia-graphics-drivers-173 - 173.14.16-0ubuntu3~dinxter2       ]("https://launchpad.net/%7Edinxter/+archive/ppa/+sourcepub/703771/+listing-archive-extra")

---

### Post by hshan on 2009-08-20
Thank you Dinxter ! Works!

---

### Post by jfernyhough on 2009-08-20
I'll admit it, your solution is more elegant than mine. :D

Also means I can now install Karmic on my old Athlon 3200+ with Geforce 4200 and have full acceleration. Nice.

(As an aside, did anyone else upgrade from a 5200 to a 4200? NVidia really annoyed me with that - bought a new 5200 to play HL (replacing a Voodoo 3) and found it sucked; then I bought a 4200 for the same price and it was immense in comparison. Weird.)

---

### Post by MKdx on 2009-08-20
> **jfernyhough said:**
> According to [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606) you need the 173 series.
Ah 180 is for newer cards then. Jockey did recommend the correct version though [173].

> You might have success if you install kernel 2.6.30 and use that instead (it's in the repos).
Hmmm I tried the 2.6.30 kernel, but this doesn't seem to work either.
I wonder why though, because it says in the bug report that this should only affect kernels >.30

> Otherwise you might consider upgrading to a more recent card. ;)
I'm keeping it for luck!

---

### Post by MKdx on 2009-08-20
> **dinxter said:**
> i'd make a guess that the dkms build of the nvidia source is failing somewhere, the failure log should be in 
/var/lib/dkms/nvidia/185.18.14/2.6.31-6-generic/x86_64/log/make.log
I thought it had something to do with the dkms autoinstall, which's indeed is the case as indicated in the make.log you pointed to.

> **dinxter said:**
> yep, thats the one with 173 too
/var/lib/dkms/nvidia/173.14.16/build/nv.c:721: error: ‘struct proc_dir_entry’ has no member named ‘owner’
its a deprecated function thing with 2.6.31 kernels
Yes, this is the error in make.log. The error occurs with 2.6.30 as well though.

> **dinxter said:**
> i've attached patches for 96 and 173 to the bugs below

That did it. It builds successfully now, and the driver get activated in Jockey.
```
$dkms status
nvidia, 173.14.16, 2.6.31-6-generic, i686: installed
```

---

### Post by MKdx on 2009-08-20
It does build successfully, and there's no dkms errors now. However, for some reason, I still get to tty whenever the glx driver is set. There doesn't seem to be any error message.

I'm trying to trace the boot sequence to see if there's anything useful, but the boot logging seems to be disabled for some reason. bootlogd can't be installed because it comes with sysvinit which conflicts with upstart, and dmesg doesn't all messages.

:confused:

---

### Post by dinxter on 2009-08-21
> **MKdx said:**
> 
I'm trying to trace the boot sequence to see if there's anything useful, but the boot logging seems to be disabled for some reason. bootlogd can't be installed because it comes with sysvinit which conflicts with upstart, and dmesg doesn't all messages.

:confused:
the x log file should be 
/var/log/gdm/\:0.log
if X is failing then the reasons should be in there
the logging daemon is now rsyslog which has replaced sysklogd, upstart replaced sysvinit quite a while ago and provides sysvinit back compatibility.

[EDIT} dmesg|less  should allow you to see all kernel messages but an X failure is unlikely to show up there, it is in the log file above. you should also be able to see messages when you attempy to start X manually either by
/etc/init.d/gdm start   
if you use gdm or,
startx

---

### Post by plun on 2009-08-21
I am rather sure that the latest GPU 5XXX driver is needed, ie 173.14.20

[http://www.nvnews.net/vbulletin/showthread.php?p=2037374](http://www.nvnews.net/vbulletin/showthread.php?p=2037374)

> Restored compatibility with recent Linux kernels.

---

### Post by gibocchia9 on 2009-08-22
it works perfectly, thx!

---

### Post by caryb on 2009-08-22
I wish I could say the same but thank goodness for the nv driver to the rescue.


Cary

---

### Post by drs305 on 2009-08-22
I just installed a week's worth of updates, which I saw included nvidia updates. Rebooting resulted in terminal only.

I reinstalled the nvidia drivers but still was unable to boot to the Desktop.

For me, the solution was to edit /etc/X11/xorg.conf and change:
> Driver	"nvidia"
to
> Driver "nv"

After the xorg.conf edit the system rebooted normally. I then checked and discovered no nvidia drivers were activated. I reactivated the drivers (185) and successfully rebooted.

After rebooting, I checked and the xorg.conf file had returned to > Driver "nvidia" which is now working correctly.

Added: In retrospect, changing "nvidia" to "nv" may have had more to do with just getting rid of "nvidia" than with substituting "nv". My guess is that just by removing "nvidia" the system booted to the onboard video without trying to use the nvidia drivers and that specifically using "nv" had little to do with solving it.

---

### Post by wavded on 2009-08-23
Changing "nvidia" to "nv" in xorg.conf worked but after I went into Gnome, Jockey ended up recommending 185, but when I rebooted, I just got a blank screen when it hit GDM.  I tried 173... and i got a command line login :-(.  Any ideas on what I'm doing wrong?

---

### Post by caryb on 2009-08-23
On my pc the nvidia is greyed out in hardware drivers app & selecting activate does nothing. I tried to reinstall the 180 driver but it fails.


Cary

---

### Post by BackwardsDown on 2009-08-23
> **wavded said:**
> Changing "nvidia" to "nv" in xorg.conf worked but after I went into Gnome, Jockey ended up recommending 185, but when I rebooted, I just got a blank screen when it hit GDM.  I tried 173... and i got a command line login :-(.  Any ideas on what I'm doing wrong?

Same.

---

### Post by ronacc on 2009-08-23
nvidia update came down for me yesterday . 185.18.31  , working ok with my 7600gs and the rc7 kernel.

---

### Post by drs305 on 2009-08-23
> **ronacc said:**
> nvidia update came down for me yesterday . 185.18.31  , working ok with my 7600gs and the rc7 kernel.

That's the same setup I have. Hopefully others will obtain similar results.

Getting rid of the nvidia driver reference in xorg.conf seems to let others boot to onboard video so hopefully they will now be able to install a working driver again.

---

### Post by caryb on 2009-08-23
For me this can be marked resolved:)


Cary

---

### Post by BackwardsDown on 2009-08-24
> **caryb said:**
> For me this can be marked resolved:)


Cary

Great! Cause I have the same card as you :)

edit: Cool! It works!

---

### Post by kernco on 2009-08-24
I'm having this problem and the solutions here don't fix it for me.  I'm using Kubuntu and had been just doing "apt-get upgrade" for about a week, ignoring the fact that there were about 60 packages being held back.  I finally did a dist-upgrade last night to take care of those.  I noticed it installed a new kernel and upgraded my nvidia driver from 180 to 185.  When I booted my computer this morning, all I got was a command line.  Changing to the nv driver allows me to get into the gui, but my dual-screen setup doesn't work and the nv driver doesn't support 3D acceleration.  When I go into the hardware drivers manager, I can choose nvidia 173 or 185, both of which are shown as not active.  When I try to activate either one, a progress bar takes about a minute to complete, but afterwards it still shows both drivers as inactive.

---

### Post by taavikko on 2009-08-24
> **kernco said:**
> I'm having this problem and the solutions here don't fix it for me.  I'm using Kubuntu and had been just doing "apt-get upgrade" for about a week, ignoring the fact that there were about 60 packages being held back.  I finally did a dist-upgrade last night to take care of those.  I noticed it installed a new kernel and upgraded my nvidia driver from 180 to 185.  When I booted my computer this morning, all I got was a command line.  Changing to the nv driver allows me to get into the gui, but my dual-screen setup doesn't work and the nv driver doesn't support 3D acceleration.  When I go into the hardware drivers manager, I can choose nvidia 173 or 185, both of which are shown as not active.  When I try to activate either one, a progress bar takes about a minute to complete, but afterwards it still shows both drivers as inactive.

what does the "dkms status" prints?
or "dpkg -l nvidia\* |grep ^ii"

Use "sudo aptitude safe-upgrade" when it's about to remove something, to give you a change to see what's going on.

---

### Post by kernco on 2009-08-24
> **taavikko said:**
> what does the "dkms status" prints?
or "dpkg -l nvidia\* |grep ^ii"
```
$ dkms status
nvidia, 185.18.36: added
```
That changes to the 173 version if I try to activate it in the hardware driver manager

```
$ dpkg -l nvidia\* |grep ^ii
ii  nvidia-173-modaliases                 173.14.16-0ubuntu1                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-180-modaliases                 185.18.36-0ubuntu1                         Transitional package for nvidia-185-modalias
ii  nvidia-185-kernel-source              185.18.36-0ubuntu1                         NVIDIA binary kernel module source
ii  nvidia-185-libvdpau                   185.18.36-0ubuntu1                         Video Decode and Presentation API for Unix
ii  nvidia-185-modaliases                 185.18.36-0ubuntu1                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                  71.86.08-0ubuntu1                          Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                  96.43.10-0ubuntu1                          Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                         0.2.15                                     Find obsolete NVIDIA drivers
ii  nvidia-glx-185                        185.18.36-0ubuntu1                         NVIDIA binary Xorg driver
ii  nvidia-settings                       180.25-0ubuntu1                            Tool of configuring the NVIDIA graphics driv

```

> **taavikko said:**
> Use "sudo aptitude safe-upgrade" when it's about to remove something, to give you a change to see what's going on.
I did do that and saw that it was going to upgrade my kernel and take me from nvidia 180 to 185.  Is there a reason I should have expected this not to work?

---

### Post by BackwardsDown on 2009-08-24
> I did do that and saw that it was going to upgrade my kernel and take me from nvidia 180 to 185. Is there a reason I should have expected this not to work?

As no important packages were removed, nope, you could not see it coming.

---

### Post by taavikko on 2009-08-24
@kernco,

My output of
```
devil@core7:~$ dkms status 
nvidia, 185.18.36, 2.6.31-6-generic, x86_64: installed 
```

So it hasn't been builded properly in your setup.
There's at least two ways to solve this.

manually building/installing
```
sudo dkms build -m nvidia -v 185.18.36 -k $(uname -r)
```
and the same, replacing build with "install"

Or by reinstalling kernel/nvidia-185-kernel-source
```
sudo aptitude reinstall linux-image-`uname -r`
sudo aptitude reinstall nvidia-185-kernel-source 
```

---

### Post by kernco on 2009-08-24
Ok, I think the problem is that 'uname -r' gives '2.6.31-4-generic' but the current version is 2.6.31-6.  When I try to reinstall linux-image-`uname -r`, I get these errors:
```
E: I wasn't able to locate file for the linux-image-2.6.31-4-generic package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the linux-image-2.6.31-4-generic package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```
So I tried doing ```
sudo aptitude reinstall linux-image-2.6.31-6-generic
```
This worked and redid the dkms nvidia build.  Now dkms status gives me ```
nvidia, 185.18.36, 2.6.31-6-generic, i686: installed
```
but uname -r still says 2.6.31-4-generic, and when I switched back to the nvidia driver and rebooted, kdm still fails to start.

---

### Post by taavikko on 2009-08-24
@kernco. no biggie, you were/are running with older kernel, just reboot completely to start the session with the latest kernel.

It should still be mandatory to insert {Driver "nvidia"} to xorg.conf for to use it.

---

### Post by kernco on 2009-08-24
I had already tried rebooting, but it's still using the old kernel.  I figured out that it isn't updating the Grub configuration, so I tried to do that myself but apparently /boot/grub/grub.cfg is readonly even if I open it with "sudo vim"...

edit: nvm, I can force it to save anyway

---

### Post by kernco on 2009-08-24
Yeah adding the kernel to the Grub boot list fixed my problem.  Thanks for your help.  Now I have to figure out if there's some problem with my system and this will happen every kernel upgrade, or if it was just a bug in the packaging of that kernel.

---

### Post by ronacc on 2009-08-24
on my sys when the 2.6.31-6-generic kernel was added to grub , it was not added as the first entry but as the third ( of 10 ) , I had to switch it myself .

---

### Post by MKdx on 2009-08-25
> **dinxter said:**
> the x log file should be 
/var/log/gdm/\:0.log
if X is failing then the reasons should be in there
the logging daemon is now rsyslog which has replaced sysklogd, upstart replaced sysvinit quite a while ago and provides sysvinit back compatibility.

Thanks for informative replys. I was looking for it.

> **plun said:**
> I am rather sure that the latest GPU 5XXX driver is needed, ie 173.14.20

I did try it, but alas same result.

```
nvidia, 173.14.20, 2.6.31-7-generic, i686: installed
```

---

### Post by MKdx on 2009-08-25
The x log wasn't that much specific unfortunately.

```
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.20  Thu Jun 24 11:19:59 PDT 2009 (or 173.14.16)
(II) Loading extension GLX
....
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

However, The first error message in the starting I was about /sbin/lrm-video not found.

I'm not sure if this has something to do with the problem, as I understand that lrm is more or less deprecated now. But at Hardy the lrm was still available, while it's not in Karmic. Another thing, Karmic apparently doesn't create /etc/modprobe.d/lrm-video by default. However, I have it on my system.
```
# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS
```

Opinions?

---

### Post by Neil Woolford on 2009-09-09
I had this problem with the Nvidia driver (version 96) not building under Karmic.
Dinxter's patched versions in his ppa worked well for me.  (Thank you Dinxter).
Yesterday, new versions of the Nvidia driver (96.43.13-0ubuntu2) appeared in the main Karmic repositories, and today I tried them out with my current kernel (2.6.31-10-generic).  They built and work fine.
For me, this problem is now fixed.

---

### Post by dinxter on 2009-09-09
i believe now other packages have settled a little into feature freeze the ever tireless alberto milone has gone through the various nvidia packages updating from upstream and fixing various bugs so hopefully people should see nvidia support working now (fingers crossed :))

---

### Post by MKdx on 2009-09-09
Works here finally!! The problem was with the lrm-video stuff. Deleting /etc/modprobe.d/lrm-video actually solved it :|

I'm not sure where that file come from, as I did fresh install with alpha3.. I then had to add my user to the video group.

---

### Post by kev000 on 2009-09-14
After the update over the weekend, nvidia broke for me.  I don't see a /etc/modprobe.d/lrm-video, so that may not be my issue.  I was using the 185 driver.

uname -r:
2.6.31-10-generic

I also tried the 190 driver from the aforementioned ppa with no success.  Anyone else experiencing this issue?

---

### Post by fog on 2009-09-14
> **kev000 said:**
> After the update over the weekend, nvidia broke for me.  I don't see a /etc/modprobe.d/lrm-video, so that may not be my issue.  I was using the 185 driver.

uname -r:
2.6.31-10-generic

I also tried the 190 driver from the aforementioned ppa with no success.  Anyone else experiencing this issue?
Same problem here. Found [this]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1686355.html") :(

---

### Post by kev000 on 2009-09-14
> **fog said:**
> Same problem here. Found [this]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1686355.html") :(

Yep, that looks like what I'm seeing.  I tried the 190 driver from NVidia's website with no success.  Xorg still crashes.  I'm up and running with "nv" but none of my glx apps run :(.

I realize that everything is really unstable, I was just wondering if anyone has found a workaround yet...  Looks like downgrading eglibc is the current workaround.  There are some packages to try though according to the bug report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/429003](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/429003)

---

### Post by autocrosser on 2009-09-14
I see that there was a "new" update for libc6---has this been cured yet?

Looks like I posted in the wrong thread.....

---

### Post by xebian on 2009-09-14
I update daily, and never had this issue.  I use the NV 185.18.36 drivers though.:confused:

---

### Post by kev000 on 2009-09-15
The libc6-ubuntu12 stuff cured the issue.  This bug should have affected *every* nvidia driver, even legacy (according to the bug report).  At any rate, it's working now so I'm happy again :guitar:

---

### Post by jermyandhisbass on 2009-09-16
I am still having the dreaded black screen after reinstalling nvidia-glx-185.  Unable to Alt+PrintScr+R and Ctrl+Alt+F2.  Chrooting and removing nvidia-glx-185 fixes the issue, but still no 3D support.

---

### Post by briancb on 2009-09-17
My problem with nvidia is the settings are stuck with main screen on separate x screen twin veiw etc greyed out. When loading Nvidia-settings at root I get this:

ERROR: Cannot open display 'Dad:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/brian/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 47
       of configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 48 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 49 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 50
       of configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       51 of configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/brian/.nvidia-settings-rc' (no Display
       connection).


Any ideas? Tried uninstalling all things nvidia reinstalling goes back to the same thing.

---

