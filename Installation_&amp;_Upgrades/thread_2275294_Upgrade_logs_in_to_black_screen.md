---
title: "Upgrade logs in to black screen"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by marklovescoffee on 2015-04-25
Dear everyone,

I just upgrades to Kubuntu 15.04, and it works great up until the login screen. Once I try to log in, it shows the progress bar, and then loads to a blank desktop. I can see and move the cursor around, and get some feedback by pressing alt+f4, and typing characters brings up the desktop search, but other than then, nothing. Failsafe login doesn't do anything. I've also tried without systems and using older kernels, and none of them boot either.

I can get into the terminal via alt+f2. My guess is it's a graphics card problem (I have a NVIDIA card), however I'd like to get some advice before I start running commands.

Any suggestions? Thanks.

And p.s. whoever designed the Kubuntu login, it's great. Absolutely beautiful.

---

### Post by marklovescoffee on 2015-04-25
And some more hints, after lshw it shows up as unclaimed. It also shows an Intel driver. Is there any way I can switch to this temporarily just so I can get my work done tonight?

---

### Post by Bashing-om on 2015-04-25
marklovescoffee' Hummm ...

Hybrid graphics ? Release 15.04 is supposed to have better support in this realm ..
Lap top machine ? What options do you have in bios to disable one of the maybe graphic chip sets ? ( so you can get your work done) .

Show us what we are working with graphics wise; post back the outputs - between code tags - of terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

Then we might want to examine the Xorg log file. See what is taking place.

As the system is stable at the Command Line Interface, we can conclude the issue is with the GUI .

[INDENT][INDENT]we start with a looksee
[/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-25
I'm typing this on phone so bear with me. I've typed out what seems relevant. I've also included a screenshot with all the details.

lspci -vnn | grep VGA -A 12
VGA compatible controller [03001: Intel Corporation Broadwell -U integrated graphics [8086:1616] (rev 09) (prog-if 00 [VGA controller])
Subsystem: Lenovo Device [17aa:3907]
Capabilities: access denied
Kernel driver in use: i915

Sudo lshw -C display
*-display
Description: VGA compatible controller
Product: broadwell integrated graphics
Configuration: driver: i915 latency=0
*-display
Description:3d controller
Priduct : gm108M (geforce 840m)
Capabilities: PS MSI pciexpress bus_master cap_list
Configuration: driver= nvidia latency=0

I'm also getting some weird error about "DRM:gen8_IRQ_handler - the master control interrupt lied (SDE)!"

---

### Post by Bashing-om on 2015-04-25
marklovescoffee; Well;

Yeah we do have hybrid graphics !
Intel/Nvidia.
Let's check and see what is installed to deal with this switchable graphics situation.
Post back :
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT]there is great hope
[/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-26
Thanks for your help. I tried switching off the discrete graphics in the bios, but no luck.

The command gives me this:
Rc libcuda1-346 346.59-0ubuntu amd64 NVIDIA CUDA runtime library

Is that useful?

---

### Post by Bashing-om on 2015-04-26
marklovescoffee; Hey;

Not at all what I expected to see for the Nvidia installed modules ... 
CUDA ??? Is this a release upgrade from 14.10 to 15.04 ?
Where and how and why does CUDA have a play in this installation ?

Might be we consider strongly, purging the Nvidia modules; and re-installing the Nvidia graphics driver.

What now returns:
```

ubuntu-drivers devices
ubuntu-drivers list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

to give us a hint on what we need to do.

[INDENT][INDENT]CUDA
[INDENT][INDENT][INDENT]a horse of a different color
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-26
Bashing-om,

I've been messing with the system a bit myself, so perhaps that's how I got the CUDA driver installed. I already tried purging NVIDIA and reinstalling, along with some other ideas from Google, but I'm willing to try it again with a bit of expert guidance!



Ubuntu-drivers devices:

Driver: intel-microcode - distro non-free

= /SYS/devices/pci0000:00/0000:00:1c.4/0000:04:00.0 ==
Vendor: NVIDIA corporation
Model: gm108 [GEForce 840M]
Driver: NVIDIA-346-updates - distro non-free
Driver: xserver-xorg-video-nouveua - distro free builtin
Driver: NVIDIA-346 - distro non-free
Driver: nvidia-340-updates - distro non-free
Driver: NVIDIA-349 - third-party free recommended
Driver: nvidia-340 - distro non-free

Ubuntu drivers list:

Nvidia-349
Nvidia-346-updates
Nvidia-340-updates
Intel-microcode
Nvidia-346
Nvidia-340

---

### Post by marklovescoffee on 2015-04-26
Do you recommend trying to purge NVIDIA again? If so, what exactly should I install after that? Thank you so much.

---

### Post by Bashing-om on 2015-04-26
marklovescoffee; Welp ..

Far from an expert, just been around for a while ... :)

Let's focus on attempting to remove CUDA .. then the Nvidia drivers, then we install the Nvidia module(S).

OK, what returns:
```

sudo find / -name nvidia-cuda-toolkit
sudo find / -name "NVIDIA-Linux-*"
ls -al /opt/cuda
ls -al ~/NVIDIA_GPU_Computing_SDK
ls -al /usr/bin/nvidia-uninstall

```
will take the 'find' command some time to search the file system, patience !

We clean up, 
[INDENT][INDENT][INDENT]wipe the sweat off
[INDENT][INDENT][INDENT]see what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-26
Both find commands return nothing, and the ls commands list there's no such directory or file...

Is this unexpected? Any other suggestions? Where to go to next?

And thank you so much for your patience.

---

### Post by Bashing-om on 2015-04-26
marklovescoffee; Well ...

> **marklovescoffee said:**
> Both find commands return nothing, and the ls commands list there's no such directory or file...

Is this unexpected? Any other suggestions? Where to go to next?

And thank you so much for your patience.

Just sorta 'unexpected' ; in and of it's self is not bad. Just means I need to dig just a bit deeper ... that CUDA package with the mark of 'rc' says that the package is (R)emoved, but config files remain .. We need to make sure we find these config files and remove them ...
It is late here my time and my mind is a bit blurry now .. let me have some time to cogitate and we have a go at it in my AM .

[INDENT][INDENT]keep'n it clean behind us
[/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-27
Yes, get some rest. Your day is my night, so in the meanwhile, I will use the find command and see if I can find anything that might be of help to us. I'll post back with anything I find.

Thanks again!

---

### Post by marklovescoffee on 2015-04-27
I finally have a computer I can use! So I can type much faster and easier now. Still can't copy and paste, but it's much better than on the phone!

Did some searching of my own based on the commands you showed before.

sudo find / -name *nvidia* finds stuff in /var/cache/apt/archives, usr/src/linux-headers-3.19.0-15, usr/bin/nvidia-detector, usr/share/app-install, usr/lib/, and /lib/modules/3.16.0-34-generic/kernel/drivers.

[COLOR=#000000]sudo find / -name *cuda* finds stuff in /var/cache/apt/, var/lib/dpkg/info, /usr/source, usr/include, and usr/lib.

[/COLOR]If one of those is useful I can share all the results from it.

---

### Post by Bashing-om on 2015-04-27
marklovescoffee; Top of my Morning to you .

OK, yeah, there is a bit of clean up to do ...
Let's see what the package manager will do for us:
```

sudo apt-get purge nvidia-\*
sudo apt-get remove --purge nvidia*

```
Repetitive, yes, just to see what there might be.

Make sure now we have no unwanted directives in your profile config file(s):
```

cat ~/.bash_profile
cat ~/.bashrc
ls -al /usr/local/cuda*

```

Cover our bases here, as I do not know how CUDA got onto the system; make sure there is no PPA  - for either cuda or Nvidia - involved:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l cuda

```

With these known we can proceed to a final cleanup in preparation to install the graphics driver.


[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-28
Bashing-Om,

Just ran all the commands. Here's what I got.

First, I purged nvidia using the first two commands. Seems normal.

cat ~/bash_profile returned nothing, but cat ~/bashrc returned a huge amount of text, larger than the screen. Can't find anything that seems to suggest NVIDIA in there though. I don't know how to view the stuff that's off-screen though. Is it possible to search it or view the off-screen texts to search to see if anything is related to the graphics?

ls -al usr/local/cuda also returns nothing.

cat -n /etc/apt/sources.list returns a bunch of sources. All start with deb and have ubuntu.com or canonical.com in the link, so I think they are all normal.

tail -v -n +1 /etc/apt/sources.list.d/* returns:
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) vivid main

I know I added that while trying to fix the drivers, and I'm guessing I should remove that, right?

dpkg -l cuda also doesn't return anything.

Does this help?

---

### Post by Bashing-om on 2015-04-28
marklovescoffee; Hey, hey ...

Proceeding with our clean up.

Not having the config file ' ~/bash_profile ' is expected, but needed to check that it is not relevant to our issue.

I do need to see the contents of ' ~/.bashrc  ' ... Make sure the directive to add a no-longer-in-existence path is removed (if it does exist ) .
If you are not able to copy and paste from terminal we have a couple of options to relay that file. I like easy and fast so I propose we use ubunu's paste site to do this:
```

sudo apt-get install pastebinit
pastbinit ~/.bashrc

```
The result will be a URL returned to terminal. post that URL back to the thread and we will access the referenced file whose contents is the '.bashrc' file.

And yepper, the source of a lot of our grieve is the existence of ' xorg-edgers ' PPA. Each time the system is updated/upgraded there is an attempt to install drivers on a broken system in such a manner it can not complete -> broken driver !
Let's remove that source:
```

sudo ppa-purge xorg-edgers

```

Once the system is clean ... then we install an appropriate graphics driver ... Further discussion on this to see what you do need and what you want to do.

[INDENT][INDENT]making progress
[INDENT][INDENT][INDENT]s l o w l y 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-28
Okay, did what you suggested. The ppa is uninstalled successfully.

I also installed the pastbinit. It's really useful! This is the link to my bashrc: [www.paste.Ubuntu.com/10932195](www.paste.Ubuntu.com/10932195).

All seems to be going smoothly. Now which drivers do you suggest I install? Thanks again.

---

### Post by Bashing-om on 2015-04-28
marklovescoffee; OK;

Good to go ...
Key combo ctl+alt+F1 to gain a console interface:
do:
```

sudo service lightdm stop
sudo apt-get remove --purge nvidia*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
ubuntu-drivers autoinstall

```

reboot and now
[INDENT][INDENT][INDENT]tell me all is finer than a frog's hair
[/INDENT][/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-28
Still running into an error at the last command. It's telling me the /var/lib/dpkg/lock is open. I tried it with sudo as well and still it gives the same error. Any suggestions? I also tried restarting and still I have this problem. Doesn't seem likely that any process is running using dpkg..

---

### Post by marklovescoffee on 2015-04-28
Ah, never mind. Guess I needed a sudo at the end for the installation part too! Trying it, and I'll let you know if it's successful.

---

### Post by marklovescoffee on 2015-04-28
It's not successful. After a restart it still only logs in to a black screen. Any other ideas?

---

### Post by Bashing-om on 2015-04-28
marklovescoffee; Welp :yeah ..

Let's see what we are working with:
```

lspci -vnn | grep VGA -A 12

```

If and what graphics driver is loaded :
```

sudo lshw -C display

```

and as all else has failed, read the instructions:
```

cat /var/log/Xorg.0.log
cat ~/.xsession-errors

```

See if we get any hints on what is not taking place.

[INDENT][INDENT]no quitting now
[/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-29
Ran the four commands you listed, and outputted them to pastebinit (really useful site!)

lspci -vnn | grep VGA -A 1200:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:3907]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at e2000000 (64-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: Lenovo Device [17aa:3907]
    Flags: bus master, fast devsel, latency 0, IRQ 48[COLOR=#000000]
[/COLOR]sudo lshw -C display  *-display
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:e2000000-e2ffffff memory:c0000000-cfffffff ioport:5000(size=64)
  *-display
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:49 memory:e3000000-e3ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128)


cat /var/log/Xorg.0.log
[http://paste.ubuntu.com/10940101/](http://paste.ubuntu.com/10940101/) ( really long)
[COLOR=#000000]
[/COLOR]cat ~/.xsession-errors
[http://paste.ubuntu.com/10940135/](http://paste.ubuntu.com/10940135/) (extremely long)

Are these of any help?

Also I'm frequently getting this error message "[drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!" Any hints?

Thanks again.

---

### Post by Bashing-om on 2015-04-29
marklovescoffee; Yukkie Poo !

You tell me what is going on .
What in the world are we working with ? Is this an server install with GUI's added ... is this an ubuntu install with (k)ubuntu desktop (KDE) added ?

What have you done here :
> 
[    17.319] (**) |-->Inactive Device "intel"
[    17.321] (--) PCI:*(0:0:2:0) 8086:1616:17aa:3907 rev 9, Mem @ 0xe2000000/16777216, 0xc0000000/268435456, I/O @ 0x00005000/64
[    17.321] (--) PCI: (0:4:0:0) 10de:1341:17aa:3813 rev 162, Mem @ 0xe3000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00003000/128
-bk-

[    17.611] (II) NVIDIA GLX Module  346.59  Tue Mar 31 13:38:58 PDT 2015

[    17.779] (II) NVIDIA(0): NVIDIA GPU GeForce 840M (GM108-A) at PCI:4:0:0 (GPU-0)

[    17.779] (--) NVIDIA(0): Valid display device(s) on GeForce 840M at PCI:4:0:0
[    17.779] (--) NVIDIA(0):     none
[    17.779] (II) NVIDIA(0): Validated MetaModes:
[    17.779] (II) NVIDIA(0):     "NULL"
[    17.779] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    17.779] (WW) NVIDIA(0): Unable to get display device for DPI computation.

[    19.986] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].

[    19.986] (EE) intel(G1): Failed to claim DRM device.



Two video display adapters .. in bios have you attempted to disable the Intel chip set ?

Tell me once more what release AND what distribution we are working with, 14.04 ?
----------------------

Can you go back to a stock/standard keyboard and mouse ? See then if all the screaming and hollering and the errors in regards to the keyboard  go away ?
----------------------------

All these errors, and what might cause them blow me away. I am all for a learning experience BUT, this might be one of those times that the Nuclear solution might be best . (Re-)install to get a fresh clean slate with known defaults and build from this firm foundation ??
-----------------------

Presently I do not know what is going on, and as such how to fix.
If You want to continue trouble shooting and get this install stable then pull all peripheral devices and plug in a standard keyboard and mouse. Turn on in bios both sets of display chip sets . Then we try and install graphics drivers suitable for the release that you are running ( 14.04 ?) Which looks to be optimus technology .. and as such we want nvidia-prime and nvidia-settings also installed.
To fix the (D)esktop (E)nvironment, That is presently above my skill set . I have had no experience with (k)ubuntu since release 9.04 ! This conflict really makes me brake hard - IF indeed that is what we have - KDE added to a (u)buntu environment. I do not know how to clean things up, but I am willing to break things to your heart's content.


[INDENT][INDENT]UnGood
[/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-04-30
Bashing-om,

This is just a laptop with Kubuntu installed. Bought it in February, installed 14.10 (stable plasma 4 version), everything worked. Tried to update to 15.04 via the package manager and everything seemed to be successful. Then, I try logging in and that's when I get the blank screen. I have no external keyboard or mouse, only the built-in keyboard, touchpad, and touchscreen.

Because the new KDE uses plasma 5, I'm guessing it's a bug with plasma, although I'm not sure what's going on with my graphics drivers either. Perhaps not though, because the failsafe mode doesn't work either. I'm going to back up my home directory and then some of the ideas mentioned here [http://askubuntu.com/questions/614447/black-screen-after-login-kubuntu-15-04](http://askubuntu.com/questions/614447/black-screen-after-login-kubuntu-15-04). If those don't work, then I'll try to try to purge and reinstall the entire KDE desktop. If this still doesn't work, I guess I will just reinstall Ubuntu from scratch and see if that works. If not, I guess I have no choice but to roll back to 14.10 temporarily, just to have a working system.

Unless you have any other suggestions, this will be my approach. I don't mind messing with the system (every time I do I learn something!) but there's a point where it just becomes simpler to reinstall so that I have a working system. If I can't get things fixed by Sunday I will reinstall.

Thanks again for your help. Even if you weren't able to solve my problems, I certainly appreciated the help!

---

### Post by Bashing-om on 2015-04-30
marklovescoffee; Hey !

Thanks for that explanation. A failed release upgrade do explain a lot .

Let's re-focus and see what we can do to clean things up.
What release does the system think is installed ? show:
```

lsb_release -a
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
then we proceed to make sure the package manager is in a happy state.

it's 'buntu
[INDENT][INDENT]with time effort and a liveDVD
[INDENT][INDENT][INDENT]it is always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by marklovescoffee on 2015-05-03
Bashing-om,

After doing some more Google searching, I've found I can get the desktop to appear by deleting on moving the kde cache folder and then restarting. Of course, I must do this every time I log in or resume from sleep, so this is not an ideal solution. At this point, I'm almost certain the problem is with KDE 5 and plasma rather than Ubuntu, a failed update, or NVIDIA. However, I will run those commands anyway.

The first command tells me I'm on 15.04 and no lsb modules are available.

The second gives:
   1	# deb cdrom:[Kubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main multiverse restricted universe
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse
    37	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner

The third:
[FONT=Verdana]
==> /etc/apt/sources.list.d/xorg-edgers-ubuntu-ppa-vivid.list <==
# deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) vivid main

Do you still think it's a problem with Ubuntu or the installation that can be fixed? Or should I just conclude there's a problem with KDE and roll back to KDE 4, which I know for sure was stable and working just fine?

Thanks again.[/FONT]

---

### Post by Bashing-om on 2015-05-03
marklovescoffee; Hey !

I find no fault with the sources list .. looks to be up solid on vivid.

I am done in for this session. But this has my attention:
> 
# deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) vivid main

On vivid this PPA is not required to install the proprietary driver.
I think though that the next thing is to make sure the package manager is stable; Then take a look at plasma and/or KDE5 .

With a fresh mind I will re-think things in my AM (GMT -5 here ) and take this up once more.

[INDENT]
just a GUI kind of thing
[/INDENT]

---

### Post by marklovescoffee on 2015-05-03
Bashing-om,

Okay, get some rest and we'll figure out what to do!

Right now I have a working system, and although the black screen comes up from time to time, I know how to fix it. I can get my work done and have accessed to the GUI, so although it's not perfect, it's good enough temporarily.

I'm torn between three options - just leaving things the way they are until I get some time off this summer to play with stuff, trying to reinstall 15.04 from scratch, or rolling back to 14.10. I'm pretty sure 14.10 would fix things, but I'd really love to have the latest and greatest, so of course I'd prefer to be on 15.04 if there's a way to make it work.

What do you think about a fresh install of 15.04? Do you think that might do the trick? Or will the problem likely come up again?

And should I remove the PPA you pointed out? Or is leaving it there fine?

Thanks for your insights!

---

### Post by Bashing-om on 2015-05-03
marklovescoffee; Welp:

1) Release 14.10 will reach End-O-Life this July, no point in wasting resources and effort there.
2) Repair the current install - vivid : doable, just takes time and effort to isolate and repair. Well worth the effort for aiding us in progressing up on that learning curve.
3) A fresh clean install is always a good thing when the situation gets out of hand and/or becomes the expedient thing. If one keeps back ups of their personal data it is but a matter of 20 minutes or so and all questions are answered.

I am always for advancing on that learning curve. In this situation my considered opinion is to purge the no-longer-needed xorg-edgers PPA and it's driver, purge the graphics driver and install the driver the system recommends from the ubuntu software repository.
Once that is done, clean up the system and make sure the package manager is stable and in a happy state.

If we are to install a driver from the repo ( a conflict in drivers ??), I need confirmation as to the display manager that kubuntu uses :
> 
LightDM is the default display manager for Ubuntu, Edubuntu, Xubuntu and Mythbuntu since 11.10 release, for Lubuntu since 12.04 release, and for Kubuntu beginning with 12.10.

```

dpkg -l lightdm

``` still valid in 15.04 ? 

-----------------------
It's your time and your effort and your system;
[INDENT][INDENT]your decision as to what to do
[INDENT][INDENT][INDENT][INDENT]we are here to help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

