---
title: "Can't login graphically after 11.10 upgrade"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2011-10-23
Hi,

I have a Dell Inspiron 17R, with an ATI Radeon HD 5470 card. In 11.04, I was using the proprietary drivers, which admittedly weren't very good, but it was the only way to get 3-D acceleration.

I upgraded to 11.10 earlier today, and I got a blank screen while booting. After some fiddling around, I have removed the proprietary ATI drivers, and now I get as far as the login screen. However, when I try to login, it kicks me out immediately, even if I select failsafe mode.

The Xorg logs don't seem to show any errors. What surprises me is that the /etc/X11 folder shows no xorg.conf file.

Where should I look?

---

### Post by raja.genupula on 2011-10-23
> **skamarla said:**
> Hi,

I have a Dell Inspiron 17R, with an ATI Radeon HD 5470 card. In 11.04, I was using the proprietary drivers, which admittedly weren't very good, but it was the only way to get 3-D acceleration.

I upgraded to 11.10 earlier today, and I got a blank screen while booting. After some fiddling around, I have removed the proprietary ATI drivers, and now I get as far as the login screen. However, when I try to login, it kicks me out immediately, even if I select failsafe mode.

The Xorg logs don't seem to show any errors. What surprises me is that the /etc/X11 folder shows no xorg.conf file.

Where should I look?


Hi man 
Fron your Grub menu boot to recovery and then select root shell and do this one by one.

```
X -configure
```

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

and reboot and let me know what you got.
All the best.

---

### Post by skamarla on 2011-10-23
Thanks for your help.

X -configure gives an error

```
(EE) Unable to initialize PCS database
(EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
(EE) open /dev/fb0: No such file or directory
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
```

But the xorg.conf.new file is generated and I have copied it to /etc/X11.

When trying to login, I get kicked out again. The Xorg.0.log file only shows an error about "Acceleration initialization failed", but it's not a critical error.

A few days ago, I had a similar problem, after upgrading the proprietary drivers, and I fixed it by editing the /.kde/share/config/kwinrc by hand, and disabling compositing. I don't know what else to disable, though.

---

### Post by raja.genupula on 2011-10-23
> **skamarla said:**
> Thanks for your help.

X -configure gives an error

```
(EE) Unable to initialize PCS database
(EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
(EE) open /dev/fb0: No such file or directory
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
```

But the xorg.conf.new file is generated and I have copied it to /etc/X11.

When trying to login, I get kicked out again. The Xorg.0.log file only shows an error about "Acceleration initialization failed", but it's not a critical error.

A few days ago, I had a similar problem, after upgrading the proprietary drivers, and I fixed it by editing the /.kde/share/config/kwinrc by hand, and disabling compositing. I don't know what else to disable, though.

Hi look at this

[http://ubuntuforums.org/showthread.php?t=1268406](http://ubuntuforums.org/showthread.php?t=1268406)

---

### Post by skamarla on 2011-10-23
I have blacklisted the intel card, and the startup looks better (it used to give a few errors about i915 before), but I eventually get the login screen, and it still won't let me in.

aticonfig isn't an option now, because I have uninstalled the proprietary drivers. Maybe I should do that now, installing fglrx from the Ubuntu repositories?

---

### Post by MAFoElffen on 2011-10-23
> **skamarla said:**
> I have blacklisted the intel card, and the startup looks better (it used to give a few errors about i915 before), but I eventually get the login screen, and it still won't let me in.

aticonfig isn't an option now, because I have uninstalled the proprietary drivers. Maybe I should do that now, installing fglrx from the Ubuntu repositories?
What part of the loging does it error at? (screen)

It sounds like (after you disabled you driver and before you did the last few things) that you booted the kernel... That meant that it got where it went from a text screen to the infamous black/purple screen. It started Plymouth... got to the Ubuntu Logo with the white and red dots. It got to the login screen.

That tells me you successfully started Xorg and am stuck in lightdm.

*** The get back to where you were before the last suggestion, rename your /etx/X11/xorg.conf to any else.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

```You said that previous to that you had uninstalled your ATI driver and had gooten to where I described... Note- You may have to use a "radeon.modeset=0" boot option to boot the graphics.

On the lightdm, try 
```

sudo dpkg-reconfigure lightdm

```That will reconfigure lightdm and reset all it connections to other packages.

Note that some combinations of hardware have issues with lightdm.  If yours happens to be one of those few, then pick GDM as a desktop manager, if previously installed If Updgraded form 11.04, it might still be there.  If it is still there, doing the command above, you would have seen it as a choice... If not then,
```

sudo apt-get install gdm

```> aticonfig isn't an option now, because I have uninstalled the  proprietary drivers. Maybe I should do that now, installing fglrx from  the Ubuntu repositories?
Lets get you with a working system with basic graphics, then we'll work on the graphics.


Tell me how it goes.

---

### Post by skamarla on 2011-10-23
> **MAFoElffen said:**
> What part of the loging does it error at? (screen)


Well, that's part of the problem. Xorg.0.log doesn't show any errors at all.

> **MAFoElffen said:**
> That tells me you successfully started Xorg and am stuck in lightdm.


Yes, Xorg is up, but it's kubuntu, so I'm stuck in KDE.

In the meantime, I installed fglrx and tried to make it work. No luck. I got an error about a version mismatch, which suggested that some previous driver hadn't been completely removed.

> **MAFoElffen said:**
> 
Lets get you with a working system with basic graphics, then we'll work on the graphics.


I agree. Where can I look for the KDE errors?

---

### Post by MAFoElffen on 2011-10-23
> **skamarla said:**
> Well, that's part of the problem. Xorg.0.log doesn't show any errors at all.

Yes, Xorg is up, but it's kubuntu, so I'm stuck in KDE.

In the meantime, I installed fglrx and tried to make it work. No luck. I got an error about a version mismatch, which suggested that some previous driver hadn't been completely removed.

I agree. Where can I look for the KDE errors?
Yes, it's getting past xorg itself and is above that layer...

Lets see, recent upgrade problems in those layers have beem on the desktop manager and permissions.  When it get to the KDE login screen, togglw ovwr to a TTY termeinal session (cntrl-alt-F2) and try
```
sudo chown $USER:$USER /home/$USER -R

sudo apt-get update && sudo apt-get install --reinstall dpkg

sudo apt-get install --reinstall kdm

if [ ! -f /etc/X11/default-display-manager ]; then sudo touch /etc/X11/default-display-manager
echo -e "/usr/sbin/kdm" | sudo tee /etc/X11/default-display-manager

sudo service kdm stop

sudo apt-get upgrade

sudo service kdm start
```I don't have KDE installed here at the moment, but that "should" be it... (hoping for you.)

---

### Post by MAFoElffen on 2011-10-23
Forgot to answer something, next to look in if still a peoblem would be dmsg and syslog logs.

---

### Post by skamarla on 2011-10-23
No luck, same problem. I followed your instructions except the default-display-manager stuff, because I noticed that my file points to /usr/bin/kdm (which exists) instead of /usr/sbin/kdm.

So I looked at dmesg, nothing, and syslog only shows the following every time I try to logon:

```
Oct 23 22:23:14 portatil-dell acpid: client 3229[0:0] has disconnected
Oct 23 22:23:14 portatil-dell acpid: client connected from 3229[0:0]
Oct 23 22:23:14 portatil-dell acpid: 1 client rule loaded
Oct 23 22:23:17 portatil-dell acpid: client 3229[0:0] has disconnected
Oct 23 22:23:17 portatil-dell acpid: client connected from 3229[0:0]
Oct 23 22:23:17 portatil-dell acpid: 1 client rule loaded
Oct 23 22:23:18 portatil-dell kdm_greet[3452]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: El fitxer o directori no existeix
```

Which means that the file doesn't exist. I'll try to follow this lead...

---

### Post by MAFoElffen on 2011-10-23
> **skamarla said:**
> No luck, same problem. I followed your instructions except the default-display-manager stuff, because I noticed that my file points to /usr/bin/kdm (which exists) instead of /usr/sbin/kdm.

So I looked at dmesg, nothing, and syslog only shows the following every time I try to logon:

```
Oct 23 22:23:14 portatil-dell acpid: client 3229[0:0] has disconnected
Oct 23 22:23:14 portatil-dell acpid: client connected from 3229[0:0]
Oct 23 22:23:14 portatil-dell acpid: 1 client rule loaded
Oct 23 22:23:17 portatil-dell acpid: client 3229[0:0] has disconnected
Oct 23 22:23:17 portatil-dell acpid: client connected from 3229[0:0]
Oct 23 22:23:17 portatil-dell acpid: 1 client rule loaded
Oct 23 22:23:18 portatil-dell kdm_greet[3452]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: El fitxer o directori no existeix
```

Which means that the file doesn't exist. I'll try to follow this lead...
Is that the Kubuntu equivalent to the untity greeter?

---

### Post by skamarla on 2011-10-23
> **MAFoElffen said:**
> Is that the Kubuntu equivalent to the untity greeter?

I guess it is, but I've checked, and this is not the problem. I've checked syslogs from before the upgrade, and this error was already there. Nothing new, then.

I have found a more promising error in syslog, though. Here it is:


```
Oct 24 01:04:16 portatil-dell dbus[1134]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Oct 24 01:04:19 portatil-dell dbus[1134]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Oct 24 01:04:19 portatil-dell dbus[1134]: [system] Successfully activated service 'org.freedesktop.UDisks'
Oct 24 01:04:21 portatil-dell kernel: [   77.293220] show_signal_msg: 3 callbacks suppressed
Oct 24 01:04:21 portatil-dell kernel: [   77.293224] kded4[1998]: segfault at 50 ip 00007f0dfa7d4b2b sp 00007fff8e48def0 error 4 in ld-2.13.so[7f0dfa7c9000+21000]
Oct 24 01:04:21 portatil-dell kernel: [   77.342880] kcminit_startup[2000]: segfault at 50 ip 00007f0dfa7d4b2b sp 00007fff8e48e000 error 4 in ld-2.13.so[7f0dfa7c9000+21000]
Oct 24 01:04:22 portatil-dell acpid: client 1256[0:0] has disconnected
Oct 24 01:04:22 portatil-dell acpid: client connected from 1256[0:0]
Oct 24 01:04:22 portatil-dell acpid: 1 client rule loaded
Oct 24 01:04:22 portatil-dell kernel: [   77.900261] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Oct 24 01:04:22 portatil-dell kdm_greet[2029]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: El fitxer o directori no existeix
```

Which seems to point again to some kind of problem in the graphic card.

For what it's worth, the output of

```
 modprobe -l | grep drm
```

is:

```
kernel/drivers/gpu/drm/i2c/ch7006.ko
kernel/drivers/gpu/drm/i2c/sil164.ko
kernel/drivers/gpu/drm/drm_kms_helper.ko
kernel/drivers/gpu/drm/drm.ko
kernel/drivers/gpu/drm/ttm/ttm.ko
kernel/drivers/gpu/drm/tdfx/tdfx.ko
kernel/drivers/gpu/drm/r128/r128.ko
kernel/drivers/gpu/drm/radeon/radeon.ko
kernel/drivers/gpu/drm/mga/mga.ko
kernel/drivers/gpu/drm/i810/i810.ko
kernel/drivers/gpu/drm/i915/i915.ko
kernel/drivers/gpu/drm/sis/sis.ko
kernel/drivers/gpu/drm/savage/savage.ko
kernel/drivers/gpu/drm/vmwgfx/vmwgfx.ko
kernel/drivers/gpu/drm/via/via.ko
kernel/drivers/gpu/drm/nouveau/nouveau.ko
```

Before the upgrade, I installed the proprietary drivers directly from the AMD site. Maybe something is still around?

---

### Post by MAFoElffen on 2011-10-24
> **skamarla said:**
> I guess it is, but I've checked, and this is not the problem. I've checked syslogs from before the upgrade, and this error was already there. Nothing new, then.

I have found a more promising error in syslog, though. Here it is:

Before the upgrade, I installed the proprietary drivers directly from the AMD site. Maybe something is still around?
I believe either that or Xorgs Radeon driver, via a Basic xorg.conf:
```
[FONT=monospace]
[/FONT]# Basic /etc/X11/xorg.conf template 

Section "Device"         
    Identifier    "Configured Video Device"         
    Driver        "radeon" 
EndSection 

     Section      "Monitor"         
    Identifier   "Configured Monitor" 
EndSection  

Section "Screen"         
    Identifier    "Default Screen"         
    Monitor      "Configured Monitor" 
           Device      "Configured Video Device" 
EndSection

```Or... The ATI Catalyst Driver supports your car. Current is v11.9, "BUT DON"T USE" that one.  Install v11.8 instead.  v11.9 has problems with Ubuntu versions 11.04 and 11.10 (compiz and unity).

/*  Further  */
I re-read all your posts in the thread and something is tugging at me.  The errors you were and are getting are associated will Nouveau modules (like your DRI errors in your xorg log and the pcid errors)...  But you have a Radeon Card, not a NVidia card.  Nouveau is an opensource NVidia driver!?!

I think something is a bit "confused."  I figure if we pointed xorg to directly to an appropriate driver, that may help (Proprietary or opensource.)  Then If we also turn off Nouveau support from "trying," that will take that out of the equation:
```

echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

```
And possibly check the file /etc/modprobe.d/blacklist.conf and ensure it contains at least the 2 lines:
```

blacklist nouveau 
blacklist lbm-nouveau

```
Hopefully that will get rid of the error messages that you have been getting, like you said, even before, when it was working.

---

### Post by skamarla on 2011-10-24
Nothing worked. I tried blacklisting nouveau first; then I tried the "radeon" driver, and finally I have installed the Catalyst driver from the AMD site. I still get the same segfault and kernel errors.

You gave me an excellent piece of information, though. The 11.9 version of the driver screws up the system really bad. Mine is one good example. I wish I had known before! I installed it before the 11.10 migration, and the problems I got were what decided me to move to 11.10, in the hope that the upgrade would clean up the installation, and I could stop downloading stuff from the ATI site every time there was a kernel upgrade.

I think that the only option I have left is to do a clean reinstall. I'll take the advice from the sticky message in this forum and do it that way.

Thanks a lot for your help!

---

### Post by MAFoElffen on 2011-10-24
> **skamarla said:**
> Nothing worked. I tried blacklisting nouveau first; then I tried the "radeon" driver, and finally I have installed the Catalyst driver from the AMD site. I still get the same segfault and kernel errors.

You gave me an excellent piece of information, though. The 11.9 version of the driver screws up the system really bad. Mine is one good example. I wish I had known before! I installed it before the 11.10 migration, and the problems I got were what decided me to move to 11.10, in the hope that the upgrade would clean up the installation, and I could stop downloading stuff from the ATI site every time there was a kernel upgrade.

I think that the only option I have left is to do a clean reinstall. [COLOR=Green]I'll take the advice from the sticky message in this forum and do it that way.[/COLOR]

Thanks a lot for your help!
You mean my sticky?
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Yes... I'm thinking that may be easier to reinstall that trying to track down "what" is missing or corrupted through all that... If you do, Go to my sticky and look at the bottom of Post #1 and the bottom of Post #334.  One more note I haven't updated there yet- Before you can install the fglrx through apt-get with 11.10, you first have to uncomment the "Conical Partners" lines in the sources list.  (I'll make a post/tutorial about that tonight when I get time and link it from Post 2...)  I've been letting people know on the forum for 3 weeks, but been to busy out here to add it my sticky yet...

Fires take priority... But refering things from or back to my sticky saves me a lot of time.

---

### Post by skamarla on 2011-10-28
Done!!

It took a while, though. While reinstalling, the laptop overheated and shut itself down. The bootloader got corrupted and I got stuck. I tried an USB install instead of the CD-ROM, but it still overheated. Finally, I managed to do it with the USB **and** a hanheld fan blowing on the side of the laptop.

I still have to check, but I think that, since I chose to add nonfree software at the moment of installation, I already got the fglrx drivers, and it's "just working". In the end, it was a breeze in several ways. :P

---

