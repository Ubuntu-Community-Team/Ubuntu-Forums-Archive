---
title: "X-server breakage"
date: 2008-12-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-12-15
A little warning until this is clarified.....

> The following packages will be REMOVED:
  nvidia-glx-180 xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom
The following packages will be upgraded:
  console-setup libdjvulibre-text libdjvulibre21 manpages ttf-liberation
  ttf-sazanami-mincho ubuntu-minimal ubuntu-standard unattended-upgrades
  xserver-common xserver-xorg-dev
11 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
Need to get 7583kB of archives.
After this operation, 34.3MB disk space will be freed.
Do you want to continue [Y/n]? 


[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/thread.html)

This will also probably break the nVidia driver.:confused:

Even if the ABI check is removed there will probably be no composite..


So I wait.......):P

---

### Post by ronacc on 2008-12-15
thanks for the warning . I think I'll hold off awhile too .

---

### Post by Starks on 2008-12-15
I don't understand why DRI and compositing are so ridiculously broken on both stable repos and unstable ppa repos...

---

### Post by plun on 2008-12-15
> **ronacc said:**
> thanks for the warning . I think I'll hold off awhile too .


OK :cool:

I also read this post which also includes log files

[http://ubuntuforums.org/showpost.php?p=6358105&postcount=15](http://ubuntuforums.org/showpost.php?p=6358105&postcount=15)

---

### Post by autocrosser on 2008-12-15
I saw the updates this morning & as it wanted to remove the 180 driver I thought: Well, I'll just revert back to the 177 driver & that "should" fix it.....In short, it wants to remove the 177 also--So I wait too....

---

### Post by phenest on 2008-12-15
Dammit! I wish I saw this thread earlier. I did the upgrades and nVidia broke. But I am able to use the nv driver, but compositing with Metacity is a joke.

I do have a usable system, so I'll lump it for now.

---

### Post by Gina on 2008-12-15
Have you tried reinstalling the 180 driver from Synaptic or CLI?

---

### Post by plun on 2008-12-15
> **autocrosser said:**
> I saw the updates this morning & as it wanted to remove the 180 driver I thought: Well, I'll just revert back to the 177 driver & that "should" fix it.....In short, it wants to remove the 177 also--So I wait too....

Yup... the challenge is that Xserver 1.6 brakes nVidias ABI check.

You can start the driver with the noABI check option but glx is probably broken without patches and that is in the "highest division".

I hope someone will clarify this situation...  Xserver can also be set on "hold"...

---

### Post by damis648 on 2008-12-15
Wait, could this have anything to do with my xorg eating up to 30% CPU? Because it just started doing that two days ago, see my thread:
[http://ubuntuforums.org/showthread.php?t=1011048](http://ubuntuforums.org/showthread.php?t=1011048)
also, I (used to until 180.06) get ```
AUDIT: Sun Dec 14 17:55:47 2008: 7228 X: client 4 rejected from local host ( uid=0 gid=0 pid=7598 )
AUDIT: Sun Dec 14 17:55:52 2008: 7228 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7633 )
AUDIT: Sun Dec 14 17:55:52 2008: 7228 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7634 )
AUDIT: Sun Dec 14 17:55:52 2008: 7228 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7635 )

```
at Xorg.0.log upon boot.AUDIT: Sun Dec 14 17:55:47 2008: 7228 X: client 4 rejected from local host ( uid=0 gid=0 pid=7598 )
AUDIT: Sun Dec 14 17:55:52 2008: 7228 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7633 )
AUDIT: Sun Dec 14 17:55:52 2008: 7228 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7634 )
AUDIT: Sun Dec 14 17:55:52 2008: 7228 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7635 )

---

### Post by chrismine on 2008-12-15
> **plun said:**
> A little warning until this is clarified.....



[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/thread.html)

This will also probably break the nVidia driver.:confused:

Even if the ABI check is removed there will probably be no composite..


So I wait.......):P
I took the plunge...

I will be waiting for awhile...

Except if somebody has got a workaround?

---

### Post by phenest on 2008-12-15
> **chrismine said:**
> I took the plunge...

I will be waiting for awhile...

Except if somebody has got a workaround?

Use the nv driver.

---

### Post by gmspromo on 2008-12-15
Sorry if this is a newbie question, but how do you change it to use the nv driver exactly?
I'm not that new at all to Ubuntu, but looking in /etc/X11/xorg.conf there is no configuration setting to set the driver to nv. I know there SHOULD be but has it moved to another file?

I upgraded Jaunty this morning and only then when I found X was broken on my laptop did I find this discussion on another computer!!! I've got X back but it's 800x600 using the generic driver. I basically did an "apt-get install xserver-xorg" which brought xorg back and then did "dpkg-reconfigure -phigh xserver-xorg" which get me back to a working xconfig .... just in low res!!

I even went to "hardware drivers" and the option was there to install and enable nvidia-173 which I tried just for the hell of it ... that broke it again and I had to go through the whole process above again just to get back to a low-res config.

Help!!

---

### Post by chrismine on 2008-12-15
Thanks I wish I could - I did like I usually do - first the normal upgrade and there was a partial upgrade which I did. As far as I remember nothing important were to be removed. Lots of new Xorg stuff installed.
Rebooted and got low graphics mode with option which ask to restore default xorg which I did. Ask to reboot and when splash screen finished loading just a black screen.

I when to recovery mode - no xfix option, dpkg-reconfigure xserver-xorg not working.

Seems to be a problem with xorg packages.

Will do apt-get update from the command line for awhile...

Waiting for Intrepid CD from Canonical and will reinstall if not fixed by then.

---

### Post by phenest on 2008-12-15
> **gmspromo said:**
> Sorry if this is a newbie question, but how do you change it to use the nv driver exactly?
I'm not that new at all to Ubuntu, but looking in /etc/X11/xorg.conf there is no configuration setting to set the driver to nv. I know there SHOULD be but has it moved to another file?

Open the xorg.conf file and put nv where it says nvidia for the driver and comment out everything else. Then reboot.

---

### Post by plun on 2008-12-15
I am trying to lock all xserver packages with no luck...:---)

Can someone else check ?   Bug in Synaptic ?

[[img]http://ubuntu-pics.de/thumb/7233/screenshot_synaptic_package_manager_16Cbc3.png[/img]](http://ubuntu-pics.de/bild/7233/screenshot_synaptic_package_manager_16Cbc3.png)

Lock is OK but they still wants to be upgraded...


----------------------
Some facts about nvidia and ABI

[http://www.nvnews.net/vbulletin/showthread.php?t=111516](http://www.nvnews.net/vbulletin/showthread.php?t=111516)

.

---

### Post by xebian on 2008-12-15
Just ignore ABI and it's ok.  I have GeForce6150 180.16 working nicely here.

---

### Post by DougieFresh4U on 2008-12-15
I ignored updates all day today. I just checked again, and it said 90 updates and 30 to remove on the 'dist-upgrade'.
So went ahead and did just the 'upgrade' and it only removed 9 packages, no xorg stuff and updated 48 packages. All the 'xorg' updates were kept back. I am assuming that within a day or two that will all be sorted out.
I am hoping I am correct in my decision. Any body care to give me some insight on this? Also, I saw the 'xorg intel' update in there, did that fix the intel issue (wishful thinking)? Some times it pays off to be patient and wait, as I am not really feeling a broken X tonite.

---

### Post by xebian on 2008-12-15
> **DougieFresh4U said:**
> I ignored updates all day today. I just checked again, and it said 90 updates and 30 to remove on the 'dist-upgrade'.
So went ahead and did just the 'upgrade' and it only removed 9 packages, no xorg stuff and updated 48 packages. All the 'xorg' updates were kept back. I am assuming that within a day or two that will all be sorted out.
I am hoping I am correct in my decision. Any body care to give me some insight on this? Also, I saw the 'xorg intel' update in there, did that fix the intel issue (wishful thinking)? Some times it pays off to be patient and wait, as I am not really feeling a broken X tonite.

You are correct.  The xorg's packages are not complete that's why it's being kept back.  It will remove the input stuff - kbd, mouse, etc..

But I let it remove what it wants and then re-installed mouse & kbd later with force.  To get the new xorg working I have to pass ignoreABI.  Working nicely.

---

### Post by ronacc on 2008-12-15
dougie is correct normal update no longer wants to remove the xserver stuff , i just got 53 upgraded 38 held back and 0 removed , rebooted ok .

---

### Post by danf_1979 on 2008-12-15
For this kind of situations:

```

$ sudo aptitude safe-upgrade

```

---

### Post by PmDematagoda on 2008-12-15
> **xebian said:**
> You are correct.  The xorg's packages are not complete that's why it's being kept back.  It will remove the input stuff - kbd, mouse, etc..

But I let it remove what it wants and then re-installed mouse & kbd later with force.  To get the new xorg working I have to pass ignoreABI.  Working nicely.

Just so you know, the mouse and kbd drivers are not useful if you are using the evdev driver. So if you have the evdev driver and it works properly, that is the only input driver you would ever need.

---

### Post by xebian on 2008-12-16
> **PmDematagoda said:**
> Just so you know, the mouse and kbd drivers are not useful if you are using the evdev driver. So if you have the evdev driver and it works properly, that is the only input driver you would ever need.

Thanks.  I just replaced them and it works quite well.

On a side note, how come the thank you button is not working for me. Tried sending you one but don't see it.  Any idea?

---

### Post by PmDematagoda on 2008-12-16
> **xebian said:**
> On a side note, how come the thank you button is not working for me. Tried sending you one but don't see it.  Any idea?

I see the Thanks button for you, perhaps it may be a cache problem on your side, try clearing the browser cache and see if it shows up.

And you are welcome:).

---

### Post by plun on 2008-12-16
> **danf_1979 said:**
> For this kind of situations:

```

$ sudo aptitude safe-upgrade

```

I slept on this and aptitude or apt is no good I believe...

xserver-xorg-dev is also upgraded.

The update manager is OK this morning...just x11-common and xbase-clients among x-packages are upgraded.

A new kernel is "also in town"...  (synaptic) ):P

---

### Post by dinxter on 2008-12-16
updated xorg seems fine on nvidia 8500gt with the drivers direct from [nvidia ]("ftp://download.nvidia.com/XFree86/Linux-x86_64/180.11/")with,

Section "ServerFlags"
        Option "IgnoreABI" "True"
EndSection

added to xorg.conf. the log shows,

================ WARNING WARNING WARNING WARNING 
This server has a video driver ABI version of 5.0 that this
driver does not officially support.  Please check
[http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X
server with a supported driver ABI.
=================================================================
(WW) NVIDIA: The driver will continue to load, but may behave strangely.
(WW) NVIDIA: This driver was compiled against the X.Org server SDK from git commit f5935288
1f315a634f60c9aac885b2764b28b167 and may not be compatible with the final version of this SDK.
(WW) NVIDIA: This server has an unsupported input driver ABI version (have 4.0, need < 4.0).  The driver will continue to load, but may behave strangely.

but log and glxinfo show 3d acceleration is running fine and haven't seen any other problems

---

### Post by caryb on 2008-12-16
My X is hosed as well I booted to recovery mode but the fix X option is not there:confused: So I installed the current Nvidia driver but that fails as well:icon_frown:


Cary

---

### Post by STEVE555 on 2008-12-16
I'm happy to report that I can now boot into the ordinary kernel by inserting ```
Option "IgnoreABI" "True"
```into my xorg.conf as posted by dinxter.It's certainly saved me having to boot into recovery mode everytime:D

Caryb,
     Have a look at my post here[http://ubuntuforums.org/showthread.php?t=1008190&page=2]("http://ubuntuforums.org/showthread.php?t=1008190&page=2")and see if that can help you for the time being.

Regards,
       STEVE555

---

### Post by philinux on 2008-12-16
I just played safe with the trusted:-
 sudo apt-get update && sudo apt-get upgrade

37 packages held back 36 xserver related.

---

### Post by Starks on 2008-12-16
How can I test the build process on the packages that still need to be built.

---

### Post by plun on 2008-12-16
> **dinxter said:**
> updated xorg seems fine on nvidia 8500gt with the drivers direct from [nvidia ]("ftp://download.nvidia.com/XFree86/Linux-x86_64/180.11/")with,

Section "ServerFlags"
        Option "IgnoreABI" "True"
EndSection



This one was a smart solution...  Thanks !

But... I am stucked with the terrible GDM greetings error.

Can someone with a working config please post a complete xorg.conf ?

tty is still broken for me so reboot in recovery is so boring..

Reinstalled nVidia driver twice and also made a clean xorg.conf with nvidia-xconfig and added ignoreABI.

Maybe I can see the greeting error with a SSH connection ?

---

### Post by linux6994 on 2008-12-16
It killed my S3 Savage. I could not get out of low resolution for anything. Editing xorg.conf to vesa helped a small bit but I mean small. I was able to see the top half of my screen on the bottom part of the monitor. I had to drop back to Intrepid, restore a few apps and restore /home. It was a fun endeavor but all is back and working on Intrepid. I will wait at least to RC1 before going up again.

---

### Post by PmDematagoda on 2008-12-16
> **plun said:**
> This one was a smart solution...  Thanks !

But... I am stucked with the terrible GDM greetings error.

Can someone with a working config please post a complete xorg.conf ?

tty is still broken for me so reboot in recovery is so boring..

Reinstalled nVidia driver twice and also made a clean xorg.conf with nvidia-xconfig and added ignoreABI.

Maybe I can see the greeting error with a SSH connection ?

My advice is to just quit trying. You are getting the ABI error for a reason and that is because the Nvidia driver still does not support X 1.6, this is the same which happened with X 1.5 until Nvidia released a driver that officially supported X 1.5.

Just use a driver like nv or nouveau, both of them do support X 1.6 since they follow the development in some way. I think nouveau is even moving onto DRI2 on the 3D side of development.

Another thing is, bug reports submitted by people using the Nvidia binary driver on X 1.6, for now, will most likely be ignored since for one, it is closed source and for two, Nvidia still does not officially support X 1.6(this is a pre-release version of X by the way).

---

### Post by STEVE555 on 2008-12-16
Hi Plun,
       Here is my xorg.conf attached with this post.
I updated my machine to the latest updates and my Xserver is still working,but my normal KDE-4.2 seems to be broken at the moment.I get the desktop,but my application launcher is missing.I tried to add it via add widgets,but plasma seems to be broken at the moment.I'm writing this post on my kde-neon-nightly installation until the developers can sort it out.

Regards,
       STEVE555

---

### Post by plun on 2008-12-16
Thanks all....!!!   I can see the error with a SSH connection..

Its a funny "brown bag"..   Xorg.0.log

> (**) Microsoft Microsoft Digital Sound System 80: always reports core
events
(**) Microsoft Microsoft Digital Sound System 80: Device:
"/dev/input/event2"
(II) Microsoft Microsoft Digital Sound System 80: Found keys
(II) Microsoft Microsoft Digital Sound System 80: Configuring as
keyboard
(II) XINPUT: Adding extended input device "Microsoft Microsoft Digital
Sound Sy$
(**) Option "xkb_rules" "evdev"
(**) Microsoft Microsoft Digital Sound System 80: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Microsoft Digital Sound System 80: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) Microsoft Microsoft Digital Sound System 80: xkb_layout: "se"

(**)
Microsoft Microsoft Digital Sound System 80: always reports core events
(**) Microsoft Microsoft Digital Sound System 80: Device: "/dev/input/event2"


Xorg thinks that my Sound System is a keyboard...:lolflag:

---

### Post by Totzo on 2008-12-16
Just started playing with jaunty and borked my xorg. For some daft reason I tried to install nvidia-glx-180 and allowed it to remove xorg. I then realised my folly and tried to reverse the process and ended up with a dpkg issue whilst trying to remove nvidia-glx-180. Oops.

Answer- revert repo to intrepid, install xorg, (keeping nvidia-180)
reboot, redo jaunty repo changes- et voila jaunty with no X problems, at least until I make the same daft mistake again!

Hope this helps someone else out :p

---

### Post by plun on 2008-12-16
I must surrender for this one ....:D:^o](*,)

Mission impossible and a Gnome start crashes all the time.

With KDM I can start a desktop session....

It must be more then one bug.....   ignoreABI seems to work just fine.

evdev.....:confused:


Rolled back to Intrepids Xserver with some hal troubles...


With a nosplash boot tty also works in normal mode.

---

### Post by Starks on 2008-12-16
Yeah, I rolled back to Intrepid too...

However, the xorg edgers ppa seems to have permanently screwed up compositing for me.

hopefully a reinstall of the system while preserving my home is in order.

---

### Post by DougieFresh4U on 2008-12-16
Just being curious, have they sorted out the Xorg drama?
I did do new kernel (.3) and rebooted with out any problem.
I would just like to get the** intel865G** working with out any work arounds or what ever.

---

### Post by Triggerhapp on 2008-12-17
Unless there was an update in the last 6 hours, Intels borked for me :P
It hangs before it reaches GDM and doesnt seem to do anything till yoou switch to a tty and kill gdm. Waiting for an update now :P

---

### Post by Starks on 2008-12-17
Here's a handy guide that might help with the version madness.

[http://www2.bryceharrington.org:8080/X/PkgList/versions_current.html](http://www2.bryceharrington.org:8080/X/PkgList/versions_current.html)

---

### Post by ShirishAg75 on 2008-12-17
Intel is still borked. I get till the GDM too but the keyboard dies (doesn't function). The mouse though works. Clicking on shutdown gives a rectangular dialog box with no letters in it. Just two boxes showing the figure cancel  and the other one with the check sign (meaning shutdown) . So have to guess. So still stuck. Updated to the newest xorg server. Today's updates

```

Log started: 2008-12-17  01:12:23
(Reading database ... 234662 files and directories currently installed.) 
Preparing to replace xserver-xorg-input-kbd 1:1.3.1-1ubuntu2 (using .../xserver-xorg-input-kbd_1%3a1.3.1-2ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-input-kbd ... 
Preparing to replace xserver-xorg 1:7.4~5ubuntu5 (using .../xserver-xorg_1%3a7.4~5ubuntu6_i386.deb) ... 
Unpacking replacement xserver-xorg ... 
Processing triggers for man-db ... 
(Reading database ... 234661 files and directories currently installed.) 
Removing xserver-xorg-input-all ... 
Removing xserver-xorg-input-mouse ... 
Processing triggers for man-db ... 
(Reading database ... 234652 files and directories currently installed.) 
Preparing to replace xserver-xorg-input-evdev 1:2.1.0-0ubuntu1 (using .../xserver-xorg-input-evdev_1%3a2.1.0-0ubuntu2_i386.deb) ... 
Unpacking replacement xserver-xorg-input-evdev ... 
Processing triggers for man-db ... 
(Reading database ... 234651 files and directories currently installed.) 
Removing xserver-xorg-input-wacom ... 
Removing xserver-xorg-input-vmmouse ... 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
 *** Restarting Hardware abstraction layer hald       [80G  [74G[ OK ] **
Processing triggers for man-db ... 
(Reading database ... 234632 files and directories currently installed.) 
Preparing to replace xserver-xorg-video-tseng 1:1.2.0-1build2 (using .../xserver-xorg-video-tseng_1%3a1.2.0-1ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-tseng ... 
Preparing to replace xserver-xorg-video-siliconmotion 1:1.6.0-1build2 (using .../xserver-xorg-video-siliconmotion_1%3a1.6.0-1ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-siliconmotion ... 
Preparing to replace xserver-xorg-video-geode 2.10.1-5 (using .../xserver-xorg-video-geode_2.11.0-1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-geode ... 
Preparing to replace xserver-xorg-video-intel 2:2.5.1-1ubuntu5 (using .../xserver-xorg-video-intel_2%3a2.5.1-1ubuntu6_i386.deb) ... 
Unpacking replacement xserver-xorg-video-intel ... 
Preparing to replace xserver-xorg-input-synaptics 0.15.2-0ubuntu7 (using .../xserver-xorg-input-synaptics_0.15.2-0ubuntu8_i386.deb) ... 
Unpacking replacement xserver-xorg-input-synaptics ... 
Preparing to replace xserver-xorg-core 2:1.5.3-1ubuntu1 (using .../xserver-xorg-core_2%3a1.5.99.3-0ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-core ... 
Processing triggers for man-db ... 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
 *** Restarting Hardware abstraction layer hald       [80G  [74G[ OK ] **
Setting up xserver-xorg-video-tseng (1:1.2.0-1ubuntu1) ... 
Setting up xserver-xorg-video-siliconmotion (1:1.6.0-1ubuntu1) ... 
Setting up xserver-xorg-video-geode (2.11.0-1) ... 
Setting up xserver-xorg-core (2:1.5.99.3-0ubuntu1) ... 
 
Setting up xserver-xorg-input-kbd (1:1.3.1-2ubuntu1) ... 
Setting up xserver-xorg-video-intel (2:2.5.1-1ubuntu6) ... 
 
Setting up xserver-xorg-input-synaptics (0.15.2-0ubuntu8) ... 
Setting up xserver-xorg-input-evdev (1:2.1.0-0ubuntu2) ... 
Setting up xserver-xorg (1:7.4~5ubuntu6) ... 
 
Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
Log ended: 2008-12-17  01:12:44

Log started: 2008-12-17  13:29:42
(Reading database ... 234623 files and directories currently installed.) 
Preparing to replace x11-common 1:7.4~5ubuntu6 (using .../x11-common_1%3a7.4~5ubuntu7_all.deb) ... 
Unpacking replacement x11-common ... 
Preparing to replace libglib2.0-dev 2.19.2-0ubuntu2 (using .../libglib2.0-dev_2.19.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libglib2.0-dev ... 
Preparing to replace libglib2.0-0-dbg 2.19.2-0ubuntu2 (using .../libglib2.0-0-dbg_2.19.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libglib2.0-0-dbg ... 
Preparing to replace libglib2.0-0 2.19.2-0ubuntu2 (using .../libglib2.0-0_2.19.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libglib2.0-0 ... 
Preparing to replace file-roller 2.24.1-1ubuntu1 (using .../file-roller_2.24.1-1ubuntu2_i386.deb) ... 
Unpacking replacement file-roller ... 
Preparing to replace libdrm2 2.4.1-0ubuntu7 (using .../libdrm2_2.4.1-0ubuntu8_i386.deb) ... 
Unpacking replacement libdrm2 ... 
Preparing to replace libdrm-intel1 2.4.1-0ubuntu7 (using .../libdrm-intel1_2.4.1-0ubuntu8_i386.deb) ... 
Unpacking replacement libdrm-intel1 ... 
Preparing to replace libglib2.0-cil 2.12.7-1ubuntu1 (using .../libglib2.0-cil_2.12.7-1ubuntu2_i386.deb) ... 
Unpacking replacement libglib2.0-cil ... 
Preparing to replace libgtk2.0-cil 2.12.7-1ubuntu1 (using .../libgtk2.0-cil_2.12.7-1ubuntu2_i386.deb) ... 
Unpacking replacement libgtk2.0-cil ... 
Preparing to replace libglade2.0-cil 2.12.7-1ubuntu1 (using .../libglade2.0-cil_2.12.7-1ubuntu2_i386.deb) ... 
Unpacking replacement libglade2.0-cil ... 
Preparing to replace libglib2.0-data 2.19.2-0ubuntu2 (using .../libglib2.0-data_2.19.3-0ubuntu1_all.deb) ... 
Unpacking replacement libglib2.0-data ... 
Preparing to replace libglu1-xorg-dev 1:7.4~5ubuntu6 (using .../libglu1-xorg-dev_1%3a7.4~5ubuntu7_all.deb) ... 
Unpacking replacement libglu1-xorg-dev ... 
Preparing to replace libgtop2-common 2.24.0-0ubuntu2 (using .../libgtop2-common_2.24.0-0ubuntu3_all.deb) ... 
Unpacking replacement libgtop2-common ... 
Preparing to replace libgtop2-7 2.24.0-0ubuntu2 (using .../libgtop2-7_2.24.0-0ubuntu3_i386.deb) ... 
Unpacking replacement libgtop2-7 ... 
Preparing to replace libndesk-dbus1.0-cil 0.6.0-1 (using .../libndesk-dbus1.0-cil_0.6.0-1ubuntu1_all.deb) ... 
Removing libndesk-dbus1.0-cil from Mono 
Unpacking replacement libndesk-dbus1.0-cil ... 
Preparing to replace libndesk-dbus-glib1.0-cil 0.4.1-1 (using .../libndesk-dbus-glib1.0-cil_0.4.1-1ubuntu1_all.deb) ... 
Removing libndesk-dbus-glib1.0-cil from Mono 
Unpacking replacement libndesk-dbus-glib1.0-cil ... 
Preparing to replace system-config-printer-kde 4:4.1.80-0ubuntu1 (using .../system-config-printer-kde_4%3a4.1.85-0ubuntu1_all.deb) ... 
Unpacking replacement system-config-printer-kde ... 
Preparing to replace xbase-clients 1:7.4~5ubuntu6 (using .../xbase-clients_1%3a7.4~5ubuntu7_all.deb) ... 
Unpacking replacement xbase-clients ... 
Preparing to replace xlibmesa-gl-dev 1:7.4~5ubuntu6 (using .../xlibmesa-gl-dev_1%3a7.4~5ubuntu7_all.deb) ... 
Unpacking replacement xlibmesa-gl-dev ... 
Preparing to replace xserver-common 2:1.5.99.3-0ubuntu1 (using .../xserver-common_2%3a1.5.99.3-0ubuntu3_all.deb) ... 
Unpacking replacement xserver-common ... 
Preparing to replace xserver-xorg-core 2:1.5.99.3-0ubuntu1 (using .../xserver-xorg-core_2%3a1.5.99.3-0ubuntu3_i386.deb) ... 
Unpacking replacement xserver-xorg-core ... 
Preparing to replace xserver-xorg 1:7.4~5ubuntu6 (using .../xserver-xorg_1%3a7.4~5ubuntu7_i386.deb) ... 
Unpacking replacement xserver-xorg ... 
Preparing to replace xorg 1:7.4~5ubuntu6 (using .../xorg_1%3a7.4~5ubuntu7_i386.deb) ... 
Unpacking replacement xorg ... 
Preparing to replace xutils 1:7.4~5ubuntu6 (using .../xutils_1%3a7.4~5ubuntu7_all.deb) ... 
Unpacking replacement xutils ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Setting up x11-common (1:7.4~5ubuntu7) ... 
 
Setting up libglib2.0-0 (2.19.3-0ubuntu1) ... 
 
Setting up libglib2.0-dev (2.19.3-0ubuntu1) ... 
Setting up libglib2.0-0-dbg (2.19.3-0ubuntu1) ... 
Setting up file-roller (2.24.1-1ubuntu2) ... 
 
Setting up libdrm2 (2.4.1-0ubuntu8) ... 
 
Setting up libdrm-intel1 (2.4.1-0ubuntu8) ... 
 
Setting up libglib2.0-cil (2.12.7-1ubuntu2) ... 
Setting up libgtk2.0-cil (2.12.7-1ubuntu2) ... 
Setting up libglade2.0-cil (2.12.7-1ubuntu2) ... 
Setting up libglib2.0-data (2.19.3-0ubuntu1) ... 
Setting up libglu1-xorg-dev (1:7.4~5ubuntu7) ... 
Setting up libgtop2-common (2.24.0-0ubuntu3) ... 
Setting up libgtop2-7 (2.24.0-0ubuntu3) ... 
 
Setting up libndesk-dbus1.0-cil (0.6.0-1ubuntu1) ... 
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono 
 
Setting up libndesk-dbus-glib1.0-cil (0.4.1-1ubuntu1) ... 
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono 
 
Setting up system-config-printer-kde (4:4.1.85-0ubuntu1) ... 
Setting up xbase-clients (1:7.4~5ubuntu7) ... 
Setting up xlibmesa-gl-dev (1:7.4~5ubuntu7) ... 
Setting up xserver-common (2:1.5.99.3-0ubuntu3) ... 
Setting up xutils (1:7.4~5ubuntu7) ... 
 
Setting up xserver-xorg (1:7.4~5ubuntu7) ... 
 
Setting up xserver-xorg-core (2:1.5.99.3-0ubuntu3) ... 
 
Setting up xorg (1:7.4~5ubuntu7) ... 
Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Log ended: 2008-12-17  13:30:52

```Notice the 

* Restarting Hardware abstraction layer hald       [80G  [74G[ OK ]  

It shouldn't appear like that, should it?

---

### Post by TerminX on 2008-12-17
> **PmDematagoda said:**
> My advice is to just quit trying. You are getting the ABI error for a reason and that is because the Nvidia driver still does not support X 1.6, this is the same which happened with X 1.5 until Nvidia released a driver that officially supported X 1.5.
The new ABI is already supported by the latest NVIDIA driver, the support just isn't official (pre-release version of X and all) and isn't enabled by default.  IgnoreABI should be perfectly safe to use and GLX should work fine.  180.16 + compiz on 1.5.99.3 is working great for me.

---

### Post by plun on 2008-12-17
Yup, ignoreABI seems to be OK but something else brakes Gnome for me...
[I][B]
""The greeter application appears to be crashing[/B][/I]""

Bug for nVidia users:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410)

---

### Post by jfernyhough on 2008-12-17
Finally took the plunge.

180.16+1.5.99 working fine.

I did, however, ignore nvidia-settings when it asked to update xorg.conf. The only additions to a plain dpkg-reconfigure -phigh xserver-xorg are specifying the ConfiguredDevice "Driver" "nvidia" and adding ServerFlags IgnoreABI True.

I still have horrifically poor scrolling performance in Java apps, though.

---

### Post by plun on 2008-12-17
Yup... reinstalled my system partition and ignoreABI works just fine. :D

Still on kernel 2.6.28-2 and using nVidia driver 180.16...

---

### Post by jfernyhough on 2008-12-17
OK, maybe it's not quite "fine" but "close enough". I have an oddity with my mouse cursor - or rather, I have two.

If I run metacity I have a static cursor in one part of my screen, and I have the other controllable cursor.

When I run compiz the static cursor disappears until, e.g.,  I scroll a webpage in Firefox where it appears while I scroll, then it disappears again. Also, when I move over a hyperlink while the cursor would normally change to a pointing finger and stay that way while I hover over the link, it now changes immediately back to the normal arrow.

I imagine this is down to evdev. It's both fun and annoying. :D

---

### Post by plun on 2008-12-17
> **jfernyhough said:**
> 
I imagine this is down to evdev. It's both fun and annoying. :D

Yup...also some strange issues when hovering over different functions on desktop... but it works..:D

I am going to try to find what caused my "mess"... just a few non standard apps, Compiz, Murrine and PulseAudio from GIT/SVN.

---

### Post by Kevbert on 2008-12-17
My Nvidia driver has just broken with the 177 driver, can't set up driver on display:0 or :1. A system update tries to install a new nv driver(?) My display adapter is a Geoforce 7600GS.  I'll do a re-install when Alpha2 comes out tomorrow and see what happens.

---

### Post by ronacc on 2008-12-17
I'm still ok here with 180.11 and 2.6.28-2 and xorg 1.5.3  but I use apt-get for updates and have been avoiding dist-upgrades .

---

### Post by plun on 2008-12-17
> **ronacc said:**
> I'm still ok here with 180.11 and 2.6.28-2 and xorg 1.5.3  but I use apt-get for updates and have been avoiding dist-upgrades .

Yup but you are "stucked" in there...as it look.

Our devs choosed to block nVidia and ATI with Jockey..

> jockey (0.5~beta3-0ubuntu10) jaunty; urgency=low

  * data/handlers/{fglrx,nvidia}.py: Disable for now, they do not
    currently work with X.org 1.6.

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001962.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001962.html)

 

Wrong, IMHO.. nVidia apparently works

Its just the "mess" to add ignoreABI and then install the driver again in recovery or with nosplash and normal tty.  (and a pray ):P  )

---

### Post by philinux on 2008-12-17
Is it not better to just wait, rather than do all these workarounds. I'm still using update && upgrade and things are fine. If things are kept back eventually it will sort itself out.

---

### Post by plun on 2008-12-17
> **philinux said:**
> Is it not better to just wait, rather than do all these workarounds. I'm still using update && upgrade and things are fine. If things are kept back eventually it will sort itself out.

Well... its a free world.

Its discussed in the end of this bug report...
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410)


Filed another one against evdev and my MS sound system  ;)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/309100](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/309100)

---

### Post by philinux on 2008-12-17
Hi Plun,

I was asking, from a testing point of view is it better to wait.

I've enjoyed busting things up myself with partials and workarounds, but is it the best way?

---

### Post by plun on 2008-12-17
> **philinux said:**
> 

I was asking, from a testing point of view is it better to wait.

I've enjoyed busting things up myself with partials and workarounds, but is it the best way?

If you read all comments and also Mr Harringtons referal to Alpha 2 known issues its probably better to just take the challenge...

[https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview](https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview)

> # A new XServer, version 1.6, is included in Alpha-2. The binary proprietary drivers -fglrx and -nvidia are not yet supported for this server and will exhibit various serious issues if run against it. Users of these drivers are encouraged to wait or to switch to the corresponding open source drivers (-ati and -nv respectively) in the meantime.

# -nouveau is available in Alpha-2 universe as an EXPERIMENTAL X driver for expert nVidia users only. We are accepting patches but not bug reports at this time. Regular users should stick with -nv for now.
#

Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it via the DontZap option in xorg.conf. A GUI tool to simplify setting xorg.conf options is under development and will be available in a later Alpha release. 

This is a development version and still a early one....

Excellent way to learn more about different functions "under the hood"...  but of course this can be changed but I dont think so.

---

### Post by Starks on 2008-12-17
I hope Jaunty's xserver gets fixed soon, I hate using the Intrepid packages.

---

### Post by ShirishAg75 on 2008-12-18
lot of updates today morning. Almost 90 odd updates, including the new kernel. Now able to get upto the login window and type but keyboard is so so slow.

---

### Post by DougieFresh4U on 2008-12-18
Wondering if the xserver-xorg issue has resolved as I see they are still being held back during update this morning

---

### Post by ! ! ! winner on 2008-12-18
> **chrismine said:**
> I took the plunge...

I will be waiting for awhile...

Except if somebody has got a workaround?

[http://www.prizerebel.com/index.php?r=806574](http://www.prizerebel.com/index.php?r=806574)

---

### Post by autocrosser on 2008-12-18
There are still upgrade problems here--I'm waiting for it to be worked out.....I'll post as soon as I get a good upgrade path.

---

### Post by plun on 2008-12-18
> **autocrosser said:**
> There are still upgrade problems here--I'm waiting for it to be worked out.....I'll post as soon as I get a good upgrade path.

Well... the safest way must be to just uninstall/deactivate 3D drivers from nVidia and ATI and then upgrade Xserver

There are no more comments about the nVidia driver within [the bug report]("https://bugs.launchpad.net/bugs/308410").

After that its up to every user to install and **enable ignoreABI** within xorg.conf..... !!!

Its also more important that Xserver 1.6 is tested early, so this is just good. IMHO

Maybe Alberto will change this but it will probably take a while for him.
Jockey is also changed and nVidia/ATI disabled for the moment.

Alpha2 is also within "soft freeze" for the moment...

---

### Post by jfernyhough on 2008-12-18
> Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it via the DontZap option in xorg.conf. A GUI tool to simplify setting xorg.conf options is under development and will be available in a later Alpha release.COh so /that's/ why it doesn't work. I was considering it a bug with the new packages. What a stupid thing to do - surely if you do it by accident you do it once and never again.

---

### Post by NoelJB on 2008-12-18
> > I will be waiting for awhile...
> > Except if somebody has got a workaround?

> Use the nv driver.

Someone has a high performance, high feature, sports car for which a new kind of tire isn't yet compatible, and he's told to downgrade to a Yugo because it is compatible with that tire, rather than told that the new tire is just for testing, isn't of all that much importance, and that, yes, he should just relax and wait for his sports car to be prepared for it.

Licensing zealotry aside, nv is a toy whose sole value can be found in acting as a backup for when a real driver cannot be made available.  And nouveau is not much, if any, better.  Certainly not at this stage of development, nor any time soon.

Would we all like fully functional Open Source drivers?  Yes, of course.  But we *need* fully functional drivers.  Who is going to explain to the newbie when suspend/resume stops working?  Or the eye candy?  Or any of the myriad other things not supported except by the real driver?  He is prepared to wait, so lets not downgrade his experience.

---

### Post by plun on 2008-12-18
> **NoelJB said:**
> > > I will be waiting for awhile...
> > Except if somebody has got a workaround?

> Use the nv driver.

Someone has a high performance, high feature, sports car for which a new kind of tire isn't yet compatible, and he's told to downgrade to a Yugo because it is compatible with that tire, rather than told that the new tire is just for testing, isn't of all that much importance, and that, yes, he should just relax and wait for his sports car to be prepared for it.

Licensing zealotry aside, nv is a toy whose sole value can be found in acting as a backup for when a real driver cannot be made available.  And nouveau is not much, if any, better.  Certainly not at this stage of development, nor any time soon.

Would we all like fully functional Open Source drivers?  Yes, of course.  But we *need* fully functional drivers.  Who is going to explain to the newbie when suspend/resume stops working?  Or the eye candy?  Or any of the myriad other things not supported except by the real driver?  He is prepared to wait, so lets not downgrade his experience.

Well... whatever our devs chooses for solution the nVidia challenge can be fixed. ATI is probably impossible, Intel 86X seems to have trouble.

We are for sure no helpless noobs and we can for sure help each other to fix 3D.   Newbies should also stay away from Alphas !!!

Some users will also choose the Nouveau driver and its just great.

But for sure the best solution is to rebuild the 180 driver and a script for ignoreABI but I don't think they have time for that...

---

### Post by NoelJB on 2008-12-18
> **plun said:**
> 
We are for sure no helpless noobs and we can for sure help each other to fix 3D.   Newbies should also stay away from Alphas !!!

Wasn't talking about you.  :-)  I've seen your name around, and have a fair idea of your capabilities.  I'm just referring to almost knee-jerk reactions to recommend drivers that we know are functionally bad.

And, yes, it is all well and good to tell newbies to stay away from alpha releases, but (a) they'll play with it anyway, and (b) there are plenty of constructive things that they can do and test without sending them into known areas of breakage that turn them off from working in more useful areas.  :-)

> **plun said:**
> 
Some users will also choose the Nouveau driver and its just great.

As the release notes suggest, if one is not prepared and able to submit patches against the driver, please don't bother using it.

> **plun said:**
> 
But for sure the best solution is to rebuild the 180 driver and a script for ignoreABI but I don't think they have time for that...

That's one option.  Another is to wait for nvidia to put out a 180 drop intended for 1.6, and hopefully also fixing the suspend/resume bug they they introduced in the 180 series.

Meanwhile, there are so many other areas of Jaunty to test and work on that don't require upgrading to the latest X server. :-)

---

### Post by philinux on 2008-12-18
Just did the usual apt-get update upgrade and it went wonky until 3 reboots sorted it. It only removed the 177 driver. When I got in I enabled the driver and all ok now.

Whew>>>

---

### Post by autocrosser on 2008-12-18
Well, plun my friend---I must either use the repo drivers or "roll my own" due to the SLI setup I have as I have not been able to get the nv driver to even start with SLI & I really doubt that the Nouveau driver can work with SLI either.....


I am thinking about the "roll my own" option---will see how things work this week & next---I'm holding out for Alberto to come thru again ;)

Cheers!!!!
autocrosser

> **plun said:**
> Well... the safest way must be to just uninstall/deactivate 3D drivers from nVidia and ATI and then upgrade Xserver

There are no more comments about the nVidia driver within [the bug report]("https://bugs.launchpad.net/bugs/308410").

After that its up to every user to install and **enable ignoreABI** within xorg.conf..... !!!

Its also more important that Xserver 1.6 is tested early, so this is just good. IMHO

Maybe Alberto will change this but it will probably take a while for him.
Jockey is also changed and nVidia/ATI disabled for the moment.

Alpha2 is also within "soft freeze" for the moment...

---

### Post by plun on 2008-12-19
> **NoelJB said:**
> 
And, yes, it is all well and good to tell newbies to stay away from alpha releases, but (a) they'll play with it anyway, and (b) there are plenty of constructive things that they can do and test without sending them into known areas of breakage that turn them off from working in more useful areas.  :-)

That's one option.  Another is to wait for nvidia to put out a 180 drop intended for 1.6, and hopefully also fixing the suspend/resume bug they they introduced in the 180 series.

Meanwhile, there are so many other areas of Jaunty to test and work on that don't require upgrading to the latest X server. :-)

Well... Hardy and Intrepid was both messed up because of "waiting and waiting".  

Its better to take "the ****" in the beginning and also that newbies maybe learns what a development version is.... ):P

The resume/suspend bug is probably a combination of a kernel bug and mismatch with the nVidia driver

Linus blog:
[http://torvalds-family.blogspot.com/2008/12/debugging-hell.html](http://torvalds-family.blogspot.com/2008/12/debugging-hell.html)

Nevertheless not important for a development, non-production version !
I cannot understand any whinings about this !  Just to collect all facts within a bug report and also a bug report to nVidia.

Nevertheless the 180.16 driver from nVidia works excellent with Xserver 1.6 at least for me....

---

### Post by plun on 2008-12-19
> **autocrosser said:**
> Well, plun my friend---I must either use the repo drivers or "roll my own" due to the SLI setup I have as I have not been able to get the nv driver to even start with SLI & I really doubt that the Nouveau driver can work with SLI either.....



Of course.... "dinxter's" solution just works.

Alberto must rebuild the driver and preferred is 180.16, maybe nVidia releases a new one today...

If Alberto doesn't rebuilt it, install [the driver]("http://www.nvnews.net/vbulletin/showthread.php?p=1873716") from recovery

IgnoreABI must be set within xorg.conf.

Jockey must be changed again.....

Thats it, not so much, IMHO....):P

---

### Post by mariuz on 2008-12-19
> **plun said:**
> Of course.... "dinxter's" solution just works.

Alberto must rebuild the driver and preferred is 180.16, maybe nVidia releases a new one today...

If Alberto doesn't rebuilt it, install [the driver]("http://www.nvnews.net/vbulletin/showthread.php?p=1873716") from recovery

IgnoreABI must be set within xorg.conf.

Jockey must be changed again.....

Thats it, not so much, IMHO....):P

Thanks i was just setting it in gdm.conf 
without results
:lolflag:

---

### Post by philinux on 2008-12-19
Installing the nvidia drivers from system>admin>hardware drivers removes xserver-xorg in the background. No warning.

Had to install xserver-xorg from recovery to get back in. ):P

---

### Post by DougieFresh4U on 2008-12-19
good morning all from cold and snowy New York :mad:
I take it the xserver issue is not resolved yet?
Unfortunetly I use onboard Intel865G. graphics
I wait eagerly for the fix ):P

---

### Post by autocrosser on 2008-12-19
Yes--I've done it many times before...and I would really want to move forward soon..I'm putting another 500MB drive in this weekend & might just do it then.

I'll E Alberto & see where he is at---
Cheers!!!!


> **plun said:**
> Of course.... "dinxter's" solution just works.

Alberto must rebuild the driver and preferred is 180.16, maybe nVidia releases a new one today...

If Alberto doesn't rebuilt it, install [the driver]("http://www.nvnews.net/vbulletin/showthread.php?p=1873716") from recovery

IgnoreABI must be set within xorg.conf.

Jockey must be changed again.....

Thats it, not so much, IMHO....):P

---

### Post by tseliot on 2008-12-19
> **autocrosser said:**
> Yes--I've done it many times before...and I would really want to move forward soon..I'm putting another 500MB drive in this weekend & might just do it then.

I'll E Alberto & see where he is at---
Cheers!!!!
Would you prefer that I rebuild the packages (which won't work unless the IgnoreABI option is enabled)?

Also did anyone see if drivers other than 180 (i.e. 177, 173, 96) work with the new X.org?

---

### Post by plun on 2008-12-19
> **tseliot said:**
> Would you prefer that I rebuild the packages (which won't work unless the IgnoreABI option is enabled)?

Also did anyone see if drivers other than 180 (i.e. 177, 173, 96) work with the new X.org?

Hi Alberto

180.16 and 180.11 is OK....   177.82 crashes.

This will probably be a mess....so "bless this mess"..O:)

EDIT

Please rebuild the driver with 180.16....  VDPAU is fixed...

---

### Post by tseliot on 2008-12-19
> **plun said:**
> Hi Alberto

180.16 and 180.11 is OK....   177.82 crashes.

This will probably be a mess....so "bless this mess"..O:)

EDIT

Please rebuild the driver with 180.16....  VDPAU is fixed...

Ok, I'll rebuild driver 180 updating it to 180.16

---

### Post by plun on 2008-12-19
> **tseliot said:**
> Ok, I'll rebuild driver 180 updating it to 180.16

Great and thanks....:KS

Alpha 2, known issues, must also be updated that nvidia cards below GPU 6XXX
is broken and must use the nv or vesa driver

[https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview](https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview)

But... maybe the beta drivers works for older cards.. ???

---

### Post by mattduckman on 2008-12-19
> **DougieFresh4U said:**
> good morning all from cold and snowy New York :mad:
I take it the xserver issue is not resolved yet?
Unfortunetly I use onboard Intel865G. graphics
I wait eagerly for the fix ):P

i've been using the -intel driver since wednesday's updates, but i have an intel945GM. maybe i'm just lucky.

---

### Post by autocrosser on 2008-12-19
> **tseliot said:**
> Ok, I'll rebuild driver 180 updating it to 180.16

THANK YOU!!!!  Is good to hear from you!! I'll wait til I see the driver.....

---

### Post by DougieFresh4U on 2008-12-19
> **mattduckman said:**
> i've been using the -intel driver since wednesday's updates, but i have an intel945GM. maybe i'm just lucky.

Updates on Wednesday wanted to remove many, many packages and had 42 packages that were held back (doing just 'upgrade')
I saw the Intel update in there but I didn't let it install as it was in that mess of 'xserver-xorg updates,removal,dependency issues. I was waiting for it all to get resolved.

---

### Post by ayates on 2008-12-19
173.14.15 on FX-5900 with -ignoreABI works here.

---

### Post by alexv75 on 2008-12-20
180.11.02 on xserver 1.5.99.3 works flawlessly with the "IgnoreABI" "True" option. For me it feels like this driver is faster than 180.16 in 2D :s

---

### Post by plun on 2008-12-20
> **alexv75 said:**
> 180.11.02 on xserver 1.5.99.3 works flawlessly with the "IgnoreABI" "True" option. For me it feels like this driver is faster than 180.16 in 2D :s

Yup... it might be so but 180.16 supports VDPAU better...

Xine also now supports it...
[http://www.phoronix.com/scan.php?page=news_item&px=Njk0MA](http://www.phoronix.com/scan.php?page=news_item&px=Njk0MA)

My Glxgears values went down with 180.16 but is still excellent at least
on my PC....  :)

---

### Post by ShirishAg75 on 2008-12-20
hi guys, totally off-topic but would love to get some help here [http://ubuntuforums.org/showthread.php?t=1016586](http://ubuntuforums.org/showthread.php?t=1016586)

---

### Post by autocrosser on 2008-12-20
I just got updates & the path was clear--updated Xorg (all of it) & the driver 180.16 was unblocked...using PPA:

#Restricted PPAs for .28 Kernel
deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

180.16 driver installed without problems--just added the:

Section "ServerFlags"
Option "IgnoreABI"      "True"
EndSection

as per dinxter's fix.

:popcorn: :guitar: :):):)

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> I just got updates & the path was clear--updated Xorg (all of it) & the driver 180.16 was unblocked...using PPA:

#Restricted PPAs for .28 Kernel
deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

180.16 driver installed without problems--just added the:

Section "ServerFlags"
Option "IgnoreABI"      "True"
EndSection

as per dinxter's fix.

:popcorn: :guitar: :):):)


Yes the driver was rebuild 7 hours ago.....

[https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive)

> Publishing details

    * Published 7 hours ago

Changelog

nvidia-graphics-drivers-180 (180.16-0ubuntu0andersk1) jaunty; urgency=low

  * Add driver 180.16.



Maybe you also must change mouse settings a little...:)

---

### Post by autocrosser on 2008-12-21
Mouse is working normally--no "bumps in the road" at this time.....

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> Mouse is working normally--no "bumps in the road" at this time.....

Ok... I also installed the ppa version and it seems to work OK including DKMS.

A new updated Xorg seems also to be coming....

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002109.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002109.html)

See if it causes trouble for this driver...

---

### Post by ronacc on 2008-12-21
> **plun said:**
> Ok... I also installed the ppa version and it seems to work OK including DKMS.

A new updated Xorg seems also to be coming....

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002109.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002109.html)

See if it causes trouble for this driver...

> xorg (1:7.4~5ubuntu8) jaunty; urgency=low

  * Disable terminal to prevent root access (LP: #310126)  

"explative deleted" have they gone crazy ?????

---

### Post by plun on 2008-12-21
> **ronacc said:**
> "explative deleted" have they gone crazy ?????

Impossible to get any facts about it....

Bug 310126,  seems to be a non public report.

[I]Not allowed here

Sorry, you don't have permission to access this page. [/I]

---

### Post by tghe-retford on 2008-12-21
Since installing the 180.16 driver, and all the Xorg packages, my cursor on Firefox now goes funny when a tooltip shows up, the cursor changes from a hand to a normal pointer. And sometimes, the pointer will quickly flash between a hand and a pointer about three times before it changes to a normal pointer. Happens here and on other websites as well. :confused:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97129&d=1229858672[/IMG]

---

### Post by plun on 2008-12-21
> **tghe-retford said:**
> Since installing the 180.16 driver, and all the Xorg packages, my cursor on Firefox now goes funny when a tooltip shows up, the cursor changes from a hand to a normal pointer. And sometimes, the pointer will quickly flash between a hand and a pointer about three times before it changes to a normal pointer. Happens here and on other websites as well. :confused:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97129&d=1229858672[/IMG]

The same happened for me and I adjusted settings for the mouse.

A **_small_** decrease for both Acceleration and Sensitivity.

System > Prefs > Mouse

---

### Post by rudenko_ruslan on 2008-12-21
> **tghe-retford said:**
> Since installing the 180.16 driver, and all the Xorg packages, my cursor on Firefox now goes funny when a tooltip shows up, the cursor changes from a hand to a normal pointer. And sometimes, the pointer will quickly flash between a hand and a pointer about three times before it changes to a normal pointer. Happens here and on other websites as well. :confused:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97129&d=1229858672[/IMG]
Yeah, I have that problem too. Plun said something about mouse settings, maybe he knows the cure? :confused:

---

### Post by tghe-retford on 2008-12-21
> **plun said:**
> The same happened for me and I adjusted settings for the mouse.

A **_small_** decrease for both Acceleration and Sensitivity.

System > Prefs > Mouse
That hasn't fixed the problem for me (sensitivity doesn't seem to know the meaning of a small decrease :D).

---

### Post by plun on 2008-12-21
> **tghe-retford said:**
> That hasn't fixed the problem for me (sensitivity doesn't seem to know the meaning of a small decrease :D).

Well for me it was OK after a slight decrease for both.

I am also running Firefox 3.1 and not 3.05 if something differs.

FF3.1 is within Jauntys repo.

Also check Xorg.0.log for maybe more clues.   /var/log/

---

### Post by rudenko_ruslan on 2008-12-21
> **plun said:**
> The same happened for me and I adjusted settings for the mouse.

A **_small_** decrease for both Acceleration and Sensitivity.

System > Prefs > Mouse
Thank you very much. That helped me. =D>

---

### Post by plun on 2008-12-21
> **rudenko_ruslan said:**
> Thank you very much. That helped me. =D>

Great !  :)

Well.. maybe a bigger change in settings are needed for some users..:confused:

Run with a slow mouse a minute or two and then go back...


We can probably nail a bug for evdev..:) 

.

---

### Post by LordVeovis on 2008-12-21
Ok, I want to make sure I am going to do this right as I am not as experienced as some other users here (tho not a newb)

Initiallyt when I installed 9.04 I ran the update and it broke alot... I am using Nvidia 8600GTS card.  I just wanted to make sre as long as I add the section to the xorg.conf file I should be able to update just fine, and it wont matter that I get all the new xorg stuff, right?

---

### Post by tghe-retford on 2008-12-21
> **plun said:**
> Well.. maybe a bigger change in settings are needed for some users..:confused:

Run with a slow mouse a minute or two and then go back...


We can probably nail a bug for evdev..:) 

.
I turned the settings all the way down to minimum and then back to normal and the bug disappears on the page I am viewing, then returns if I navigate to another page. The mouse settings don't work for me and the bug remains.

---

### Post by ronacc on 2008-12-21
Is it evdev or firefox ? , I am seeing this in FF both 3.05 and 3.1 but not in Opera both 9.62 and 10.0 alpha1 .

---

### Post by plun on 2008-12-21
> **LordVeovis said:**
> Ok, I want to make sure I am going to do this right as I am not as experienced as some other users here (tho not a newb)

Initiallyt when I installed 9.04 I ran the update and it broke alot... I am using Nvidia 8600GTS card.  I just wanted to make sre as long as I add the section to the xorg.conf file I should be able to update just fine, and it wont matter that I get all the new xorg stuff, right?

No... Jauntys driver is broken (dependency error with Xorg 1.6) and must be rebuild. 

Easiest way is to use the ppa which "autocrosser" points out and also "dinxter´s" fix for ignoreABI

Please read !
[http://ubuntuforums.org/showpost.php?p=6408781&postcount=83](http://ubuntuforums.org/showpost.php?p=6408781&postcount=83)

:)

EDIT

After enabling the ppa:

```
sudo apt-get update

sudo apt-get install nvidia-glx-180
```

---

### Post by tghe-retford on 2008-12-21
> **ronacc said:**
> Is it evdev or firefox ? , I am seeing this in FF both 3.05 and 3.1 but not in Opera both 9.62 and 10.0 alpha1 .
I noticed this happened since I did the upgrade for the NVidia 180.16 driver (using the PPA posted on this thread), all the Xorg packages and Gnome packages this morning. I upgraded Firefox manually a few days ago to 3.05 and it didn't have this problem when I upgraded back then.

---

### Post by ronacc on 2008-12-21
more info: I tried  several more browsers , arora ,dillo , epiphany ,galeon and seamonkey . seamonkey is the only one other than FF to show this behavior.Perhaps it has something to do with the way FF renders links since it seems to occur when passing over them .

@tghe-retford  I am running 180.16 hand installed from nvidia I also updated this am .

---

### Post by Peter76 on 2008-12-21
I have jaunty running under virtual box ( now 2.1 ) and can't get x running anymore. Tried booting into safe mode and using the reset x function there and reinstalling the vbox additional stuff, but it doesn't help. My xorg.conf shows only the "configured device" stuff. How can I fix this?

---

### Post by plun on 2008-12-21
> **ronacc said:**
> more info: I tried  several more browsers , arora ,dillo , epiphany ,galeon and seamonkey . seamonkey is the only one other than FF to show this behavior.Perhaps it has something to do with the way FF renders links since it seems to occur when passing over them .


I also tested with Opera 10 and its rock solid... (but FF3.1 is also OK after adjustment)

(ubulette also wrote about mouse troubles yesterday)

Can you please file this bug  ?   :D

---

### Post by autocrosser on 2008-12-21
> **tghe-retford said:**
> I noticed this happened since I did the upgrade for the NVidia 180.16 driver (using the PPA posted on this thread), all the Xorg packages and Gnome packages this morning. I upgraded Firefox manually a few days ago to 3.05 and it didn't have this problem when I upgraded back then.


I've been running FF 3.1 as a custom install for a couple of months now & left 3.0 far behind (too many problems)--Install 3.1 from the repos & play with your mouse settings like plun suggested--running very well here--I just have to be carefull after a full-screen game (Prey--UT2004)--if I goto a webpage (in FF) right after playing--I get a session restart...Haven't had time to track that one yet---if I just use the desktop without going on the web it "seems" to be OK---Plun, have you seen that yet???

---

### Post by ronacc on 2008-12-21
what do I file it against ? I still think the "problem" is with FF or its rendering engine . tried your cure moved mouse speed down 1 notch and it did clear the problem then moved mouse speed back to where it was and although the mouse came back up to its original speed the problem stayed gone until FF was closed and reopened .

---

### Post by DougieFresh4U on 2008-12-21
Ok, I finally let all the updates for xserver go through. All went pretty well as when I rebooted, it booted into the 'Intel' instead of 'vesa' which made me happy. I still think the Intel is a little buggy. I say this because I have had to reboot 5 or 6 times in the last few minutes because when desktop loaded it would freeze, mouse was the only thing that was working but clicking on any thing wouldn't work but mouse pointer would move around screen.
If there is some where I should be checking to see what was going on, please let me know. I also think my resolution is not right as panel bars are big but screen res. says 12180x1024 and refresh is 75
So over all it was a good thing didn't 'bork' my machine as expected
Not getting that error messege while booting, which makes boot time fast now

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> if I just use the desktop without going on the web it "seems" to be OK---Plun, have you seen that yet???

Nope, I cannot see it elsewhere then with Firefox...the mouse is "nervous" and with Opera this behavior is complete gone.

@ronacc... so a bug against Firefox could not be wrong, the magic fta also knows about this challenge...:P

---

### Post by autocrosser on 2008-12-21
HMMMMMMMMMM---guess I'll root thru the logs in a while to see what triggered it--happened twice last night--one time each for Prey & UT2004--played UT later & just puttered with the desktop for about 5~10 minutes & then FF worked "normally"

This of course was after the new nVidia driver went thru.......

Also it's nice to have the artifacts at the top of my screen gone at last!!! They were driving me bonkers!!!

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> HMMMMMMMMMM---guess I'll root thru the logs in a while to see what triggered it--happened twice last night--one time each for Prey & UT2004--played UT later & just puttered with the desktop for about 5~10 minutes & then FF worked "normally"

This of course was after the new nVidia driver went thru.......

Yes but when this happended also Xorg was upgraded for you.
The old driver blocked it 

"ubulette" also posted crash outputs within the 180.11 thread.
He for sure knows Firefox...:)

We probably needs better debug tools...:confused:

---

### Post by autocrosser on 2008-12-21
Ya--I didn't forget that--just have a "hunch" that the problem is with nVidia, not Xorg (but I've been proved wrong before:( ). How is your day going???

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> Ya--I didn't forget that--just have a "hunch" that the problem is with nVidia, not Xorg (but I've been proved wrong before:( ). How is your day going???

OK....well the key issue is to identify challengies.....

In this case its 50/50 where the cause can be...:)
Not a big deal other then "**its a bug**"... at least for me.

I have done some house cleanings...:P):P

And study some articles about Windows 7...:twisted:
too many Baghdad Bob writings among open source people, scary....

---

### Post by tghe-retford on 2008-12-21
Someone appears to have taken the initiative and posted a bug report on the cursor problem in Firefox:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/310020](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/310020)

---

### Post by autocrosser on 2008-12-21
> **plun said:**
> OK....well the key issue is to identify challengies.....

In this case its 50/50 where the cause can be...:)
Not a big deal other then "**its a bug**"... at least for me.

I have done some house cleanings...:P):P

And study some articles about Windows 7...:twisted:
too many Baghdad Bob writings among open source people, scary....


Well--It's a xorg issue---- daemon.log info:

Dec 20 22:24:05 linux gdm[13027]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

So I know where the bug "should" go--I'll recheck today, I just got more xorg updates & maybe the issue is moot now (image of crossed fingers)

Send me the Windows 7 links--I need a good laugh!!!!

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> Well--It's a xorg issue---- daemon.log info:

Dec 20 22:24:05 linux gdm[13027]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

So I know where the bug "should" go--I'll recheck today, I just got more xorg updates & maybe the issue is moot now (image of crossed fingers)

Send me the Windows 7 links--I need a good laugh!!!!

OK.... maybe someone freaks out but [Paul Thurroth]("http://www.winsupersite.com/win7/win7_m3_6956.asp") got a lot...  :tongue:

GDM also hanged for me so I reinstalled my system a few days ago....but it was a total hang.  No problem with /home on a separate partition...

---

### Post by ronacc on 2008-12-21
someone else filed a bug before I had a chance so I added comments .This doesn't affect me all that much because Opera is my "normal" browser but still if it does turn out to be endev or xorg itself who knows where it will bite next , best to squash it early  .

---

### Post by plun on 2008-12-21
> **ronacc said:**
> someone else filed a bug before I had a chance so I added comments .This doesn't affect me all that much because Opera is my "normal" browser but still if it does turn out to be endev or xorg itself who knows where it will bite next , best to squash it early  .

OK... I also tested with FF3.1 beta 3, nightly build and its better. Not perfect...

Opera 10 is perfect...:)

---

### Post by autocrosser on 2008-12-21
> **plun said:**
> OK.... maybe someone freaks out but [Paul Thurroth]("http://www.winsupersite.com/win7/win7_m3_6956.asp") got a lot...  :tongue:

GDM also hanged for me so I reinstalled my system a few days ago....but it was a total hang.  No problem with /home on a separate partition...


Ho-Hum--looks like a "slightly" tweaked Vista--You'd think that Redmond could at least keep up with us:P:P:P

I've not looked at the rest of my logs & have not played any full-screen games yet today...so I'll post if that bug is gone or not a bit later......

---

### Post by autocrosser on 2008-12-21
> **plun said:**
> OK... I also tested with FF3.1 beta 3, nightly build and its better. Not perfect...

Opera 10 is perfect...:)

I slowed down my cursor & have seen 0 problems--using the "stable' 3.1 beta2 release.

---

### Post by autocrosser on 2008-12-21
Pinned down to a xorg bug--had the same problem after the desktop resized after I finished a full-screen game (Prey) & then went to FF 3.1--had a instant GDM restart.

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> Pinned down to a xorg bug--had the same problem after the desktop resized after I finished a full-screen game (Prey) & then went to FF 3.1--had a instant GDM restart.

Are you getting any Bonobo crash reports ?

Also is SLI enabled ?  According to rumours this driver just have a basic support for Xorg 1.6

A real nVidia crash report would also probably be great
but... tty is broken and  howto **startx -- -logverbose 6**:confused:

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

---

### Post by autocrosser on 2008-12-21
Ya--I'm using SLI & I realized that any bug would most likely be invalid due to the ABI mis-match--If I wait until (I guess) the cache to "flush", I can use FF without a problem--So I'll just keep a eye on when/how it happens & when the ABI clears up--if things are still happening, file then---

No Bonobo crash reports--just the cryptic GDM line--that is all I've found so far.....

Hate to do it this way, but I'm not sure if it's just a unstable element of the driver or ?????

Your thoughts?

---

### Post by plun on 2008-12-21
> **autocrosser said:**
> Ya--I'm using SLI & I realized that any bug would most likely be invalid due to the ABI mis-match--If I wait until (I guess) the cache to "flush", I can use FF without a problem--So I'll just keep a eye on when/how it happens & when the ABI clears up--if things are still happening, file then---

No Bonobo crash reports--just the cryptic GDM line--that is all I've found so far.....

Hate to do it this way, but I'm not sure if it's just a unstable element of the driver or ?????

Your thoughts?

Well, with a nvidia report it would be easier but howto enable this log when tty is broken ??

Or just disable SLI and test....

Its "rock solid" for me.. rather perfect with my "bling".

---

### Post by caryb on 2008-12-21
> sudo apt-get install nvidia-glx-180

I don't think so....

root@stinkpad:~# apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  xorg xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-fbdev xserver-xorg-video-nv
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed:
  nvidia-glx-180
0 upgraded, 1 newly installed, 12 to remove and 1 not upgraded.
Need to get 16.6MB of archives.
After this operation, 44.6MB of additional disk space will be used.
Do you want to continue [Y/n]?


Cary

---

### Post by ronacc on 2008-12-21
try a different repo the ones that are being removed should be replaced by later packages .
EDIT: maybe you need the ppa version of 180 see earlier in this thread .

---

### Post by LordVeovis on 2008-12-21
> **ronacc said:**
> try a different repo the ones that are being removed should be replaced by later packages .
EDIT: maybe you need the ppa version of 180 see earlier in this thread .

I have currently installed the 180 using the PPA mentioned above, when I updated I didn't have any problems... but it may not have upgraded my xorg to the newer version... will check and post back.

EDIT: ya still on 1.5   How much will break if U upgrade? should I not?
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

---

### Post by ShirishAg75 on 2008-12-21
still not go. Did updates yesterday, no change, still huge keyboard delay issues. Would try today with changing gdm.conf so I'm automatically signed in.

---

### Post by LordVeovis on 2008-12-21
Also wanted to ask if anyone else has seen a problem with the desktop going away?  I noticed this after I installed the 180 and ran updates.  When first booted they will be there, but after a while all my icons go away.  Is that a separate bug, or just user settings / error.  If it is a bug, is it known / unknown?

---

### Post by ronacc on 2008-12-21
see post #83 this thread , did you add ignoreabi to your xorg.conf ? my xserver-xorg shows as 1:7.4~5ubuntu8 .strangely nvidia-settings shows the server as 1:5.99.3   .

---

### Post by LordVeovis on 2008-12-21
> **ronacc said:**
> see post #83 this thread , did you add ignoreabi to your xorg.conf ? my xserver-xorg shows as 1:7.4~5ubuntu8 .strangely nvidia-settings shows the server as 1:5.99.3   .

I added
```

Section "ServerFlags"
	Option "IgnoreABI" "True"
EndSection

```

I ran
```

X -version

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present

```

---

### Post by caryb on 2008-12-22
Thanks Guys I added the PPA to my sources.list & installed the latest Nvidia driver, It fixed all of my problems including a KDE4 problem that I didn't realise related.


Cary

---

### Post by ronacc on 2008-12-22
you are several kernel versions behind , here is the same output from my system
```
ron@ron-desktop3:~$ X -version

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.3
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux ron-desktop3 2.6.28-3-generic #4-Ubuntu SMP Fri Dec 12 22:47:31 UTC 2008 x86_64
Build Date: 17 December 2008  03:13:46AM
xorg-server 2:1.5.99.3-0ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

---

### Post by DougieFresh4U on 2008-12-22
I did all the xserver-xorg updates today.(I have the Intel865G graphics). When I rebooted, it booted into the intel driver instead of vesa. I am also using the latest kernel (.3) The problem I am having is that once desktop loads, it will 'lock up'. The only thing I can do is move mouse around but clicking on any thing brings zilch. I am forced to do a hard shut down. Then boot back up again. Some times I have been able to get as far as opening 'Opera' browser, then the freeze/lock up. I did manage to get log open once before lock up and it shows using the Intel graphics driver.
I am currently using Intrepid live cd.
Any one using Intel having this issue as well? I do know that they are working on Intel some more. So waiting this out until updates for Intel sounds like a good idea, or is there some thing else causing this freeze/lock up problem?
Any input from any one would be most appreciated.
Also, how can I get it to use the 'vesa' instead of Intel? Of course this would only be used until the Intel driver is fixed correctly.

---

### Post by ronacc on 2008-12-22
I cant help you there the only thing I have with intel graphics is my EEE and it s still on intrepid , I haven't got the guts to try a dev version on it :lolflag:

---

### Post by mattduckman on 2008-12-22
> **DougieFresh4U said:**
> The problem I am having is that once desktop loads, it will 'lock up'.

My computer locked up once today, but it was after many hours of use, and I think it was from my Bluetooth mouse, but I need to investigate it more.

Anyway, if you have a Bluetooth adapter on your computer, you might want to try turning it off and see if that helps at all.

EDIT: Can't you access your logs using either the recovery mode, another install, or a live CD?

---

### Post by LordVeovis on 2008-12-22
> **ronacc said:**
> you are several kernel versions behind , here is the same output from my system


How can I update to that then?  When i run it in command line it says there is nothing to update

---

### Post by ronacc on 2008-12-22
> **LordVeovis said:**
> How can I update to that then?  When i run it in command line it says there is nothing to update

sorry it took awhile to get back , gotta sleep some time :)how did you get to Jaunty ? update from Intrepid or install from alpha ? also if you are multiboot on which install is your grub ? Look in synaptic and see what is the latest kernel that is showing there and check your sources.list to make sure they are set correctly then look at your /boot and see what the latest kernel is there . If you are multiboot and your grub meunu.lst is on the other install it wont update to reflect the latest kernel automaticly and you will have to hand edit it.

---

### Post by DougieFresh4U on 2008-12-22
In reference to my post (#132)in this thread.
I was able to boot up and get a desk top this morning, open terminal and run updates. I saw there were 3 updates for 'xserver-xorg'. Well got all updates downloaded and then during the unpacking process it froze up. Before it froze up, screen would go all distorted and then straighten out, but I guess it ended up being to much for it to handle. So a hard shut down and was able to boot up to desktop again and open terminal and finished updating/configuring. Then I closed terminal and opened system log, but when log opened it did the 'deep freeze' again. So now I am using an Intrepid Live CD.
Is it the Intel graphics driver causing this or some thing with xserver or xorg?
Any thoughts or suggestions?
I wanted the Intel to work so much and not get those error messeges when booting up, it's like "be careful what you ask for"
Now how can I put it back to 'vesa' so I have a desktop that is not freezing up?

---

### Post by autocrosser on 2008-12-22
> **DougieFresh4U said:**
> In reference to my post (#132)in this thread.
I was able to boot up and get a desk top this morning, open terminal and run updates. I saw there were 3 updates for 'xserver-xorg'. Well got all updates downloaded and then during the unpacking process it froze up. Before it froze up, screen would go all distorted and then straighten out, but I guess it ended up being to much for it to handle. So a hard shut down and was able to boot up to desktop again and open terminal and finished updating/configuring. Then I closed terminal and opened system log, but when log opened it did the 'deep freeze' again. So now I am using an Intrepid Live CD.
Is it the Intel graphics driver causing this or some thing with xserver or xorg?
Any thoughts or suggestions?
I wanted the Intel to work so much and not get those error messeges when booting up, it's like "be careful what you ask for"
Now how can I put it back to 'vesa' so I have a desktop that is not freezing up?


Try the vesa driver & see---I'll bet it is the Intel driver---I'm using the newest nVidia driver with all the xorg updates & only have a full-screen game bug right now....

As far as getting it to use vesa---mount your install in the LiveCD & edit your X11/xorg.conf---find the line for intel & change it to vesa & save the file/reboot

---

### Post by DougieFresh4U on 2008-12-22
> **autocrosser said:**
> Try the vesa driver & see---I'll bet it is the Intel driver---I'm using the newest nVidia driver with all the xorg updates & only have a full-screen game bug right now....

As far as getting it to use vesa---mount your install in the LiveCD & edit your X11/xorg.conf---find the line for intel & change it to vesa & save the file/reboot

Thanks autocrosser
Now forgive my ignorance, but I am not good at knowing how to mount/unmount using live cd.
It would be great if some one could give me a walk through on mounting and accessing  x11/xorg.conf

---

### Post by ShirishAg75 on 2008-12-22
DougieFresh4U, there are two ways to do this :-

a. Slightly harder way

First when you are on the desktop, fire up gnome-terminal using ALT+F2

then in the terminal do a

```
$sudo fdisk -l  
```

It will give a listing of all the paritions and hard disks. 

For e.g. mine is :-

```

$ sudo fdisk -l 
[sudo] password for shirish: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ded0d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         250     2008093+  83  Linux
/dev/sda2             251        2682    19535040   83  Linux
/dev/sda3            2683        9551    55175242+  83  Linux
/dev/sda4            9552        9733     1461915   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48254824

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          18      144553+  83  Linux
/dev/sdb2              19       19457   156143767+   5  Extended
/dev/sdb5              19        2450    19535008+  83  Linux
/dev/sdb6            2451        2574      995998+  82  Linux swap / Solaris
/dev/sdb7            2575       19457   135612666   83  Linux

```

Then let's say you want to mount /dev/sdb2 so do 

```
$ sudo mount /dev/sdb2 /media/disk
```

make sure you have made a directory called disk or whatever name you want in /media . 

b. Another way to do the same is go to Places and see if you get a listing of your hard disk underneath Computer. If its there then click on that partition and it should be mounted. 

Let us know what worked for you.

---

### Post by DougieFresh4U on 2008-12-22
I do see my hardrive under 'computer', but where do I go from there? Alot of things have 'locks' on them.

---

### Post by ShirishAg75 on 2008-12-22
What happens when you right-click on that hard disk, don't you see a mount volume option. What happens when you try to click on that?

---

### Post by LordVeovis on 2008-12-22
> **ronacc said:**
> sorry it took awhile to get back , gotta sleep some time :)how did you get to Jaunty ? update from Intrepid or install from alpha ? also if you are multiboot on which install is your grub ? Look in synaptic and see what is the latest kernel that is showing there and check your sources.list to make sure they are set correctly then look at your /boot and see what the latest kernel is there . If you are multiboot and your grub meunu.lst is on the other install it wont update to reflect the latest kernel automaticly and you will have to hand edit it.

I D/Led the alpha alternate CD (likely alpha 1) and installed to a fully encrypted system (all but /boot of course) root is on a HW raid, along with /boot (separate unencrypted, bootable partition.) My swap and my /home is on a separate encrypted drive.  Not sure what you meant by " Look in synaptic and see what is the latest kernel that is showing there..." but according to dmesg I have:
```

Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)

```
Non multiboot system also.

EDIT:
As for sources.list, it looks ok to me, but honestly haven't done too much with sources.list before

---

### Post by ronacc on 2008-12-22
open synaptic and search on linux-image ( use the search button not the quicksearch box) and that will show you both avaiable and installed kernel images installed ones are marked green , if a later kernel is installed than 2.6.27-7 ( there can be more than one) then your /boot/grub/menu.lst isnt updating for some reason . how are you doing your updates ?

---

### Post by LordVeovis on 2008-12-23
> **ronacc said:**
> open synaptic and search on linux-image ( use the search button not the quicksearch box) and that will show you both avaiable and installed kernel images installed ones are marked green , if a later kernel is installed than 2.6.27-7 ( there can be more than one) then your /boot/grub/menu.lst isnt updating for some reason . how are you doing your updates ?

No, it is 2.6.27-7 as well.

I normally do it in a terminal window
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by caryb on 2008-12-23
One of the things I have found is when there is a kernel update grub asks if you if you want the maintainers copy or the local copy, if you select local grub does not update the menu although the kernel is installed.


Cary

---

### Post by ShirishAg75 on 2008-12-23
carryb, that is correct. What I do is update the maintainer's copy and then edit out stuff which I don't want. That is the way of legacy.

---

### Post by ronacc on 2008-12-23
> **LordVeovis said:**
> No, it is 2.6.27-7 as well.

I normally do it in a terminal window
```

sudo apt-get update
sudo apt-get upgrade

```

post your /etc/apt/sources.list

---

### Post by obsrv on 2008-12-23
This is what I was looking for! Thanx a lot! You ROCK!

---

### Post by alexv75 on 2008-12-23
> **plun said:**
> Yup... it might be so but 180.16 supports VDPAU better...

Now i'm using the new 180.18 driver (which must have the same or better support for VDPAU) and my 2d performance is even better (firefox switches tabs faster and the desktop feels overall snappier than before) :D. On the other hand my current GPU doesn't support VDPAU so it's dead weight for me so to speak ^^.

/off+rant
I want to congratulate myself on the fact that after months of mental preparation now i have completely removed all micro$oft bloatware (i refer to vista which was eating 13gb of my disk ^^) and installed ubuntu on all my home pc-s :p.
So far everything is good in heaven, except the fact i can't play my games... Damn alsa and pulseaudio!

---

### Post by plun on 2008-12-23
> **alexv75 said:**
> Now i'm using the new 180.18 driver (which must have the same or better support for VDPAU) and my 2d performance is even better (firefox switches tabs faster and the desktop feels overall snappier than before) :D. On the other hand my current GPU doesn't support VDPAU so it's dead weight for me so to speak ^^.

/off+rant
I want to congratulate myself on the fact that after months of mental preparation now i have completely removed all micro$oft bloatware (i refer to vista which was eating 13gb of my disk ^^) and installed ubuntu on all my home pc-s :p.
So far everything is good in heaven, except the fact i can't play my games... Damn alsa and pulseaudio!

Ok... Congrats...:D

I am looking for a new card and all Vista users can buy all expensive ones...

Zine, Mplayer and now VLC supports VDPAU...
[http://www.phoronix.com/scan.php?page=news_item&px=Njk1NA](http://www.phoronix.com/scan.php?page=news_item&px=Njk1NA)


PulseAudio is a challenge and hopefully it will be resolved in Jaunty.

psyke83's guide is just great !
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by ShirishAg75 on 2008-12-23
Another round of xserver-xorg-video-* seems to be in the offing. Although these are being built against xserver 1.5, all of them.

---

### Post by DougieFresh4U on 2008-12-23
> **ShirishAg75 said:**
> Another round of xserver-xorg-video-* seems to be in the offing. Although these are being built against xserver 1.5, all of them.

Any word on something for 'Intel'.
I am hanging in there and dealing with 'freeze/lock-ups'
At least when I boot up and get to a desktop, I can open a terminal and do updates, as it hasn't locked up when using terminal. I did manage to get 'System Monitor' open for a few before freeze'lock up and CPU was very low which is good. 
So for time being I use live cd (this is not my maim machine)

EDIT: Just checked and nothing for Intel

---

### Post by LordVeovis on 2008-12-23
> **ronacc said:**
> post your /etc/apt/sources.list

/etc/apt/sources.list as follows.

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha amd64 (20081122)]/ jaunty main restricted                                                                   

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha amd64 (20081122)]/ jaunty main restricted                                                                   
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to       
# newer versions of the distribution.                                           

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties                                              

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties                                      

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb http://archive.ubuntu.com/ubuntu/ jaunty universe                      
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe              

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main

```

When I update via a terminal it does tell me 101 not upgraded:
```

The following packages have been kept back:
  brasero capplets-data compiz-core compiz-gnome compiz-plugins deskbar-applet
  ekiga f-spot gedit gedit-common gnome-applets gnome-applets-data
  gnome-control-center gnome-panel gnome-screensaver gnome-settings-daemon
  gnome-utils gtk2-engines-pixbuf libcanberra-gtk0 libcanberra0 libeel2-2
  libflickrnet2.1.5-cil libglade2.0-cil libglib2.0-cil
  libgnome-window-settings1 libgnomecanvas2-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtkhtml3.14-19 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono1.0-cil libmono2.0-cil libndesk-dbus1.0-cil linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  mono-common mono-gac mono-jit mono-runtime nautilus python-glade2
  python-gnome2-desktop python-gobject python-gtk2 tomboy tracker
  tracker-search-tool tracker-utils ubuntu-desktop xserver-xorg
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.

```

EDIT: Added more.

---

### Post by ronacc on 2008-12-23
@ LordVeovis Your sources.list is ok ,I wonder why all those packages are being held back ? and I see a kernel update in there , are you sure they aren't showing in synaptic ? try hitting the reload button in synaptic and see if they show up , it should pick them up from the apt-get update but maybe it isn't for some reason . also you could try ```
 sudo apt-get dist-upgrade 
``` just look carefuly at what it wants to do before you accept it , if it wants to remove something vital without replacing it be careful , you could also use synaptic > status > upgradeable and select packages one (or a few) at a time and that will tell you what is blocking that package(s) but with 101 held back that would take awhile .

---

### Post by LordVeovis on 2008-12-24
> **ronacc said:**
> ... also you could try ```
 sudo apt-get dist-upgrade 
``` just look carefuly at what it wants to do before you accept it

I wasn't sure about one of the packages, so i looked it up and it was ok.  It installed the 101 that were held back, and other packages as well.  It worked.  I have the proper versions now.  I guess it might be that I had started with the alpha 1 CD 2 days or so before the alpha 2 release.  I thought it would still update to it.  Guess not:confused:

---

### Post by ronacc on 2008-12-24
sometimes update manager or apt  gets upset about something insonsequential and it takes a dist-upgrade to get things rolling again , its safe as long as you are careful about it and do like you did, when in doubt check .

---

### Post by NeoFax on 2009-01-06
I have installed the 173.14.15 NVIDIA drivers and added the IgnoreABI string to the xorg.conf file as stated previously, but I still cannot get into X as it says the ignoreABI is not being recognized.  So, I added the ignoreABI directly to the GDM.conf file and same problem, cannot get into X.  This is the most problems I have had w/ NVIDIA for a long time.

---

### Post by Gourgi on 2009-01-06
> **NeoFax said:**
> I have installed the 173.14.15 NVIDIA drivers and added the IgnoreABI string to the xorg.conf file as stated previously, but I still cannot get into X as it says the ignoreABI is not being recognized.  So, I added the ignoreABI directly to the GDM.conf file and same problem, cannot get into X.  This is the most problems I have had w/ NVIDIA for a long time.

try to use this PPA [https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive) to install the 180.18 driver.
and keep the ignoreABI option to xorg.conf
that solved my problems

---

### Post by bobya on 2009-01-06
Thanks, I had the same problem and your info helped

---

### Post by ShirishAg75 on 2009-01-08
new radeonhd release coming up. 

```

xserver-xorg-video-radeonhd (1.2.4-1) experimental; urgency=low

  * New upstream release.
  * Add myself to Uploaders.

```

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002707.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002707.html)

---

### Post by NeoFax on 2009-01-08
> **Gourgi said:**
> try to use this PPA [https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive) to install the 180.18 driver.
and keep the ignoreABI option to xorg.conf
that solved my problems

These drivers do not work for my card, FX5200.  I have to use the 173.xx series of drivers.  The development team have not updated yet to the .15 drivers and the .12 ones will not compile on a 2.6.28 kernel.  So I read in this thread someone had gotten the .15 drivers to work with the ignoreabi option, but it simply does not work for me.

---

### Post by emonkey on 2009-01-09
Nvidia released the 180.22 Driver (stable).

Does anybody know something about it? Does it implement the new ABI?

Are there more infos about the following?
"Improved compatibility with recent Linux kernels."
(from [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html))

I know, kernel != xorg ... but is there hope?

---

### Post by plun on 2009-01-09
> **emonkey said:**
> Nvidia released the 180.22 Driver (stable).

Does anybody know something about it? Does it implement the new ABI?

Yup.

I filed a upgrade request about it but I cannot see it.

[https://bugs.launchpad.net/bugs/315169](https://bugs.launchpad.net/bugs/315169)

So I am running Jaunty with a downloaded version from nVidia and ignoreABI added.


Meny System > Hardware drivers (Jockey) is NOT changed.

---

### Post by ShirishAg75 on 2009-01-09
There was just a small xorg update sometime back. 

> 

xorg (1:7.4~5ubuntu10) jaunty; urgency=low

  * apport/source_xorg.py:  Fix arg list to prevent error
    'Error: Cannot open display ":0 -"'
    (LP: #311442)


---

### Post by platykurtic on 2009-01-18
I'm on X Server 1.5.99.901, with the nvidia drivers 180.22, and I get can't enable compiz. Any ideas?

---

### Post by LordVeovis on 2009-01-18
> **platykurtic said:**
> I'm on X Server 1.5.99.901, with the nvidia drivers 180.22, and I get can't enable compiz. Any ideas?

Start a new thread with this... and also what does it say when you try?

Launch by command line.

```
compiz --replace
```

---

### Post by gspat on 2009-01-18
> **emonkey said:**
> Nvidia released the 180.22 Driver (stable).

Does anybody know something about it? Does it implement the new ABI?

Are there more infos about the following?
"Improved compatibility with recent Linux kernels."
(from [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html))

I know, kernel != xorg ... but is there hope?

I'm using it right now, seems to work well enough...

make sure you set the serverflag!

---

### Post by DougieFresh4U on 2009-01-18
Maybe this does not belong in this thread, but any thing good going on with 'Intel' yet?
Just wondering as I still can not get a stable desktop with out those little adjustments to 'xserver' and also I have no Direct Rendering.

---

### Post by vikrant82 on 2009-01-19
Struggling here too with Intel 915GM. So what have been these adjustments, DougieFresh4U ? 

I am on the crappy 'vesa' driver. Leave apart compiz, have been fasting even on videos. Another thing, that happens here is, entire X hangs, once I click on that volume applet.  A drop down appears and finally X hangs with a black placeholder for that dropdown. 

Anyone else experiencing anything similar?

---

### Post by DougieFresh4U on 2009-01-19
> **vikrant82 said:**
> Struggling here too with Intel 915GM. So what have been these adjustments, DougieFresh4U ? 

I am on the crappy 'vesa' driver. Leave apart compiz, have been fasting even on videos. Another thing, that happens here is, entire X hangs, once I click on that volume applet.  A drop down appears and finally X hangs with a black placeholder for that dropdown. 

Anyone else experiencing anything similar?
 
Put this in file:
[B]```
/etc/X11/xorg.conf

Section "Device"
Identifier "Configured Video Device"
Driver "Intel"
Option "NoAccel" "true"
EndSection
```
Good luck

---

### Post by vikrant82 on 2009-01-21
Doesnt work sticking to

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

---

### Post by AaronP_ on 2009-01-21
I just got word from the X.org folks that I can consider ABI 5 finalized, so I removed the ABI checks and the next round of releases will no longer require -ignoreABI.

Please note that as various people mentioned, we don't support systems running development snapshot X servers with the ABI checks disabled.

---

### Post by DougieFresh4U on 2009-01-21
> **AaronP_ said:**
> I just got word from the X.org folks that I can consider ABI 5 finalized, so I removed the ABI checks and the next round of releases will no longer require -ignoreABI.

Please note that as various people mentioned, we don't support systems running development snapshot X servers with the ABI checks disabled.

Any news about 'Intel'?

---

### Post by adult swim on 2009-01-23
the latest updates broke my X on intel 945

---

### Post by mrjohnston on 2009-01-23
My x4500 is broken too as of last update of X.

---

### Post by tepsipakki on 2009-01-23
The intel breakage is not related to this thread.

That said, you can get around it by downgrading libdrm2 & libdrm-intel1. Once the new xserver-xorg-video-intel is available on the archive you are safe to upgrade again. Unfortunately one of the amd64 build-daemons is broken at the moment, so the new mesa & -intel are not built yet.

---

### Post by Starks on 2009-01-23
I'm not a big fan of the fact that current intel drivers (repo and ppa) tend to occasionally stutter while using VGA output from a laptop.

---

### Post by Tich666 on 2009-01-23
I've been getting acceptable results with the [xorg-edgers ppa](https://launchpad.net/~xorg-edgers/+archive) for my 4500MHD, using UXA:
about 550fps in glxgears, compiz runs smooth and I can even play youtube videos in fullscreen!

I used to get 150fps in intrepid with the default drivers and the ones from jaunty (2.5.1) but 2.6.0 has been a significant improvement for me.

The drivers from the ppa also work with the very latest updates and kernel (2.6.28-5)

---

### Post by Starks on 2009-01-24
Is the PPA driver still newer?

Also, why are the drivers still so slow?

---

### Post by plun on 2009-01-31
X-server fixes, RC2 out

Also upgraded for Jaunty today

[http://www.phoronix.com/scan.php?page=news_item&px=NzAyOA](http://www.phoronix.com/scan.php?page=news_item&px=NzAyOA)

> **X Server 1.6.0 RC2 Finally Makes It Out The Door**
Posted by Michael Larabel on January 31, 2009
X Server 1.6 was supposed to be out nearly a month ago, but today we are finally getting closer to nearing this much anticipated release. Intel's Keith Packard has announced the second release candidate for X Server 1.6.0. The RC2 release is arriving almost three weeks after the first release candidate was made available. Fixed in this release is a few RandR and input changes, but a majority of the work deals with Apple's XQuartz in the server.

It looks like we will now see the final release of X Server 1.6.0 in early February. X Server 1.6.0 introduces RandR 1.3, Direct Rendering Infrastructure 2, Predictable Pointer Acceleration, and other improvements.

Maybe time for a reboot and check....;)

---

### Post by vikrant82 on 2009-01-31
Intel 915GM works .. Yipppee!!! :popcorn:

Compiz works like ever .. :D

---

### Post by iamkrazee on 2009-03-30
Not quite :S Broken in Jaunty !

---

### Post by zevans on 2009-03-31
> **iamkrazee said:**
> Not quite :S Broken in Jaunty !

The xserver-xorg-core yesterday (or day before?) broke mine too - the RandR API broke completely so I was stuck on 640x480x60Hz - ouch! Using xrandr, krandrtray, or the KDE settings all caused a server reset.

It's fixed now - 
xserver-xorg-core 
2:1.6.0-0ubuntu7

so if I were you I'd fire up synaptic this morning. :)

---

### Post by nawitus on 2009-04-22
I upgrade to 9.04 succesfully, but now I've got this problem and my system is broken :/. If I try to install nvidia-glx, the xserver will get removed.. and vice versa.

---

