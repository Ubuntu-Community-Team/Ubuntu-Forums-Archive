---
title: "New nVidia driver ver 173.14.05"
date: 2008-05-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-05-28
> Version: 173.14.05
Operating System: Linux x86
Release Date: May 28, 2008

Release Highlights

    * Added support for the following new GPUs:
          o Quadro FX 3600M
          o GeForce 9800 GX2
          o GeForce 9800 GTX
          o GeForce 9600 GT
          o GeForce 9600 GSO
          o GeForce 9600 GS
          o GeForce 9500M GS
          o GeForce 8400
          o GeForce 8400 GS
    * Added support for Quadro FX 5600/4600 SDI and Quadro G-Sync II.
    * Resolved a bug causing left and right eyes to be reversed in stereo mode on some Quadro FX GPUs.
    * Fixed a problem that caused OpenGL to stop rendering to windows with origins at or beyond 4096 pixels (horizontally) on GeForce 8 and 9 GPUs.
    * Fixed a bug causing some Quadro FX 4500 SDI configurations to take a long time to achieve synchronization.
    * Added preliminary support for X.Org server 1.5.
    * Addressed a problem causing visual corruption when using GeForce 8 GPUs to drive Chi Mei 56" displays.
    * Addressed visual corruption when driving Cintiq 20WSX wide format tables with some GeForce 6 and 7 GPUs.
    * Fixed OpenGL rendering corruption with textures compressed using the DXT5 compression algorithm.
    * Fixed a regression that caused invalid EDIDs to be detected for the internal display device on some notebooks.
    * Improved hotkey switching and power management support on some GeForce 8 notebooks.
    * Fixed a regression causing some GeForce 6100/6150 systems to fail to restore the screen after DPMS cycles.
    * Fixed a bug that prevented the console from being restored correctly in SLI mode on GeForce 6 and 7 GPUs.
    * Fixed interlaced modes on GeForce 8 GPUs.
    * Fixed a problem that caused the synchronization signal polarity to always be positive for DVI devices on GeForce 8 and 9 GPUs.
    * Resolved a problem resulting in X startup to fail on some GeForce 8 and 9 systems without swap space.
    * Fixed a bug resulting in X crashes when using GeForce 8 and 9 GPUs in SLI to drive X screens at depth 8.
    * Fixed a problem that caused TV output on secondary TVs to be black and white on some GPUs.
    * Restored compatibility with recent Linux 2.6 kernels.

32bits
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)

64bits
[http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)


[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

------------------------------

Works OK with Intrepids repo "uptodate" and kernel 2.6.25   :)


"* Added preliminary support for X.Org server 1.5." ,  important
for the future.

RGBA function is still broken during scroll but thats more experimental..

---

### Post by no1wantdthisname on 2008-05-29
Anyone try this:
> 
As was mentioned in the 173.08 beta release, 173.14.05 contains support for an experimental glyph cache on the GeForce 8 and 9 series that may improve anti-aliased font rendering performance. This support can be enabled by running nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1.

In addition, 173.14.05 added a new X config file option, PixmapCacheSize. This option, when combined with the InitialPixmapPlacement and GlyphCache options described above, is designed to improve performance in applications that rapidly allocate and free small pixmaps, such as gtkperf and Mozilla Firefox. Please see the README for details on exactly what this option does and how to use it.

as mentioned in the second post here: [http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

How much faster is it?

---

### Post by plun on 2008-05-30
> **no1wantdthisname said:**
> 
How much faster is it?

Well, the challenge is something to measure with, glxgears is a really
primitive tool.

Phoronix has a new test suite

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

Also a deb package on download page. 

I have been testing a little with the pixmapcache and it feels smoother/faster.

---

### Post by tretle on 2008-06-01
hopefully the new nvidia driver will make it into the repo's soon.

---

### Post by cocopuffz on 2008-06-01
My fonts still look bad... and it still won't allow me to go to 1440x900

Tried a bunch different edits to my xorg.conf file and it makes no difference. Also, if I reboot, the initial display still dumps me into 1024x768. 

At least it "works", but this version hasn't resolved any of the issues I had with the beta drivers.

----

Fixed. I ran gksudo displayconfig-gtk instead of the old dpkg-reconfigure.... and that solved it.

---

### Post by madjr on 2008-06-02
some more info:

[http://news.softpedia.com/news/NVidia-173-14-05-Display-Driver-Brings-Support-for-X-Org-1-5-86771.shtml](http://news.softpedia.com/news/NVidia-173-14-05-Display-Driver-Brings-Support-for-X-Org-1-5-86771.shtml)

---

### Post by plun on 2008-06-02
> **cocopuffz said:**
> My fonts still look bad... and it still won't allow me to go to 1440x900

Fixed. I ran gksudo displayconfig-gtk instead of the old dpkg-reconfigure.... and that solved it.

Just something I've seen

nVidia sets everything as default to "Auto" and it follows gtk settings.

With nvidia-settings this can be changed > X server display configuration > Resolution

nvidia-settings is always installed with a driver directly from nVidia, manual procedure from a repo....should be standard with the glx-new package . IMHO....:)

---

### Post by gblorax on 2008-06-05
I've done some digging and found that this 173.14.05 is likely the "big fix" for the issue I'm having with getting black windows.

Two questions:

1. Typically how long do you usually have to wait before this is something I can download through Synaptic?

2. If I don't wait, I realize there are ways of getting the package anyways - I've seen a few articles but worried if I do something non-standard to get it working, that I may not get future updates the way I'm currently getting them. Is there an easy way to get the driver now? Appreciate any help even if it means pointing me to an existing thread - just haven't found one that tells me how to reverse what their suggesting if anything goes wrong.

---

### Post by plun on 2008-06-05
> **gblorax said:**
> 

1. Typically how long do you usually have to wait before this is something I can download through Synaptic?

2. If I don't wait, I realize there are ways of getting the package anyways - I've seen a few articles but worried if I do something non-standard to get it working, that I may not get future updates the way I'm currently getting them. Is there an easy way to get the driver now? Appreciate any help even if it means pointing me to an existing thread - just haven't found one that tells me how to reverse what their suggesting if anything goes wrong.

1. This is politics and "the software religious" believes that "the 1% sect" can force nVidia to open their driver....just tragic.

Mr Envy seems also to gone "religious".... so this can take time.

2.  My way

> sudo gedit /etc/default/linux-restricted-modules-common

DISABLED_MODULES="nv nvidia_new"

sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed

**Logout > Ctrl-Alt-F1 and switch to a tty and login**

sudo /etc/init.d/gdm stop         or kdm for kubuntu

sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run

Ctrl-Alt-Del for PC restart 



:)

---

### Post by RAOF on 2008-06-05
> **plun said:**
> 1. This is politics and "the software religious" believes that "the 1% sect" can force nVidia to open their driver....just tragic.

Mr Envy seems also to gone "religious".... so this can take time.
...

I'm not sure what you're referring to here?  Are you suggesting that the fact that the latest nvidia driver isn't instantly available in the development repository is due to politics?  Amazingly enough, it isn't.  The new nvidia driver will likely be included in the next linux-restricted-modules release, but the kernel team have other things to do, and releasing a new linux-restricted-modules package *right now*, so the few people crazy enough to run Intrepid at this point can use it immediately, isn't exactly a priority.

For those people not running Intrepid, it is my understanding that Envy-NG is going to be providing updated nvidia drivers.  But the packaging of those drivers takes a non-zero amount of time and effort.  Envy-NG is in the repositories because the author worked with MOTU and members of the kernel & X team to get it into a state where it wouldn't accidentally break someone's Ubuntu install, won't need to be re-run after kernel updates, etc.

To suggest that this work was done to make it more difficult for you to use the nvidia drivers is entirely wrong.  These people have gone to great efforts to make the nvidia drivers *easier* for you to install.

To add something slightly constructive to this rant, this [wiki page](https://help.ubuntu.com/community/NvidiaManual) provides some background and troubleshooting information if you choose to manually install the nvidia driver.

---

### Post by ronacc on 2008-06-06
> **RAOF said:**
> 

To suggest that this work was done to make it more difficult for you to use the nvidia drivers is entirely wrong.  These people have gone to great efforts to make the nvidia drivers *easier* for you to install.

To add something slightly constructive to this rant, this [wiki page](https://help.ubuntu.com/community/NvidiaManual) provides some background and troubleshooting information if you choose to manually install the nvidia driver.

try to understand that those of us who have been castigated many times and called "unUbuntu" for daring to self install the nvidia drivers might have a tendency to see it as a crusade for "Idealogical Purity " or "Software Religion"  and to be a bit paranoid when things like this occur (bug# 190090) .

---

### Post by RAOF on 2008-06-06
Ah, OK.  Plun seemed to be talking about "software freedom" politics, you're talking about the Ubuntu systems for making it easy to install the nvidia driver interfering with a manually installed nvidia driver (incidentally, I don't see anything but professionalism from Martin Pitt in that bug).

I think this may be an unavoidable tradeoff; we don't try to make it difficult to install the driver manually, and we provide mechanisms to disable the automatic systems - have you read the wiki page I linked in the last post?  I've had no problems with self-installed nvidia drivers following those instructions.  That said, I would almost never *recommend* self-installing the drivers; almost all the time it's unnecessary effort.

---

### Post by ronacc on 2008-06-06
my comment was not about the way the bug was handeled it was about the fact that the bug occured in the first place . I understand that Ubuntu is trying to make it easy for the non technicaly inclined to use and I appluad that , but there is a difference between "making it easy" and "our way or the Highway" and sometimes that line atleast appears to be crossed. and no one recommended that I install the driver myself the decission was entirely my own and I gladly accept the consequences .

---

### Post by hvymtlsteve on 2008-06-06
> **plun said:**
> 
2.  My way
:)

Thanks for posting that! 
For some reason it didn't quite work the first time I did it, but the second time around, I went ahead and switched to su instead of sudo to run the installer script, and it worked like a charm!

---

### Post by 23meg on 2008-06-06
> **RAOF said:**
> 
To suggest that this work was done to make it more difficult for you to use the nvidia drivers is entirely wrong.  These people have gone to great efforts to make the nvidia drivers *easier* for you to install.


It's not just wrong; in plun's case it's pure trolling and mudslinging. He has been pointed to facts on this matter many times, yet keeps fueling the same FUD. Just use the ignore list / report button; replying is useless. He'll just keep twisting what you have (or even haven't) said to help his own case, and then call you a hypocrite.

---

### Post by KimH on 2008-06-06
> **plun said:**
> 

2.  My way



:)

Thank you so much for this guide :KS It worked great on my Dell XPS M1330 with Hardy. Now I can switch between the laptop monitor and my external monitor using Fn+F8 like I could i Gutsy.

:guitar:

/Kim

---

### Post by tseliot on 2008-06-06
> **plun said:**
> 1. This is politics and "the software religious" believes that "the 1% sect" can force nVidia to open their driver....just tragic.

Mr Envy seems also to gone "religious".... so this can take time.

I really don't know what you're talking about.

I've been working on some new projects for Ubuntu therefore I haven't had the time to test this driver properly.

You will see this driver soon through EnvyNG for Hardy.

As regards Intrepid, I am the new maintainer of the nvidia driver in Ubuntu together with Timo Aaltonen. We're working on a new package since the linux-restricted-modules will no longer exist. This is why the new driver is not yet available in Intrepid.

In other words, no, it's not politics.

---

### Post by Cuppa-Chino on 2008-06-06
> **plun said:**
> 

2.  My way



:)

no dice when ever my computer starts up it finds Nvidia drivers on first boot but then goes into "low graphics mode" tx1000 hewlett packard, cannot get even get back to a nv driver now... 

anybody else had the one boot issue?

---

### Post by ronacc on 2008-06-06
I can't say for sure from the info you give but it sounds like after you boot something is changing the driver for the next boot . I ran into a spurt of this during Hardy devlopement and cured it by removing jockey and jockey-gtk , are you fully updated ? in my release version of Hardy I do not find it necessary to remove those files to run the Nvidia driver (173.14.05 ) . Is your /etc/x11/xorg.conf file being altered ? you can check that by , when you see the low graphics warning don't click anything , kill it with ctrl+alt+bkspc and take a look at your xorg.conf with your favorite command line editor  .

---

### Post by Gina on 2008-06-09
Just built an AMD Athlon 64 X2 system which has NVidia graphics on the mobo.  As installed the Ubuntu display was twice as high and three quarters the width of the screen :eek: but on installing the NVidia propriatary driver all was well.  Even the desktop effects work :)

---

### Post by LibertyShadow on 2008-06-11
> **Cuppa-Chino said:**
> no dice when ever my computer starts up it finds Nvidia drivers on first boot but then goes into "low graphics mode" tx1000 hewlett packard, cannot get even get back to a nv driver now... 

anybody else had the one boot issue?

For a complete tutorial see plun's post for Intrepid:
[http://ubuntuforums.org/showpost.php?p=5259741&postcount=42](http://ubuntuforums.org/showpost.php?p=5259741&postcount=42)

---

### Post by darco on 2008-06-11
> **plun said:**
> 32bits
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)

64bits
[http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)


[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

------------------------------

Works OK with Intrepids repo "uptodate" and kernel 2.6.25   :)


"* Added preliminary support for X.Org server 1.5." ,  important
for the future.

RGBA function is still broken during scroll but thats more experimental..

Am I missing something, no support for the 8800GT?

darco

---

### Post by Unix_Slayer on 2008-06-11
> **cocopuffz said:**
> My fonts still look bad... and it still won't allow me to go to 1440x900

Tried a bunch different edits to my xorg.conf file and it makes no difference. Also, if I reboot, the initial display still dumps me into 1024x768. 

At least it "works", but this version hasn't resolved any of the issues I had with the beta drivers.

----

Fixed. I ran gksudo displayconfig-gtk instead of the old dpkg-reconfigure.... and that solved it.

**Works fine for me.**

[IMG]http://mysite.verizon.net/mgm_mgm/realnv.jpg[/IMG]
[IMG]http://mysite.verizon.net/mgm_mgm/nv1.jpg[/IMG]

---

### Post by Majin_Buu on 2008-06-15
Your tutorial worked when I used the same kernel as you wrote, but when I upgraded, nvidia started to complain.

```
sudo /etc/init.d/kdm stop
sudo nvidia-setup -K --kernel-name=2.6.24-19-generic
```

```
ERROR: Unable to find the kernel source tree for the currently running kernel. 
Please make sure you have installed the kernel source files for your 
Kernel and that they are properly configured; on Red Hat Linux systems, 
For example, be sure you have the 'kernel-source' or 'kernel-devel' RPM 
Installed. If you know the correct kernel source files are installed, 
You may specify the kernel source path with the '--kernel-source-path' 
Command line option
```

Right after you agree to nvidia tos etc, the installer tells me something about "wrong kernel found, might fix it if you use kernel source" something like that (im currently at work).

But how is that possible if I followed the tutorial step by step?

The kernel was upgraded through apt, did I miss something here? Kernel-source?

---

### Post by diehardcc on 2008-06-16
I found this thread by searching and so far this is the most relevant topic, but in the wrong section (Intrepid).

I'm new to Ubuntu 8.04 and I would like to update my NVIDIA graphic drivers (169.12) to the latest. I'm using "Nvidia binary X.Org driver ('new' driver)" from the "Add/Remove Applications" and I don't think its automatically updating from "System > Administration > Update Manager"???

If it does update, then when are they ever going to push the new NVIDIA drivers through the "Update Manager"? If no, then where do I go to request or remind them to do it?

[B]By the way, I'm not comfortable using "sudo apt-get install" terminal commands. I find using "Add/Remove Applications" and "Update Manager" the ultimately the best features for newcomers like me. And, I hope the Ubuntu team sees that it is vital to upkeep it.

When I saw the post of commands from "LibertyShadow", I feel like shooting myself. Why can we just make a single-simple way using the GUI to install/uninstall applications (exe, install wizard script)? :([/B]

---

### Post by RAOF on 2008-06-16
> **diehardcc said:**
> ...
If it does update, then when are they ever going to push the new NVIDIA drivers through the "Update Manager"? If no, then where do I go to request or remind them to do it?
...

The driver you have installed will (almost certainly) not get updated through the "Update Manager".  Hardy has been released, and this means that (ideally) nothing should change in Hardy - the general exceptions are where leaving things unchanged is worse than the risk involved in updating them (security flaws, data corruption bugs, etc).

However, for Hardy you can install the 'envy-ng' tool, which *will* have updated nVidia drivers, although I'm not sure whether the new drivers are available through it just yet.

---

### Post by plun on 2008-06-16
> **RAOF said:**
> The driver you have installed will (almost certainly) not get updated through the "Update Manager".  Hardy has been released, and this means that (ideally) nothing should change in Hardy - the general exceptions are where leaving things unchanged is worse than the risk involved in updating them (security flaws, data corruption bugs, etc).

However, for Hardy you can install the 'envy-ng' tool, which *will* have updated nVidia drivers, although I'm not sure whether the new drivers are available through it just yet.

Well, leave all 9XXX GPU users with no driver just hurts GNU/Linux.:(
(the "crazy nerd" debate)


The driver is available for Hardy but in Hardy Proposed.

[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

Launchpad bug and test report, also approved  
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/239115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/239115)

**Martin P :Accepted into -proposed, please test and give feedback here**

But now this is a Intrepid forum and for Intrepid its a manual procedure for the moment (also a patch for the 2.6.26 kernel)  ((I havent tested 169.12 for Intrepid)

:)

---

### Post by gblorax on 2008-06-16
> **tseliot said:**
> 

You will see this driver soon through EnvyNG for Hardy.

In other words, no, it's not politics.

Hi TSEliot - as the person's who's post unintentionally sparked this debate, I just wanted to chime in and say thanks for the work on EnvyNG. I look forward to the release of this driver version, when you have time of course.

---

### Post by sistoviejo on 2008-06-17
The driver is already on the pre-release repositories. 

I have a Nvidia 6150 GO and it solved a big issue I had which made the text-mode console unreadable and made the screen not work very well when coming back from sleep mode. This bug fix is actually listed in the driver's release notes.

It works well with kernel 2.6.24-18-generic but I think it should work with whichever kernel you have.

To install it you need to enable pre-release updates from the software sources.

Then you need to install nvidia-glx-new-envy and nvidia-new-kernel-source-envy 
Do not install any other packages or run any other updates while you have the pre-release repositories enabled unless you know what you're doing.
If it asks you to install linux-headers, make sure you install the same version as the kernel you're running. 
Be sure to disable pre-release updates from the software sources after you're done.
I think you have to restart the computer at this point.

Please keep in mind that though this worked for me it might not work for you. Do it at your own risk or wait for the update to hit the stable repositories.

---

### Post by LibertyShadow on 2008-06-23
> **diehardcc said:**
> [B]
When I saw the post of commands from "LibertyShadow", I feel like shooting myself. Why can we just make a single-simple way using the GUI to install/uninstall applications (exe, install wizard script)? :([/B]

Yes, this particular method is *definitely* for the zealous users who want the *latest* binary blobs from Nvidia. I said in the post that I recommend using the drivers in the repository because they are officially supported and thoroughly tested.   For most Nvidia cards, you can simply open System>Administration>Hardware Drivers to enable the restricted drivers.

Majin_Buu:
> 
Right after you agree to nvidia tos etc, the installer tells me something about "wrong kernel found, might fix it if you use kernel source" something like that (im currently at work).

But how is that possible if I followed the tutorial step by step?

The kernel was upgraded through apt, did I miss something here? Kernel-source? 

I believe that you updated the linux-source-2.6.24 package, but did not extract the files.  If you have not yet fixed this problem, boot into 2.6.24-18-generic kernel and run these steps:
```

sudo apt-get update
sudo apt-get install linux-source-2.6.24
cd /usr/src
sudo rm -rf ./linux-source-2.6.24/
sudo tar xvjf ./linux-source-2.6.24.tar.bz2

```

You do not need to stop the Xserver before recompiling the kernel module.  I just fixed that in my post above.

Run this in a terminal before restarting after a kernel update:
```

sudo nvidia-setup -K --kernel-name=<*kernelname*>

```
where <*kernelname*> is replaced by the new kernel name as seen in the command:
```

ls /lib/modules/

```

Please let me know how that goes.

---

### Post by plun on 2008-06-23
> **LibertyShadow said:**
> 
Please let me know how that goes.

Well, Intrepid is on the 2.6.26 kernel and this is the thread for that.

[http://ubuntuforums.org/showthread.php?t=833633](http://ubuntuforums.org/showthread.php?t=833633)


Hardys challenge with nVidias driver with **Hardy Proposed** and
EnvyNG which is updated

[http://ubuntuforums.org/showthread.php?t=836541](http://ubuntuforums.org/showthread.php?t=836541)

Albertos Launchpad thread about this.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/239115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/239115)

And from his  blog
[http://albertomilone.com/wordpress/?p=210](http://albertomilone.com/wordpress/?p=210)


EDIT
EnvyNG seems to have been moved this morning to Hardy updates so no need for
Hardys proposed repo.

---

### Post by Nullack on 2008-06-23
Though Envy doesnt have the new .09 version as of yet. I dont like how Envy tries to load the NV module twice - I guess no biggie but it messes my logs :)

---

### Post by plun on 2008-06-23
> **Nullack said:**
> Though Envy doesnt have the new .09 version as of yet. I dont like how Envy tries to load the NV module twice - I guess no biggie but it messes my logs :)

Well, this is more about finding a solution which fits the majority of
users.

If nvidia-glx-new will be frozen to version 169.12 for this LTS, Envy is the solution.  (bad solution IMHO when nVidia and all PC manufacturer now ships 9XXX GPUs and nVidia beats sales records every quarter :-\")

---

### Post by Unix_Slayer on 2008-06-23
Version: 173.14.09
Operating System: Linux x86
Release Date: June 11, 2008

Release Highlights

    * Fixed aliased font rendering corruption on X.Org server 1.5.
    * Fixed a display corruption problem driving two dual-link DFPs with Quadro FX 1700 GPUs.
    * Fixed a regression that prevented the X driver from starting on some GeForce FX, 6 and 7 mobile GPUs.
    * Fixed a locale-interaction issue in the nvidia-settings X server configuration file parser.
    * Added preliminary support for Linux 2.6.26.

---

### Post by LibertyShadow on 2008-06-24
This is a method to automatically update manually installed nvidia drivers after a kernel update: [http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by Gina on 2008-06-25
> **LibertyShadow said:**
> This is a method to automatically update manually installed nvidia drivers after a kernel update: [http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")I'm hoping to have time to have a look at that today - I'll need to install the new nVidia driver to test Intrepid properly - can't be doing with ultra low res!

---

### Post by plun on 2008-06-25
> **Gina said:**
> I'm hoping to have time to have a look at that today - I'll need to install the new nVidia driver to test Intrepid properly - can't be doing with ultra low res!

Well....

"Bless this mess" :)

For Intrepid you must use Amaranths patch

[http://ubuntuforums.org/showthread.php?t=833633](http://ubuntuforums.org/showthread.php?t=833633)

and my little finding later about lrm-video


Xorg was updated today with tons with fixes and I just reinstalled
the patched driver without any issues.

Excellent performance for the moment and everything works.

---

### Post by Gina on 2008-06-25
Thank you for that :)  I've run Amaranth's patch without error and tried running the nVidia install from command line.  However, I always get an error saying I have X running.  I've tried all I can find - in the nVidia README and in these forums etc. to be in runlevel 3 (as recommended by nVidia) but still get the error.

I'm probably missing some little something... any suggestions please?

---

### Post by sistoviejo on 2008-06-25
> **plun said:**
> Well....

"Bless this mess" :)

For Intrepid you must use Amaranths patch

[http://ubuntuforums.org/showthread.php?t=833633](http://ubuntuforums.org/showthread.php?t=833633)

and my little finding later about lrm-video


Xorg was updated today with tons with fixes and I just reinstalled
the patched driver without any issues.

Excellent performance for the moment and everything works.

Are you using Intrepid already?

---

### Post by ronacc on 2008-06-25
of course , this is the intrepid testing forum .

---

### Post by xebian on 2008-06-25
> **Gina said:**
> Thank you for that :)  I've run Amaranth's patch without error and tried running the nVidia install from command line.  However, I always get an error saying I have X running.  I've tried all I can find - in the nVidia README and in these forums etc. to be in runlevel 3 (as recommended by nVidia) but still get the error.

I'm probably missing some little something... any suggestions please?

You need to stop gdm. Open a tty session -  CTL+ALT+fn
At the terminal, sudo /etc/init.d/gdm stop

---

### Post by plun on 2008-06-25
> **Gina said:**
> 
I'm probably missing some little something... any suggestions please?

Well, this is a "mess" as I wrote....:)

First of all it might be a good idea
to read how nVidia describes it

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Debian/Ubuntu just scroll down a bit.



In practical Ubuntu way
```

sudo gedit /etc/default/linux-restricted-modules-common

DISABLED_MODULES="nv nvidia_new"


sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed


EXTRA beacuse of Intrepids lrm-video, comment out 

sudo gedit /etc/modprobe.d/lrm-video

#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS


---------------------
---------------------

Logout > Ctrl-Alt-F1 and **switch to a tty** and login

sudo /etc/init.d/gdm stop 


*Patched driver is used below*

sudo sh NVIDIA-Linux-x86-173.14.09-pkg1-custom.run

Ctrl-Alt-Del for PC restart
or
sudo /etc/init.d/gdm start  
```



Every time the kernel or Xorg is upgraded commands below the line
must be done for reinstalling nVidias driver.

---

### Post by Gina on 2008-06-25
Thank you for that :)  Unfortunately I've done all that and got the confirmation the GDM had been stopped but I still get the error that I'm running an X server after running the custom nVidia driver installation.

---

### Post by plun on 2008-06-25
> **Gina said:**
> Thank you for that :)  Unfortunately I've done all that and got the confirmation the GDM had been stopped but I still get the error that I'm running an X server after running the custom nVidia driver installation.

Are you using KDM  (kubuntus gdm)  ?

sudo /etc/init.d/kdm stop 


gdm stop or kdm stop just kills X

Strange...:confused:

---

### Post by xebian on 2008-06-25
> **Gina said:**
> Thank you for that :)  Unfortunately I've done all that and got the confirmation the GDM had been stopped but I still get the error that I'm running an X server after running the custom nVidia driver installation.

Reboot to recovery mode, and then select "drop to root shell".  Just to be sure stop gdm or kdm.  Then you can do your install.

---

### Post by Gina on 2008-06-25
Yes, I've tried that (I think).  I'll try it again in case that's a combination I missed.

I'm using GDM with 64 bit version - I'm thinking of trying it with the 32 bit version in case there's any difference.

---

### Post by ronacc on 2008-06-25
when you kill kdm (or gdm) and open the term try hitting ctrl+alt+bkspc . I'm gdm and 64bit here and the patched driver installed fine for me . I did need to comment out lrm-video to get it to run though .

---

### Post by Gina on 2008-06-25
Tried recovery mode and dropped to root shell then stopped GDM and continued as before.  This time things proceeded much better.  Got a couple of warnings and it asked to compile a kernel module which I let it do.  Ended up saying it had been successful.  Rebooted and still got low res screen so tried running nVidia's config utility.  That came up with an error that the nVidia driver wasn't installed.  Rebooted again - got the low res warning - ran the setup and chose driver for my graphics series.  I can now get 800x600 res! - which I guess is a slight improvement on the 640x480 I was getting.

Yes, I commented out the lines for installing lrm-video - new, normal and legacy versions of the driver.

I did use ctrl-alt-bkspc to restart X.

So... a bit further along the road but still not getting a working nVidia driver.

---

### Post by ronacc on 2008-06-25
have you checked your xorg.conf , if you have ever let it go all the way to desktop in low graphics mode it has trashed your xorg.conf , the best bet is to after installing the driver but before starting gdm take a look at your xorg.conf and make sure it is calling the nvidia driver  or just copy over a known good xorg.conf .

---

### Post by Raptor45 on 2008-06-25
> **Gina said:**
> I'm hoping to have time to have a look at that today - I'll need to install the new nVidia driver to test Intrepid properly - can't be doing with ultra low res!

Just as a point of information, you don't need the nvidia driver to run hi res. While waiting for the nvidia driver to be sorted out, I am using nv at 1680x1050. Granted this does not give 3D support, but for testing a release as early as this thats not something I'm concerned with.

> have you checked your xorg.conf , if you have ever let it go all the way to desktop in low graphics mode it has trashed your xorg.conf , the best bet is to after installing the driver but before starting gdm take a look at your xorg.conf and make sure it is calling the nvidia driver or just copy over a known good xorg.conf .

This is definitely true; the low-graphics mode is more of a hindrance than a help. You are much better off just manually editing xorg.conf to change the driver if nvidia breaks. For example, when the nvidia driver failed I switched to nv with the tool, but it messed up the resolution so I could only do low res as you say. After restoring the original xorg.conf and simply changing to nv manually everything works fine. Of course you can go back and add in the resolutions to xorg.conf, but thats a bit of a pain.

---

### Post by ronacc on 2008-06-25
I keep several copies of a known good xorg.conf handy .

---

### Post by plun on 2008-06-26
> **ronacc said:**
> I keep several copies of a known good xorg.conf handy .

Yup, so do I....

Another option is to use a "blank" xorg.conf before starting nVidias setup.

```
sudo gedit /etc/X11/xorg.conf

or within the tty

sudo nano /etc/X11/xorg.conf 
```


And to permit nVidias setup to write to xorg.conf, last sequence in setup (just answer Yes)

---

### Post by Gina on 2008-06-26
I haven't looked at the xorg.conf yet but it did ask to create a new one and I said yes.  I have a good working xorg.conf for Hardy (with proposed updates) which uses an nVidia graphics driver and happily runs my monitor at it's native res of 1280x1024.

I'll probably be having another go at it later today.

---

### Post by plun on 2008-06-26
> **Gina said:**
> I haven't looked at the xorg.conf yet but it did ask to create a new one and I said yes.  


Ok.. the challenge is that nVidia just writes within existing xorg.conf

If its a mess as also ronacc wrote nvidias driver fails to load.

This is mine for the moment


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Tue Jun 10 17:14:15 PDT 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Nevertheless you are learning the tty and its really useful if you
are running a server without a GUI...

Also remember !

The terminal stores old commands, arrow up/down on keyboard

Search for old commands with   **Ctrl-R**


Dont use too much time on the nVidia challenge... :)

---

### Post by Nullack on 2008-06-26
Yeah its an annoyance for sure. Most of the entries nvidias driver puts into the conf just spams the conf up and makes it confusing. e.g. Those modules are auto loaded by x by default anyway.

---

### Post by ronacc on 2008-06-26
your hardy xorg.conf will work just fine I've been using the same one since fiesty :) box hasn't changed monitor hasn't changed xorg.conf hasn't changed ! and you might want to install MC (midnight commander) before you start, its an MSDOS style filemanager that uses the arrow keys and function keys to navigate and runs from term , makes it easier to navigate around from term.

---

### Post by Gina on 2008-06-26
Done it! It's working! :):)

Used my Hardy xorg.conf - had a duff run where it complained of wromg kernel module so I re-ran the driver installation and apart from the odd warning, that worked and I was able to run the nvidia-xconfig to change the resolution to 1280x1024.  However, in spite of opting to save the configuration to xorg.conf, it didn't hold the res after a reboot.  I used the System > Preferences > Screen resolution to set it again and it then held res after reboot :)  I'm posting this from my AMD64 running Intrepid 64 bit version with full native screen resolution.

I'll list my steps (as far as I can remember) in case it helps others :-
[LIST]
[*]Boot into recovery mode and drop into root shell.
[*]Run **sudo /etc/init.d/gdm stop** to stop Gnome Desktop Manager and X Server
[*]Change to dir containing the custom nVidia install script as patched by Amaranth's patch
[*]Run **sh NVIDIA-Linux-x86_64-173.14.09-pkg2-custom.run** to install the driver
[*]At the prompt, let it compile kernel module
[*]Run **nvidia-xconfig** and let it replace xorg.conf
[*]Reboot normally
[*]Screen resolution wrong - so run **Applications > System Tools > NVIDIA X Server Settings** to set screen res and use **save to xorg.conf** option.
[*]Reboot normally
[*]Screen res wrong so use **System > Preferences > Screen Resolution** to set it
[*]Reboot - all working fine - correct screen resolution :)
[/LIST]

To plun...  Yes, I getting well used to command line now :lolflag: And yes, use the up/down to access the history :)

P.S. .... New xorg.conf :-
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (gina@amd64-dev)  Wed Jun 25 21:38:35 BST 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Gina on 2008-06-26
I would like to say a big THANK YOU to everyone who has helped with this :):)

Now for other problems (like lack of sound)...  Well, maybe not today :lolflag:

---

### Post by ronacc on 2008-06-26
try switching to alsa for sound , that worked for me , system>prefs>sound , with some apps you also need to switch in that apps prefs also.

---

### Post by Gina on 2008-06-26
> **ronacc said:**
> try switching to alsa for sound , that worked for me , system>prefs>sound , with some apps you also need to switch in that apps prefs also.Yup!  That was it :)  Thank you :)

---

### Post by psyke83 on 2008-06-26
> **ronacc said:**
> try switching to alsa for sound , that worked for me , system>prefs>sound , with some apps you also need to switch in that apps prefs also.

That's not a proper fix, it will merely bypass PulseAudio (and system sounds still won't work). I'd say the problem is that PulseAudio considers the pcsp (pc speaker) kernel module as a separate sound card and selected it as the default device. 

There are two solutions:
1. Blacklist the pc speaker kernel module: [http://ubuntuforums.org/showpost.php?p=5225071#postcount=12](http://ubuntuforums.org/showpost.php?p=5225071#postcount=12)
2. Configure PulseAudio to use the right ALSA sink: [http://ubuntuforums.org/showpost.php?p=5216747&postcount=3](http://ubuntuforums.org/showpost.php?p=5216747&postcount=3)

Either solution will work fine, and it's probably going to be fixed officially in the future.

---

### Post by ronacc on 2008-06-26
> **psyke83 said:**
> That's not a proper fix, it will merely bypass PulseAudio (and system sounds still won't work). I'd say the problem is that PulseAudio considers the pcsp (pc speaker) kernel module as a separate sound card and selected it as the default device. 

There are two solutions:
1. Blacklist the pc speaker kernel module: [http://ubuntuforums.org/showpost.php?p=5225071#postcount=12](http://ubuntuforums.org/showpost.php?p=5225071#postcount=12)
2. Configure PulseAudio to use the right ALSA sink: [http://ubuntuforums.org/showpost.php?p=5216747&postcount=3](http://ubuntuforums.org/showpost.php?p=5216747&postcount=3)

Either solution will work fine, and it's probably going to be fixed officially in the future.

tried your solution that works also, thanks , just a note though the "proper fix" is that which makes my box work.

---

### Post by Raptor45 on 2008-06-27
> **ronacc said:**
> tried your solution that works also, thanks , just a note though the "proper fix" is that which makes my box work.

In a testing version, at least in my opinion, the idea of a "proper fix" is a little different. I don't try to do hacks and whatever else might be necessary to make something work. You aren't testing to find out what hacks and such work (not to mention hacks may break other unrelated things). Instead you're testing to find and track what bugs occur in a normal installation. The testing version isn't really meant for day to day use anyway, especially this early.

For example in this case, bypassing PulseAudio, what if a problem occurs further down the line, and you don't know to report it? Or when installing nvidia drivers manually, what if they cause compatibility issues once the real ones are released?

On a normal release I'll do whatever it takes to get everything working. When testing, I try to follow the "Ubuntu"/"Debian" ideology and keep everything as close to "stock" as possible; even if that means living with a little breakage for a while. I want to know my bugs are a real problem Ubuntu, not a result of some patch or hack I applied.

But that's only my testing philosophy, to each their own.

---

### Post by Gina on 2008-06-27
> **Raptor45 said:**
> In a testing version, at least in my opinion, the idea of a "proper fix" is a little different. I don't try to do hacks and whatever else might be necessary to make something work. You aren't testing to find out what hacks and such work (not to mention hacks may break other unrelated things). Instead you're testing to find and track what bugs occur in a normal installation. The testing version isn't really meant for day to day use anyway, especially this early.

For example in this case, bypassing PulseAudio, what if a problem occurs further down the line, and you don't know to report it? Or when installing nvidia drivers manually, what if they cause compatibility issues once the real ones are released?

On a normal release I'll do whatever it takes to get everything working. When testing, I try to follow the "Ubuntu"/"Debian" ideology and keep everything as close to "stock" as possible; even if that means living with a little breakage for a while. I want to know my bugs are a real problem Ubuntu, not a result of some patch or hack I applied.

But that's only my testing philosophy, to each their own.I agree with that.  I realise the manual installation of the nVidia driver is just an interim measure until - once the Ubuntu standard installation is available I expect to reinstall Intrepid and test that.  I expect to reinstall several times during the development to be sure of removing hacks and other fiddling to return to a standard system for testing.

PulseAudio is different and will need to be enabled for testing.  Personally, I may turn it off if I want to listen to music while testing other things.  I should think PulseAudio will be one of the earlier things worked on since ATM it's definitely broken.  It is also a problem in Hardy and for my general use a work-around is needed for the moment.

---

### Post by ronacc on 2008-06-27
@raptor45 yes I agree with that , if you note I said I tried the fix psyke83 and found it worked , I am continuing to use it but in a way it is a bit of a hack also in that to get sound that way you must add an app (padevchooser) that is not installed by default and further ,though not in my case, blacklist your pc speaker. With the Nvidia driver I start out with and occasionaly revert to the "ubuntu way" but will only put up with a screwed display for a limited amount of time . during the testing phase I refrain from any major hacks.

---

### Post by plun on 2008-06-27
> **ronacc said:**
> @raptor45 yes I agree with that , if you note I said I tried the fix psyke83 and found it worked , I am continuing to use it but in a way it is a bit of a hack also in that to get sound that way you must add an app (padevchooser) that is not installed by default and further ,though not in my case, blacklist your pc speaker. With the Nvidia driver I start out with and occasionaly revert to the "ubuntu way" but will only put up with a screwed display for a limited amount of time . during the testing phase I refrain from any major hacks.

Well, I cannot define this as a hack, its bugs and left out functionality

During Hardys development we wanted a Blueprint for PulseAudio but everything was a hidden agenda about howto integrate PA.

This is the real Pulseaudio.

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

psyke83 has tried to fix this mess within his howto.
It works great with Intrepid (relevant parts)


All pulseaudio packages can easily be seen within Ubuntus package database


But...  as seen within psyche83 thread some users has severe trouble to **read and follow** a manual...so thats maybe the biggest challenge. Maybe a MS disease or a Messenger,  maybe also a IRC:) about reading more then one sentence.


It can take weeks-months until upstream fixes some bugs...:)

---

### Post by ronacc on 2008-06-27
I quess I should have said workaround , I tend to use "hack" in the sense of altering the default configuration to make up for errors or omisions , probably a bad choice of words on my part but I hail from a time when hack did not have the negative implications it has today .

---

### Post by Gina on 2008-06-27
A bit off topic (nothing to do with nVidia)... but I now have Audacity able to record from Line input in Intrepid - won't work in Hardy on the AMD64 though it does on the P4 - strange.

---

### Post by Totzo on 2008-06-29
I just tried to install the 173.14.09 driver on a 2.6.26-2-generic kernel and the installer complained about it being a xen kernel! Anyone else had this problem? Fix anyone?

edit: I think I've found the solution (doh! should have searched first)

[http://ubuntuforums.org/showthread.php?t=833633&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=833633&highlight=nvidia)

---

