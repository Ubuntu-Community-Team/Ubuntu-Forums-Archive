---
title: "NVIDIA driver solution - upgrade from 7.10 gutsy to 8.04 hardy"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by jKeats3 on 2008-04-21
I use an NVIDIA n-force 630i/integrated Geforce 7100 chipset, and I was having some significant problems with the Nvidia 169.12 graphics driver.  I was using the old kernel, 2.6.24-14-generic, with Gutsy, and 2.6.24-16 with Hardy.  I solved the problem by reverting the gcc compiler version from 4.2 back to 4.1 and THEN reinstalling the nvidia driver over the 2.6.24-16-generic kernel.

To change the gcc compiler version you are using, you have to edit the CC environment variable.

To check your kernel version, type "uname -r".  To check the gcc version that is currently set as default on your machine, type "gcc -v"

---

### Post by jKeats3 on 2008-04-23
Update on this issue:

Running NVIDIA n-force 630i/Geforce 7100 integrated video

Due to some update that was released in the last couple of days, this driver solution is no longer working.  I am now on kernel 2.6.24-16-generic, and regardless of whether I have gcc-4.1 or gcc-4.2 enabled as default when the NVIDIA driver (version 169.12) compiles a kernel module at restart, the driver works for that session only, but when I reboot the machine, X starts up in low graphics mode.

Note: this isn't a problem with /etc/X11/xorg.conf, because I explicitly tell the NVIDIA installer not to replace the xorg.conf file when I reinstall it, yet as a result, correct NVIDIA graphics still operate at full resolution for that session even when the installer doesn't update xorg.conf.  It must be a problem with the kernel module / kernel interface that is somehow supplanted by a default version, or overridden due to some compatibility check, at startup.

Note: I had this exact problem with NVIDIA driver 169.04 and kernel 2.6.24-14-generic, and it wasn't fixed until I installed the updated 169.07 NVIDIA installer, which solved the problem.  So perhaps I will have to wait for NVIDIA to release a driver version beyond 169.12 so that this particular problem is solved with this particular kernel.

Does anyone have an inkling of what may be going on here?  These NVIDIA drivers seem to cause almost incessant problems, every time a new kernel release or update is sent out.  Is there some static link they are using that needs to be made dynamic/symbolic, perhaps?

---

### Post by psyke83 on 2008-04-23
You are creating these problem yourself by electing to manually install the nvidia drivers. Use the official Ubuntu-supplied packages and you will be ok, even with future updates (providing the horrible nvidia-installer can clean up all the cruft left behind).

Using the latest version of the nvidia driver package you have been using, use the uninstaller, e.g.:

```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
```

Then, install the following packages:

```
sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall
```

---

### Post by Creshal on 2008-04-27
I'm having the same problem as jKeats3, both with the installer of nvidia and the package from the Ubuntu-repository. The driver works fine, until I reboot the system. I always get an "(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!"-Error in the logfile and the driver only works after a reinstallation.
It really seems that kernel 2.6.24-16 and forceware 169.12 don't work together... or is there any solution for this problem?

---

### Post by jgriffinpark on 2008-04-27
I too am having a very strange problem with NVIDIA drivers:

Basically, it was loading into safe graphics mode every time I rebooted, so I overwrote the xorg.conf file with a generic file, and installed NVIDIA drivers with the ENVY script. This has allowed me to get the correct screen revolution (No more eyestrain!:)) but the NVIDIA card still isn't functioning correctly (ie no compiz, project 64 etc)

GRUB still shows the 7.10 kernel, because during upgrade, I chose to keep the menu.lst file from before, since I'd modified it. I think that this is the root of my problem...so I tried to replace the old kernel in menu.lst with 2.6.24-16, and got a host of brand new problems (sound messed up, ndiswrapper non-functioning) 

This is all very frustrating, since I just wanted to do a simple upgrade, and I'm a complete linux newbie.
Does anyone have any experience with similar problems? I really really really don't want to do a fresh install... Much appreciated.

---

### Post by brad103 on 2008-04-27
I am having a similar problem with my nVidia Quadro NVS 130M that worked perfectly under Fiesty (using Envy). Now when loading in Hardy my Xorg.0.log complains:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

$ uname -r
2.6.24-16-rt

EDIT: Duh! My problem was not knowing what [rt]("https://wiki.ubuntu.com/RealTime/Hardy") means. I got rid of that kernel now and switched back to generic and envy worked great. Good luck to those still having issues.

---

### Post by kirux on 2008-04-28
I have experienced the same problem jgriffinpark related. I am running Ubuntu 8.04 on a Hp Pavilion Dv6232.

2.6.24-16 kernel solved the NVidia problem, but sound and wifi were all messed up.

I solved the problem using 2.6.24-16-generic version of kernel. After that, all was working except the wireless card, but using the Restricted Drivers Manager should solve this.

Now the only thing is that my USB mouse does not work, I think this problem is related to running dpkg-reconfigure xserver-xorg a few times trying to solve the NVidia issue. Some help here will be great.

---

### Post by zombix on 2008-04-28
I tried everything, envyng, removing old kernel, reinstaling drivers... nothing helped. Only thing that worked was to download drivers from nvidia
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/NVIDIA-Linux-x86-96.43.05-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/NVIDIA-Linux-x86-96.43.05-pkg1.run)

that tool recompiled drivers.

now I have glx and accellerated drivers working, but still no option in hadrware drivers, I guess it is ok that way.

---

### Post by lewdev on 2008-04-28
I have the same problem.  I am also a *nix newbie.  I have got as far as running the above link and stops where it asks for the kernel source.  I don't know where or how to get that.

When it starts up with [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] configured to run nvidia drivers, it gives me this message:

```
kinit: trying to resume from /dev/disk/by-uuid/2e132103-db3d-4131-85f7-9cb351b4ff531
kinit: No resume image, doing normal boot...
```

Then, I'm prompted to login in a terminal, where I have attempted to retrieve drivers using the above mentioned program.

I'm running on an eMachine:
AMD Athlon XP Processor 3000+
NVIDIA Geforce4 MX

---

### Post by bcspratt on 2008-04-28
Hey jgriffinpark,

You might want to leave the reference to the old kernel in menu.lst as if the update goes astray you should still be able to use the old kernel as a fall back till you figure out the problem.  I think you should be able to put back the 7.10 kernel references then you just have to add/duplicate a new entry for the 8.04 kernel.

Regarding Nvidia drivers.  Neither the 2.6.24.16-rt nor the 2.6.24.16-generic kernels had the new built in Nvidia drivers I thought they were supposed to have.  I could not compile the driver I downloaded from Nvidia under the "rt" kernel but could under the generic kernel.  Not sure what the rt kernel is about, I'll have to look that up.  I used the command 
"bash ./NVIDIA-Linux-x86-100.14.19-pkg1.run"  to compile my driver from the command line in the recovery mode for 8.04 (not 7.10) and got my video working again.

God Bless

---

### Post by jgriffinpark on 2008-04-28
Dear bcspratt:

I have saved the 7.10 kernel in menu.lst, as it has fewer bugs for me as of right now. I am debating doing a fresh install of 8.04, but from what you've said it seems as if the restricted drivers would still be inadequate?
I just want a fully functioning OS like I had two days ago... :(

---

### Post by UncleFoo on 2008-04-29
> **psyke83 said:**
> You are creating these problem yourself by electing to manually install the nvidia drivers. Use the official Ubuntu-supplied packages and you will be ok, even with future updates (providing the horrible nvidia-installer can clean up all the cruft left behind).

Using the latest version of the nvidia driver package you have been using, use the uninstaller, e.g.:

```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
```

Then, install the following packages:

```
sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall
```

Thank you thank you thank you. This worked!

I have Envied a bunch of times, read a pile useless info, installed, unistalled, etc. That last little reinstall snippet did the trick. Why doesn't it work when you install with synaptic? That would be much nicer.
:guitar:

---

### Post by amireldor on 2008-04-29
i did what psyke83 suggested on post #3 and it worked for me too!

the only problem i have now is that the maximum resolution is 1024x768 instead of 1280x800 (i'm on a hp dv6xxx laptop too) - can someone help me please?

---

### Post by tdeboeser on 2008-04-29
I had the same problem as OP.  EnvyNG couldn't fix my problem ( with it installing either the new driver, or older one ).  Installing the drivers from Ubuntu repos didn't work either.  

BUT

Downloading the installer/driver ( ver. 169.x ) from nvidia did the trick.  My resolution and compiz stuff are working now.

Now to get rid of this firefox beta... ugh...

Tom de
Geforce 7600

---

### Post by kaaredump on 2008-04-29
My original plan was to set up an old Dell as a file/ssh server, did so using Ubuntu 7.10. 
But got quite baffeled by all the eye-candy, so the old Dell soon got hooked up to the 40" LCD in my livingroom :).

The other night I go got a message tha an upgrade was avaliable(8.04), and started the update. Things went well, but when logging in (soon after the splash screen & progressbar expires the graphisc turned blury. 

Managed to get it straight by disabling the nVidia driver, but now none of the eye candy works. 
My graphics card is a LeadTec or something, think its powered by an NVIDIA GeForce FX 5200 GPU.

Any ideas??

---

### Post by PedestrianIcon on 2008-04-30
> **jgriffinpark said:**
> I too am having a very strange problem with NVIDIA drivers:

Basically, it was loading into safe graphics mode every time I rebooted, so I overwrote the xorg.conf file with a generic file, and installed NVIDIA drivers with the ENVY script. This has allowed me to get the correct screen revolution (No more eyestrain!:)) but the NVIDIA card still isn't functioning correctly (ie no compiz, project 64 etc)

GRUB still shows the 7.10 kernel, because during upgrade, I chose to keep the menu.lst file from before, since I'd modified it. I think that this is the root of my problem...so I tried to replace the old kernel in menu.lst with 2.6.24-16, and got a host of brand new problems (sound messed up, ndiswrapper non-functioning) 

I too had exactly this problem after upgrading.  

As it turns out, keeping the old menu.lst file was the root of my problem, as I was booting into the old 2.6.22-14 kernel instead of the new hardy kernel (2.6.24-16).  Fixing the grub menu and booting into the correct kernel solved all my problems right away.  (Just replaced all instances of 2.6.22-14 with 2.6.24-16 in my menu.lst fixed everything)

Not sure why you're having problems with sound or ndiswrapper ... both of those still work just fine for me after the upgrade. :/

From the responses here, it seems like at least some of the people posting in this thread have the same issue I did.  Hopefully this will help at least some of you out!

---

### Post by Creshal on 2008-05-02
Hmpf. I'm still having problems with the nvidia driver, that it won't run after a reboot.
Nope, I did a fresh installation of Ubuntu 8.04, so there are no old kernel versions which could cause the problem. There is just 2.6.24-16-generic on this machine.
Nope, using the version from the repository doesn't help (and it can't be uninstalled).
Nope, the version direct from nvidia doesn't help.
Nope, a clean xorg.conf doesn't help (after a reinstallation, the driver works with the old conf perfectly).

Is there anything else I could try (except switching to ATi...)?

---

### Post by little_buzzier on 2008-05-02
I did what Psyke83 wrote, it didn't work for me (Nvidia GeForce 7600).

As I am not a genius for command lines, could someone translate me a solution that have work for some in a human understandable language? :)

Thanks!

---

### Post by Creshal on 2008-05-02
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall
```
Simply deinstalls the driver installed by nvidia's driver and installs the repository version.

---

### Post by little_buzzier on 2008-05-02
I just got that...
  
```
sh: Can't open NVIDIA-Linux-x86-169.12-pkgl.run

```

and if I try the next apt-get, it install right but it doesn't solve the problem...

---

### Post by Creshal on 2008-05-02
Well, you need to run sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
in the directory where you placed the downloaded NVIDIA-Linux-x86-169.12-pkg1.run...

---

### Post by Kralnor on 2008-05-03
@psyke83

I had some trouble with Hardy Heron not resuming properly from hibernation - all I got was a blank screen. But after running

```

sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall

```

I am now able to resume properly.

Thanks a lot!

---

### Post by Creshal on 2008-05-04
Well... fixed my problems. After I unistalled *all* packages from the restricted-repository, the driver works even after reboots.

---

### Post by paul higginbotham sr on 2008-05-07
when thinking about upgrading, I thought, how bad can it be, my machine comes with linux installed as an option. Well, it is a dell e1505 with nvidia card. Video booted okay but when I tried to get it functioning away from legacy, it messed up till now after working on it it has no options, but working good. My sound is trash and I have a lot of multimedia here. The broadcom wireless crashed on install and I have been working on it for 3 days. If I only knew, I would have used Gutsy for 5 more years no problem.

---

### Post by Hellbourne on 2008-05-10
> **psyke83 said:**
> You are creating these problem yourself by electing to manually install the nvidia drivers. Use the official Ubuntu-supplied packages and you will be ok, even with future updates (providing the horrible nvidia-installer can clean up all the cruft left behind).

Using the latest version of the nvidia driver package you have been using, use the uninstaller, e.g.:

```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
```

Then, install the following packages:

```
sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall
```

Still doesn't work for me and I'm very frustrated. I uninstalled the manual installation and tried reinstalling the Ubuntu-supplied packages but I still keep getting the darn low-graphics mode. Any suggestions?

Thanks,

Amit.

---

### Post by Micool on 2008-05-12
From a fresh new install, I have the following problem at each time I start a kubuntu 8.04, kde 3.5.9 ( Hardy ):

X is very slow when kdm starts the images are loaded line by line ... If anyway loading is successfull, kde also has the problem: menus, images, task bar etc.. are slow to display.

If CRTL ALT Backspace is done to restart X, X restart correctly KDM and KDE works then fine.

removing the 169.12 drivers solve this problem, but then, no hardware acceleration can be used.

4 differents fresh new installs had same effects with my 8800 GTX with HARDY

The nvidia drivers I used with gutsy worked fine with gutsy

I don't know how to trace this problem,

Help would be largely appreciated !

---

### Post by jolyan on 2008-05-22
> **psyke83 said:**
> You are creating these problem yourself by electing to manually install the nvidia drivers. Use the official Ubuntu-supplied packages and you will be ok, even with future updates (providing the horrible nvidia-installer can clean up all the cruft left behind).

Using the latest version of the nvidia driver package you have been using, use the uninstaller, e.g.:

```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
```

Then, install the following packages:

```
sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall
```

This worked for me too, I had tried sooo many other options, but never got my card (MSI 7600GS Nvidia) recognised, best I could via other options was using the vesa driver and manually configuring the screen. But all this was resolution and no graphics extension.

Running the restricted modules options gave me the card in the restricted drivers and all pistons firing. Three days of headaches cured in one post, ta very muchly. :)

---

### Post by Kralnor on 2008-06-03
Seems like it's broken again. After resuming the process doesn't get any further than "Suspending Console(s)". Either that happens or there is simply a black screen.

I tried reinstalling the nVidia drivers again but without luck.

I suspect a recent kernel update in Synaptic messed it up. Can anyone confirm that?

---

