---
title: "Nvidia driver activated but not currently in use ??"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2010-01-20
Under System-Admin-Hardware Drivers I see nvidia-current as activated but not currently in use.There are two entries for Nvidia X Server Settings and when clicked neither one of them work. Also x server crashes when trying to open either one of them. Any one else having this problem ?? Any work around would be appreciated. Thanks

---

### Post by jppr on 2010-01-20
Jockey (Ubuntu's restricted driver manager) doesn't yet support the new alternatives system used by the nvidia driver packages, so in order to install nvidia drivers you will have to install them from the command line:  
[LIST]
[*] sudo apt-get install nvidia-current (or nvidia-173 or nvidia-96) 
[*]select the alternative that matches the driver that you have installed  
[LIST]
[*] (e.g. /usr/lib/nvidia-current/ld.so.conf for nvidia-current): 
 sudo update-alternatives --config gl_conf 
[/LIST]
[*]update the ld cache:  
[LIST]
[*] sudo ldconfig 
[/LIST]
[*]then configure your xorg.conf with:  
[LIST]
[*] sudo nvidia-xconfig 
[/LIST]
[*]And restart your computer.
[/LIST]

---

### Post by jerrynewt on 2010-01-20
Ok completed everything (also removed the 7machines ppa and nvidia-current prior to starting) and afterwards same result. Hardware drivers show nvidia-current activated but not in use and nvidia x server settings (still 2 entries) will not activate.

---

### Post by chrismine on 2010-01-20
I had the same problem. I removed all nvidia drivers with Synaptic. Then I installed again from command line - sudo apt-get install nvidia-current and ran sudo nvidia-xconfig and it worked.

Hope it helps.

---

### Post by jerrynewt on 2010-01-20
Mmmmm tried that, now I have Nvidia_current is now activated and currently in use.Also now I have Nvidia accelerated grahics driver (version current) [Recommended]. I tried to change to the latter to see what happend and was advised I do not have permission to change it. Still have the 2 Nvidia X Server Settings listed in System-Admin and neither one of them work. So now the driver is recognized but no xserver settings.

---

### Post by | MM | on 2010-01-21
Perhaps i am retarded, but i cannot get my driver to load dispiste the recommendations in this thread.  I always wind up with the x rescue screen.

I remove all traces of nvidia packages.

i apt-get install nvidia-current

i run ldconfig

i run nvidia-xcong

i restart

i get a low res rescu screen if i use that ppa people go on about, or if i use main repo's i get some error about failed to load the nvidia module, thent he low res x rescue screen.

Nvidia 9800, updated to kernel-11 etc this morning.

Without the nvidia module loaded, my fans (on the gfx card i presume) run at full speed, which is driving me completely raving mad... lol](*,)

---

### Post by | MM | on 2010-01-21
Success!

Heres what *I* did:

1.With no traces of nvidia, install nvidia-current from synaptic.

2.Run [FONT="Courier New"]sudo nvidia-xconfig[/FONT].  The file it produce gave me errors, so...

3.Edit the xorg.conf so only the following remians ([FONT="Courier New"]sudo gedit /etc/X11/xorg.conf[/FONT]):
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```

4. Restart.

Hopefully all is well!

---

### Post by jmmL on 2010-01-24
I'm still having this problem. I followed the official steps of install, update-alternatives, nvidia-xconfig then ldconfig. I also edited my xorg.conf as MM suggested, but still no luck.

How do you remove all traces of nvidia? I wonder if my problem might be that I had earlier installed driver's direct from nvidia but I uninstalled these with nvidia's utility before installing nvidia-current from the repos.

---

### Post by jerrynewt on 2010-01-24
Am I missing something?? There is no xorg.conf in Lucid. I have a XF86Config and an xorg.conf.failsafe. Will creating an xorg.conf file interfere with the XF86Config ??

---

### Post by jerrynewt on 2010-01-24
Bump

---

### Post by zenarcher on 2010-01-25
I don't know that this is the right way to install the Nvidia drivers and get them working, but it's worked for me two or three times with Alpha 2.

First, I installed the Seven Machines repository.  Then, from Synaptic Package Manager, I installed the Nvidia 190.xx packages shown in Synaptic.  Following that, I opened Hardware Drivers from System....and clicked to install the newest.  After that and a reboot, my Nvidia drivers have been activated and working just fine.

Cheers,
zenarcher

---

### Post by autocrosser on 2010-01-25
I've got a xorg.conf I use & ---no, it won't muck with your install....if you want, I'll post mine (it's a custom due to the SLI system I use, but it works with single cards also....)

---

### Post by jerrynewt on 2010-01-25
Yes post it please. I can use all the help I can get !! Thanks again.

---

### Post by illbashu on 2010-02-26
Did anyone find a fix for this?

---

### Post by philinux on 2010-02-26
> **illbashu said:**
> Did anyone find a fix for this?

Yes. Deactivate nvidia-current. Make sure your system is fully up to date.

Reboot to pick up the latest kernel. Activate nvidia-current.

---

### Post by illbashu on 2010-02-26
> **philinux said:**
> Yes. Deactivate nvidia-current. Make sure your system is fully up to date.

Reboot to pick up the latest kernel. Activate nvidia-current.

I tried removing and reinstalling it and restarting like 5x already it didn't work.

---

### Post by illbashu on 2010-02-28
BUMP! Still looking for a fix for this.

---

### Post by leveliv on 2010-03-09
yes it is rather annoying, I can't run any OpenGL apps without this.

---

### Post by Owen.C93 on 2010-03-09
> **jerrynewt said:**
> Bump
I had to make a xorg.conf. I'm not sure on the exact template but mine is as follows.
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```However I have messed around with it so use with caution.

---

### Post by whoop on 2010-03-16
Shouldn't this issue resolve itself?
Wasn't the latest nvidia driver "dangerous" to use because of a bug that causes the fan to run to slow (risk of frying your card when using heavy 3D apps).

I am suffering the same issue, but am thinking it will be fixed, could be wrong...

Anyhow: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997)

---

### Post by envis on 2010-03-25
> **chrismine said:**
> I had the same problem. I removed all nvidia drivers with Synaptic. Then I installed again from command line - sudo apt-get install nvidia-current and ran sudo nvidia-xconfig and it worked.

Hope it helps.

that did not work for me on nvidia amd64

after i did that and restarted the computer was in 640x480
there was only 1 driver listed in hardware drivers instead of 3 like before
the only 1 driver is green but still says "installed but not in use"
i can use the nvidia x server settings but it now only offers me 640x480 or 320x240

looks like im gonna have to reformat.. i guess maybe ill go for ubuntu 9 this time...

and its really hard to use the synaptic package manager in 640x480 everytime you try to click something the window moves under your click as you click. to click stuff you have to aim like 3 centimeters under it.... thats like some feature that is probably designed to be useful that making my life hard..

---

### Post by mattman on 2010-03-25
I installed the current nvidia driver via the offcial Ubuntu repos and it works well but jockey shows the driver as activated but not in use.

---

### Post by lidex on 2010-03-25
> **mattman said:**
> I installed the current nvidia driver via the offcial Ubuntu repos and it works well but jockey shows the driver as activated but not in use.

That's what I have...seems to work just fine

---

### Post by dino99 on 2010-03-25
this is a known jockey issue but no importance, only information is wrong

---

### Post by edkmho on 2010-03-26
HI guys, I have the same issue, but my was with additional problem. I was stuck with just 2D, when i tried to enable the desktop effect, it won't let me. By any chance anyone experienced this. 

Please help. Many thanks.

---

### Post by dino99 on 2010-03-26
> **edkmho said:**
> HI guys, I have the same issue, but my was with additional problem. I was stuck with just 2D, when i tried to enable the desktop effect, it won't let me. By any chance anyone experienced this. 

Please help. Many thanks.

i dont use compiz but you might report that bug if no one else have done yet: ubuntu-bug jockey

---

### Post by dazer26 on 2010-03-26
Hmm i'v had the same problem in Lucid for a while now.  It's almost as if the nouveau driver is actually being used, cause 2d is fine, and compositing seems fine, but as soon as I try to play a 3d game (urban terror, WoW) I get about one frame per second.  At first I thought it was because of new sketchy Nvidia driver, but my GPU temp was fine.  When I first installed Lucid a couple of months back the 3d worked great (better than in 9.10).  I'm gonna try and uninstall/reinstall and reboot see what happens.

---

### Post by marcha23 on 2010-03-27
Well to get 3D working I had to replace /usr/lib/xorg/modules/extensions/libglx.so with link to /usr/lib/nvidia-current/xorg/libglx.so.195.36.15

---

### Post by zorkobra on 2010-04-17
> **jerrynewt said:**
> Under System-Admin-Hardware Drivers I see nvidia-current as activated but not currently in use.There are two entries for Nvidia X Server Settings and when clicked neither one of them work. Also x server crashes when trying to open either one of them. Any one else having this problem ?? Any work around would be appreciated. Thanks
An easy GUI way to enable nVidia driver.  Requires 2 reboot.  
Select SYSTEM > ADMINISTRATION > HARDWARE DRIVERS and UNinstall both nVidia drivers.  
Exit and reboot.
Select SYSTEM >PREFEENCES > APPEARANCE > VISUAL EFFECTS > EXTRA (or normal) 
Exit and reboot.
Worked perfectly for me... hope it works for U as well

---

### Post by eco2geek on 2010-04-25
> **marcha23 said:**
> Well to get 3D working I had to replace /usr/lib/xorg/modules/extensions/libglx.so with link to /usr/lib/nvidia-current/xorg/libglx.so.195.36.15
Thanks, that also solved the problem for me (which, specifically, was that it wasn't loading NVIDIA's glx module).

---

### Post by schmolch on 2010-04-25
This **** is not working for me.
I tried to switch from the nouveau-driver (which is useless on my triple-head setup) to nvidia 3 times.
I removed all traces of nvidia-packages, ran ldconfig, installed nvidia-current and rebooted.
All i get is a splash screen for a second followed by horizontal white lines and the box freezes.
Im soo tired of this crap.
I would pay 1000 bucks for a OS that just works but its all just bullshit.

---

### Post by schmolch on 2010-04-25
And why have you removed the option to boot to a console login?
And why did you switch the key to go to the grub menu from esc to shift, why is there no announcement on the top of this forum?

****!

---

### Post by lidex on 2010-04-25
> **zorkobra said:**
> An easy GUI way to enable nVidia driver.  Requires 2 reboot.  
Select SYSTEM > ADMINISTRATION > HARDWARE DRIVERS and UNinstall both nVidia drivers.  
Exit and reboot.
Select SYSTEM >PREFEENCES > APPEARANCE > VISUAL EFFECTS > EXTRA (or normal) 
Exit and reboot.
Worked perfectly for me... hope it works for U as well

After some recent updates that works for me.

---

### Post by mc4man on 2010-04-25
> I would pay 1000 bucks for a OS that just works...

Well only a couple of hundred for windows 7, you may consider that a bargain.

I've never had any issue switching from nouveau to nvidia-current or back again.

With nouveau in use and **nvidia-current installed** I simply
```
sudo update-alternatives --config gl_conf
```
pick the nvidia-current (auto mode usually

Probably not needed this direction but never  hurts
```
sudo ldconfig
```

Then

```
sudo update-initramfs -u
```
```
sudo nvidia-xconfig
```
restart

---

### Post by schmolch on 2010-04-25
I ran the pkg from nvidia and it works now.
Thanks for the advice though.

---

