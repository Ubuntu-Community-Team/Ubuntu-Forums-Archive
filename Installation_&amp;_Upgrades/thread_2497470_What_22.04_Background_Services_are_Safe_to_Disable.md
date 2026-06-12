---
title: "What 22.04 Background Services are Safe to Disable + Login Screen Turns Black"
date: 2024-05-06
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2024-05-06
After previous problems upgrading / installing 22.04 (fresh install) see here: [https://ubuntuforums.org/showthread.php?t=2497163]("https://ubuntuforums.org/showthread.php?t=2497163")  There were many issues including activating Ubuntu Pro then computer fails to Start !!!

And thinking I had resolved the problem ... alas I did not. After several days of successful boots, I now get part of the same problem as before.
Upon booting and Login Screen shows ... first key pressed and screen goes BLACK. Have to hard Reset / Reboot and pray I can login to my system.

After a luckily successful Boot-up, I bring up Startup and Shutdown / Background Serves.  I notice several things Running that I don't need. Such as;

Bluetooth ( Don't have bluetooth availability on my Desktop)
Free Space Notifier (will never happen on my 1TB SSD )
Touchpad  (this is a Desktop, there is No Touchpad and NEVER will be)
Keyboard Layout ( most will NEVER switch their keyboard layout)
Network Proxy Config ( I have no Proxy)
Wacom Tablet  (as if this OS is confused, wasting valuable resources)
SMB Watcher (have no link or connection to a SMB)
Search Folder Updater (could care less)
Remote URL Change Notifier ( really?!?! )
Write Daemon ( I am the  ONLY user, local users would be for Server or whatever )

Logic would dictate all of the above Services can be deactivated / switched off safely, less they run forever for No Reason. 
But unsure which is causing 22.04 to fail to Boot correctly (Grub didn't show, now shows) or be able to Login!?!?!

I suspect it is Thunderbolt Device Manager. Since this has something to do with PCI Express which is where my GPU is plugged into, and there 
are issues with my ASUS Nvidia GeForce GT610 w/2GB DDR3 Ram, PCI Express 2.0 (running 2 monitors) and Nvidia Driver 390 with 22.04. 
Whereas in System Settings / Driver Manager / Software Sources / Additional Drivers shows Using X.Org X Server Nouveau display driver 
and not Nvidia driver 390 (proprietary, tested).

Questions:

1. How can I trouble shoot my Login Screen turning my monitors BLACK and computer unable to respond?!!?

2. And which Background Services can we "safely" turn off in our Desktop Environment (otherwise is it just poke and hope for everyone) ???

3. Is it safe to allow X.org X server as Nvidia GPU Driver rather than Nvidia driver 390 (no longer supported) ???

Thanks for any feedback, and hope this helps others.

By the way ... after logging into UbuntuForums; it Failed to go into the Forums and posted an Error Msg. Upon attempting , via Contact Us, to notify of the problem,
received Wrong URL under your Contact / help page [https://forms.canonical.com/sso-support/]("https://forms.canonical.com/sso-support/") "The requested URL /sso-support/ was not found on this server.". Maybe whoever reads this can get it to the right person (webmaster).

---

### Post by currentshaft on 2024-05-08
ho hey

---

### Post by Rick St. George on 2024-05-08
> **currentshaft said:**
> 

Boot into recovery mode at grub, or if you can get past grub but don't get a graphical interface, try control-shift-F1 through F7. If all else fails, boot to a live Ubuntu image and repair the file system from there.


Grub Menu does not show. In my previous thread (see link in 1st sentence above) I could hold SHIFT key down and a BLANK Grub Menu would come up. Haven't needed or tried it this time (after another FRESH Install from USB stick, and I'm not doing it again).

What I've noticed is that upon Boot-up, my Num Lock light will go off and on. When Login Screen shows ... it is off. When I hit the Num Lock key, the light of course comes on and the Login Screen stays up for me to be able to Login. If I don't press Num Lock key at the right time, the screen goes BLACK / BLANK and I can't do anything else but hit the RESET button to ReStart the computer. 

Does this tell anyone what is happening, or what is going on? I have saved to a file, relevant parts of the Boot Fail Log but is lengthy to post ... if it would help!

Thanks for any and all replies.

---

### Post by TheFu on 2024-05-09
I routinely disable services/programs that I don't use.  OTOH, if something bad happens, I re-enable it FAST!  LVM snapshots makes this effort easy.

Running extra code that you don't use is a liability. It is more code with more bugs.  

If your system isn't stable, I'm inclined to think there is either a hardware or OS setting problem.  Check the system logs for hardware issues, research each, decide if they are important or not, correct each.  Sometimes old hardware breaks - like 10+ yr old GPUs.  I had a GPU that was failing prevent boots from working.  The only way I discovered it was by replacing the GPU and not seeing any more issues.  I  can only guess there was a short in the GPU card, somewhere.  Also, I had an older, spare, GPU laying around, so it wasn't too hard to test a different one.

Troubleshooting issues from a Try Ubuntu Flash drive (the installer/boot flash you made) is common when there are issues.  If that environment is stable and working, then it isn't likely a hardware issue. Look at your personal and system settings.

---

### Post by Rick St. George on 2024-05-09
> **TheFu said:**
> I routinely disable services/programs that I don't use.  OTOH, if something bad happens, I re-enable it FAST! 
 LVM snapshots makes this effort easy.
> 

I'm familiar with VirtualBox Snapshots .... but what is LVM?

[QUOTE]
If your system isn't stable, I'm inclined to think there is either a hardware or OS setting problem.  


I've been through all the Personal and OS Settings I can find, under MENU. Not used any commands tactics.

[QUOTE] 
Troubleshooting issues from a Try Ubuntu Flash drive (the installer/boot flash you made) is common when there are issues.  If that environment is stable and working, then it isn't likely a hardware issue. Look at your personal and system settings.

I don't have a spare GPU to fit a PCIexpress Slot. It may be worth buying ... will report back afterwards.

Thanks FU  ):P

---

### Post by TheFu on 2024-05-09
> **Rick St. George said:**
> 
I'm familiar with VirtualBox Snapshots .... but what is LVM?


Do some research. It isn't something to be added after-the-fact.  It needs to be chosen as part of the install - - - or better, customized pre-install, then tell the installer about your LVM layout during install.  Sadly, 24.04 broke LVM in the installer. It is ugly now.
[https://en.wikipedia.org/wiki/Logical_volume_management](https://en.wikipedia.org/wiki/Logical_volume_management) is an overview.  To my knowledge, there are 3 methods to have snapshots.
LVM, BTRFS, ZFS.  I haven't touched VirtualBox in so long that I don't recall if their snapshots are real or fake.  There are lots of fake uses of the "snapshot" term, especially with some backup tools incorrectly using it.

> **Rick St. George said:**
> 
I've been through all the Personal and OS Settings I can find, under MENU. Not used any commands tactics.

I don't know how to do OS settings with a GUI.  I doubt any GUI provides sufficient control.

> **Rick St. George said:**
> I don't have a spare GPU to fit a PCIexpress Slot. It may be worth buying ... will report back afterwards.

GPUs aren't cheap like they were 15 yrs ago.  It might make more sense to switch to a new CPU+motherboard that has an iGPU than to find a "cheap" $130 low-end GPU.  Only you can decide.  I swapped out a Ryzen 2600 + nVidia 1030 GT setup for a Ryzen 5600G that is 40% faster and the iGPU is faster than the nVidia 1030 GT (it was 4-6 yrs newer, so that makes sense).  The iGPUs today will put your GPU to shame.

If a new Ryzen 5600G + Motherboard + 16GB of RAM is under $220, that's a great deal.  I haven't been watching prices for a while.  I paid $120 for the CPU a few years ago.  MB runs between $50 and $140, so there's a wide range of options.  DDR4 RAM isn't going to get any cheaper than it is today, unless you can find someone to give you their old RAM.  I have 16GB of G.Skill DDR4 3200 RAM laying around that needs a home, but I'd want $45 for it, so it isn't a good deal.  I paid $120 for it, I think.

Soon, DDR4 RAM will be hard to find and prices will increase for used RAM. That's how RAM pricing works.

---

### Post by Rick St. George on 2024-05-09
FYI, found this interesting, and if I run into the same problem again, will try this remedy and report back.

> 
You will find more details in this launchpad issue [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1990750]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1990750").

When ever facing the black screen issue, then boot in recovery mode however is possible and remove/reinstall the tested drivers.
For the time being this is the commands to apply as it was proposed to me, and it worked:
(obviously replacing driver 525 with your version)


```

$sudo apt-get --purge remove &#8216;nvidia&#8217;
$sudo apt install linux-modules-nvidia-525-generic nvidia-driver-525

```

> 
Please note that I previously reinstalled the system whenever I was having the black screen/blinking cursor, as I did not know there is always a workaround to start up Ubuntu from there, for example do: [CTRL] + [ALT] + [DEL] to regain access to the boot menu, or instead during boot keep pressing on the key that gives you access to the Ubuntu boot menu (&#8216;Shift&#8217; key with my Gigabyte mainboard) to select the recovery mode, or somewhere during boot when the system hangs I could regain control by clicking randomly on the function keys.

Selecting the Nouveau driver will also allow your system to boot normally without the black screen also subsequently allowing you to reinstall the nVidia tested drivers from a normally booted system.

Last but not least as I am updating my system with pre-releases and presently using 20.10 Kinetic, I had recently the same black screen issue after a system update and I had to downgrade to kernel 5.19.0.31.32 from I believe a 5.19.0.35 version (using Mainline).


Retrieved From: [https://discourse.ubuntu.com/t/22-04-nvidia-drivers/28072/27]("https://discourse.ubuntu.com/t/22-04-nvidia-drivers/28072/27")

---

### Post by Rick St. George on 2024-05-17
> **currentshaft said:**
> 

Boot into recovery mode at grub, or if you can get past grub but don't get a graphical interface, try control-shift-F1 through F7. If all else fails, boot to a live Ubuntu image and repair the file system from there.


Grub does not come up. Login shows briefly ... then everything goes BLACK. Control shift F1 - 7 does nothing. This is a Fresh Install. Why would I Re-install a 3rd time?!?!?

v20.04 worked fine. A fresh install of v22.04 FAILS. Obviously something is wrong with v22.04 and yet they are moving on and creating 24.04. The posts are full of people having trouble with both! 

If I go back to 20.04, which worked fine, it is not being supported. So what choice do we have but to ask for help in solving these issues? But, best I can get is ... Buy a new computer?!?!?

To say I am frustrated pales in comparison to the vulgar things coming out of my mouth these past few weeks trying to make UbuntuStudio boot up! 

Hate to say it ... I may have to give up.

---

### Post by Rick St. George on 2024-05-17
One more time ... Here is the Error I'm getting when attempting Update after Fresh Install of v22.04.

```

2 packages can be upgraded. Run 'apt list --upgradable' to see them.

~$ apt list --upgradable
Listing... Done
python3-update-manager/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.18]
update-manager-core/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.18]
stephen@stephen-ms7640:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.15.0-106 linux-headers-5.15.0-106-generic
  linux-lowlatency-hwe-6.5-headers-6.5.0-17
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-6.5.0-17-lowlatency linux-image-6.5.0-17-lowlatency
  linux-modules-6.5.0-17-lowlatency
The following packages have been kept back:
  python3-update-manager update-manager-core
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 639 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 531613 files and directories currently installed.)
Removing linux-headers-6.5.0-17-lowlatency (6.5.0-17.17.1.1.1~22.04.1) ...
Removing linux-image-6.5.0-17-lowlatency (6.5.0-17.17.1.1.1~22.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-17-lowlatency
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-35-lowlatency
Found initrd image: /boot/initrd.img-6.5.0-35-lowlatency
Found linux image: /boot/vmlinuz-6.5.0-35-lowlatency
Found initrd image: /boot/initrd.img-6.5.0-35-lowlatency
Found linux image: /boot/vmlinuz-6.5.0-28-lowlatency
Found initrd image: /boot/initrd.img-6.5.0-28-lowlatency
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-modules-6.5.0-17-lowlatency (6.5.0-17.17.1.1.1~22.04.1) ...
Setting up nvidia-dkms-390 (390.157-0ubuntu0.22.04.2) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.157 DKMS files...
Deleting module nvidia-390.157 completely from the DKMS tree.
Loading new nvidia-390.157 DKMS files...
Building for 6.5.0-35-lowlatency
Building for architecture x86_64
Building initial module for 6.5.0-35-lowlatency
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-390.0.crash'
Error! Bad return status for module build on kernel: 6.5.0-35-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia/390.157/build/make.log for more information.
dpkg: error processing package nvidia-dkms-390 (--configure):
 installed nvidia-dkms-390 package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on nvidia-dkms-390 (<= 390.157-1); however:
  Package nvidia-dkms-390 is not configured yet.
 nvidia-driver-390 depends on nvidia-dkms-390 (>= 390.157); however:
  Package nvidia-dkms-390 is not configured yet.

dpkg: error processing package nvidia-driver-390 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                 Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-35-lowlatency
Errors were encountered while processing:
 nvidia-dkms-390
 nvidia-driver-390
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Can this be safely ignored? Forget the Nvidia 390 driver? Stop using Terminal Commands? Let the OS Software Updater do its thing?
This has got me running in circles! Sometimes it boots-up, sometimes it does not! And upon Reboot, system hangs at Mobo Screen ... No Login Screen at all. Can't Boot, Can't Login, Can't USE it.
Any feedback?

---

### Post by currentshaft on 2024-05-17
Sorry, I mispoke, it's Control-Alt-F1 through F7. You may need to hold the Function (Fn) key on your keyboard to access the F keys.

---

### Post by Rick St. George on 2024-05-17
> **currentshaft said:**
> Sorry, I mispoke, it's Control-Alt-F1 through F7. You may need to hold the Function (Fn) key on your keyboard to access the F keys.

May have been F3 that brought me to a prompt login. Logged in ... now am at a prompt and don't know what to do next?!?!?

---

### Post by Rick St. George on 2024-05-17
From my previous (same) issue, see URL at first post;

Posted by MAFOElfen
Nvidia 390 is no longer supported by NVidia, but is still being patched by the Ubuntu Graphics Team. My Lenovo Thinkpad T520 uses this driver...

Try this:
```


sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install -y nvidia-graphics-drivers-390

```

I get this "Unable to locate package nvidia-grahics-drivers-390".  Used "nvidia-driver-390" instead and received same Dpkg Error Code (1) from previous failure (see post #9).



Still can't boot, still at prompt.

---

### Post by Rick St. George on 2024-05-17
Semi followed instructions found here - [https://www.stephenwagner.com/2019/05/05/ubuntu-linux-black-screen-frozen-system-after-upgrade-install/]("https://www.stephenwagner.com/2019/05/05/ubuntu-linux-black-screen-frozen-system-after-upgrade-install/")

At the prompt edited Grub, Removed quiet and splash and added nomodeset. Update Grub and Rebooted.

Computer boots up but ONLY to 1 monitor and the resolution is not right (1024x768) and cannot change it. What does this mean that it won't recognize my 2nd monitor???
Any ideas???

---

### Post by TheFu on 2024-05-18
> **Rick St. George said:**
>  Any ideas???

Nothing constructive, just that nVidia sucks.  

About 2 yrs ago, I removed nVidia from my last system here.  Things are so much easier.  In my situation, the iGPU in a Ryzen 5600G is faster than the nvidia 1030 GT.  And I'm able to encode hevc and h.264 videos using the iGPU, unlike with the 1030.  The HW-Encoding is fast, but the quality kinda sucks.  Only useful for real-time transcoding, when needed for different devices.  For any archival, handbrake CPU transcoding is much higher quality and lower file size, but takes about 3x longer.

I suppose of your needs require $1000+ nvidia, and you earn a living with those GPUs, then anything less isn't a consideration.  But for middle-of-the-road and low-end GPUs, there's just no need for nvidia and the hassles seem to happen every few months. That was my experience since around 2012-ish.  I'd been using nvideo since the early 2000s.  When they dropped support for my 7200gs and only the F/LOSS drivers were available in 2016, I knew nvidia was just like all other proprietary software vendors.

---

### Post by currentshaft on 2024-05-18
? as

---

### Post by currentshaft on 2024-05-18
au

---

### Post by TheFu on 2024-05-18
currentshaft, Good that you have a $1500+ GPU.  Enjoy.  The most I've ever spent on a GPU was $130 and that was for a 3dfx model.
I had nvidia GPUs for about 15 yrs, so my thoughts that "nvidia sucks" isn't without some basis.  

BTW, I've never personally spent more than $1000 on a full computer, much less just a GPU.  I bought my first computer in the 1980s.  Before that, I use my parent's x86 clone or the school's different computers.  My first $real_job post-University was as a computer programmer.

In 2012, Linus said, "NVIDIA is the Single Worst Company We've Ever Dealt With"
Ref: [https://www.techpowerup.com/167855/nvidia-is-the-single-worst-company-weve-ever-dealt-with-linus-torvalds](https://www.techpowerup.com/167855/nvidia-is-the-single-worst-company-weve-ever-dealt-with-linus-torvalds)

In 2012, I wasn't really having issues, but that time would come. I have a perfectly good GeForce 7200 gs and a 430GT  Tell me how to make either work on Ubuntu 24.04 at 1920x1200, please.  Since nVidia dropped support, their proprietary drivers have not worked.  That's my definition of SUCK.  The F/LOSS drivers only support 768p resolutions, at least at the time and for over 4 yrs.  Then I gave up trying.

Ok, I'll amend my statement, "nVidia sucks for all uses, except high-end needs where the GPU costs 3x more than the rest of the computer".

---

### Post by Rick St. George on 2024-05-19
> **currentshaft said:**
> What happens when you run "startx" at the command line prompt atfter logging in?

```


ms7640:~$ startx

/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console.


```

Note: I am the Only User and with Administrator rights.

This issue may have to do with installation of VirtualBox ... as others [see here]("https://ubuntuforums.org/showthread.php?t=2497812") have the same problem!?!? So... should this moved to VIRTUALIZATION category?

I need to make sure before I pay $100+ for another GPU. This one worked fine for a Decade with UbuntuStudio v18.04 and 20.04.
I'm inclined to believe it is a Software problem (maybe v22.04), either with VirtualBox and/or Nvidia, and not a Hardware problem (I just replaced 10yr old SSD).

Note Build: 
Mobo - MSI 990FXA-GD65 Military Hardened (not overclocked) set for UEFI Boot (confirmed)
CPU - AMD FX-8320 Vishera 8 Core
GPU - ASUS GeForce GT610 2GB DDR3 Ram in PCIe x16 slot
PSU - 450 Watt Enermax Gold
RAM - 2 X 8GB Corsair Vengence DDR3 1600 Mhz
OS - UbuntuStudio-64 v22.04 LTS

---

### Post by Rick St. George on 2024-05-20
PROBLEMS WITH NVIDIA DRIVER DEPENDENCIES
Attempt to Fix.

```

ms7640:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up nvidia-dkms-390 (390.157-0ubuntu0.22.04.2) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.157 DKMS files...
Deleting module nvidia-390.157 completely from the DKMS tree.
Loading new nvidia-390.157 DKMS files...
Building for 6.5.0-35-lowlatency
Building for architecture x86_64
Building initial module for 6.5.0-35-lowlatency
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-390.0.crash'
Error! Bad return status for module build on kernel: 6.5.0-35-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia/390.157/build/make.log for more information.
dpkg: error processing package nvidia-dkms-390 (--configure):
 installed nvidia-dkms-390 package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on nvidia-dkms-390 (<= 390.157-1); however:
  Package nvidia-dkms-390 is not configured yet.
 nvidia-driver-390 depends on nvidia-dkms-390 (>= 390.157); however:
  Package nvidia-dkms-390 is not configured yet.

dpkg: error processing package nvidia-driver-390 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                    Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-35-lowlatency
Errors were encountered while processing:
 nvidia-dkms-390
 nvidia-driver-390
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
=========================

Same Result for;

```

sudo apt-get install libnvidia-ifr1-390 libnvidia-gl-390

```

Already installed, and Loops through Error Msgs.

Same for any other commands. The following is from AI.

> 
The error &#8220;dpkg: dependency problems prevent configuration of nvidia-driver-390 in ubuntu v22.04&#8221; indicates that there are unmet dependencies for the installation of the NVIDIA driver version 390 on Ubuntu 22.04. This can occur when the required dependencies are not installed or are not properly configured.

To resolve this issue, you can try the following steps:

Run the command sudo apt-get install -f to fix any broken dependencies.
Run the command sudo dpkg --configure -a to configure any unconfigured packages.
Check if there are any missing dependencies by running the command sudo apt-get install libnvidia-ifr1-390 libnvidia-gl-390 and install them if necessary.
If the issue persists, try removing any conflicting packages by running the command sudo dpkg-divert --remove <package_name> and then reinstall the NVIDIA driver.
If none of the above steps work, you can try reinstalling the NVIDIA driver by running the command sudo apt-get install nvidia-driver-390 and then configuring it again with sudo dpkg --configure -a.


FAILED AGAIN !!!

-----  After more Research - Tried the Following -----------

```

#Fix missing pkgs
sudo apt-get update --fix-missing

# Unlock
sudo fuser -vki /var/lib/dpkg/lock
# Delete the Lock
sudo rm /var/lib/apt/lists/lock
# Reconfigure Pkgs
sudo dpkg --configure -a
# Install Fixed Pkgs
sudo apt-get install -f
# Clean
sudo apt-get clean
# Remove old pkgs
sudo apt-get autoremove

```

Nothing Works!

Maybe this will remove the Error File and Try to Rebuild/Reinstall

```

ms7640:~$ sudo mv /var/lib/dpkg/info/nvidia-dkms-390* /tmp
ms7640:~$ sudo dpkg --configure -a
Setting up nvidia-dkms-390 (390.157-0ubuntu0.22.04.2) ...
Setting up nvidia-driver-390 (390.157-0ubuntu0.22.04.2) ...

```

System Rebooted, but still ONLY 1 monitor displays.
this is an AOC 27" With Full HD 1920x1080 resolution, HDMI out.
Display settings shows ONLY available at 1024X768 in Weyland Session (whatever that is). Cannot modify!

Apparently, newer Ubuntu version 20.04+ have problems with anything outside of SNAP. Such as Video Drivers, Virtual Machines (at least VirtualBox).
Will have to do more research on difference between Plasma X11 and Plasma Weyland (which refuses to accept Nvidia).

Sooo...  one must know what GPUs are now currently supported in Ubuntu v22.04 / 24.04 and for how long? [Short List]("https://ubuntuforums.org/showthread.php?t=2480110") Is it up to the Mfg ONLY? 
Maybe we are asking the wrong people!?!? Are they better supported under another Open OS like Red Hat, etc.? If so ... who?
Three weeks later I'm still messing around trying to get my computer to work ... loosing productivity and money. 
I have 4 computers and 3 monitors sitting on my floor collection dust. Are they garbage now? Is this 8 core CPU garbage?
Trying to keep my sanity is difficult to say the least in this world. Much less have to deal with this also! 
I doubt it, but hope this helped someone. This issue is still not resolved. Suggestion were to buy another GPU (1000s to choose from ... but, which one), 
dump VirtualBox and use another Virtual software like KVM/QEMU (researching it now) but can't calculate lost time and money! Enough Ranting - Sorry

---

### Post by TheFu on 2024-05-20
If it were me and you didn't plan to get a $1500 GPU, then I'd go with the AMD GPU that fit my needs and budget. Get a current generation GPU that is supported by the kernel you use for the longest support period.

I have doubts that anything else is wrong, without more data showing a motherboard, CPU, PSU, HDD, SSD or some other issue.

Drivers aren't Linux-OS dependent.  All flavors of Linux have the same kernel, just different versions. Eventually, they all will have the same driver. Some are more bleeding edge which has pros and cons.  Some use older kernels, which means they are more stable, but don't support the latest drivers/hardware.  Releases from different vendors hope over each other with the latest kernels.

A GT610 is pretty old. It was the low-low-low-end GPU when it was new.  It has a VGA output, which hasn't been part of most GPUs over 6 yrs.  I know, 6 yrs ago, I wanted a VGA connected GPU and couldn't find any except 8-monitor versions for $1200 (trading platform GPUs) with specialized Windows-only drivers.  Any current generation GPU would be better. In fact, any iGPU would be better from the last 3 yrs, so it may make sense to do a GPU+iGPU upgrade now.

I would have screwed around with an old nVidia GPU for a few days, then found a replacement AMD GPU and bought that. Down time would have been at most 7 days, probably 3-5 days.

---

### Post by Rick St. George on 2024-05-22
> **TheFu said:**
> 
If it were me and you didn't plan to get a $1500 GPU, then I'd go with the AMD GPU that fit my needs and budget. Get a current generation GPU that is supported by the kernel you use for the longest support period.


Thanks FU ... Found this helpful [List at wikipedia.org]("https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units")

Going with Radeon 580, $95 on Amazon, and will plug 3 monitors into it. This will get rid of Nvidia driver 390 (or I'll Remove it), and working on switching to QEMU/KVM instead of VirtualBox. Have [post under Virtualization]("https://ubuntuforums.org/showthread.php?t=2497347") dealing with that issue!

Many, many posts & articles about this issue with v22.04 and 24.04 booting to a black screen. After reading all these, for days, it seem also it may be related to the now default Plasma Wayland vs. X11 debate. 

FYI: for anyone who doesn't know ...

Perhaps the main feature of Wayland is GUI level sandboxing, Wayland "Clients" can not snoop on others, so in theory a malicious program can't log you entering passwords or the like.

What they call benefits or features I call roadblocks to me being productive, and breaking of long standing paradigms for doing work without jumping thru often illconceived, complex, or unstable hoops to achieve the same end goal. Nobody asked me if I wanted to switch!?! I don't believe that level of sandbox sophisitication is needed on most home workstations.

I don't want the koolaid rammed down my throat, thank you!
So ... how to convert back to X11?

Upon Boot-up, Before Login, click the COG wheel lower right corner.
Choose x11 option and login. May have to ReStart.

NOTE: May not need to if using a supported GPU / Kernel. Will wait till after I receive my new card to see what happens!

---

### Post by TheFu on 2024-05-22
Be very careful getting GPUs that aren't new.  For a few years now, lots of fakes that will claim to be 1 type have had their firmware flashed to lie about the true model of the card.  Many are used that were overclocked and run full out for over year doing crypto-workloads.

When it comes to GPUs, I'd only buy new from a big-box computer store with supply chain I can trust or from a friend who likes to upgrade, but doesn't actually know much about GPUs and is upgrading because they think they need something faster (probably for no good reason).

I'd stay away from online retailers with known, shared, "bins" for different suppliers - basically, they mix the good, reputable, parts with the unscrupulous parts and don't have any way to track back to which supplier provided the bogus card.  You may be willing to risk it.  I am not.

Of course, having an iGPU completely removes that possibility.

---

### Post by Rick St. George on 2024-05-23
> **TheFu said:**
> Be very careful getting GPUs that aren't new.  For a few years now, lots of fakes that will claim to be 1 type have had their firmware flashed to lie about the true model of the card.  Many are used that were overclocked and run full out for over year doing crypto-workloads.


I thought that was the prime reason for the massive build out of memory and clock speed of these GPUs!
So - how does one stop this intrusion of our GPUs and Systems?

---

### Post by TheFu on 2024-05-23
I don't know.  Opinions follow - verify things you might think are facts.

Buy "APUs" (CPUs with built-in iGPUs)?  However, even those may lose support, if not forever, for a few years.  

For example, around 2010, I bought an AMD APU - E-350 system ($100 for the ITX MB+APU+case+PSU) because it had a Radeon iGPU with the CPU that would do decoding of mpeg2 videos in the iGPU for 720p and lower resolutions.  Then something changed related to Linux support and the iGPU wasn't supported anymore for some reason.  It never handled 1080p resolution videos and the CPU just couldn't handle software-based decoding of other codecs with higher than 600p resolutions.  I limped along for a few years with that, then moved to a Pentium G3258 which was 5-10x faster and used more "standard" components like a mATX motherboard, standard PSU, etc.  That was fast enough and had an Intel iGPU which was fine for my needs.  It became the network NAS and ran a few light VMs without problems.  Never had any complaints about the iGPU, since it wasn't really used for anything.  I stopped watching content on the system at this switch and got a Raspberry Pi 2 to use as a media player which supported both mpeg2 and h.264 video playback at 1080p over the network.  A few years later, I moved to a r-pi3 and used that for over 5 yrs.  About a year ago, I got tired of waiting and r-pi4 hardware was becoming easier to find, so I picked one of those up. Fantastic playback device that handles mpeg2, h.264 and h.265 decoding/playing in hardware.  The downside is that it needs a fan and that fan isn't silent. 

The pi2 and pi3 didn't need fans, so they were silent.  The pi2 is a backup p-hole/DNS for my LAN. It is more than fast enough for that.  I only boot it when taking down the main LXC-based pihole.

The pi3 can handle significantly more workload. Today it is used as a spare media player, mostly for music in other rooms of the house, though it can handle video too - if there's a screen in the room.

I'm still using a pi4 as a media player, but Santa brought me a pi5 for Xmas.  The Pi5 isn't much of an upgrade for my needs.  It is barely faster than the Pi4 and they removed some of the hardware video codec support, so it isn't as efficient as the pi4 for that purpose.  Mine is built, has an OS, but I've only used it about 1 hour since Xmas.  It might be a good laptop replacement with a small, folded USB keyboard+touchpad and a 10in HDMI 1080p screen. OTOH, a used $150 chromebook that is wiped and has a lite-Ubuntu loaded will probably be more capable and more flexible.  My local microcenter has an $80 Chinese-no-name laptop like that with a very slow Intel N34xx CPU from 2016 that is probably more flexible/better for conference uses. I'm tempted.  Not good for much else, I suspect.  I understand the audio chips took 2-3 years before Linux support was easy. I'll probably just take a $2 paper notebook instead and seem like a Luddite.  OTOH, that cheap laptop will have a CPU + iGPU that is more than sufficient to watch local videos that **are not** h.265/HEVC encoded.

AMD has pushed their drivers into the kernel, so I don't expect support to be removed like the nVidia proprietary driver (blob) support is removed.  There is a cost to supporting drivers for older hardware that won't create any profit for the GPU company.  I understand that nVidia has been trying to get their drivers, at some level, into the F/LOSS model, but there is just so much proprietary information in their hardware and drivers and the company sells out of almost all their hardware that gets made.  There is little reason for the leader in AI hardware to bother with low-end GPU hardware for cheap people like me.  Intel and AMD do seem to consider us in their marketing plans and pricing, so I'm happier to give them my money.  With the iGPU in the CPU, failures will be extremely rare, if they ever happen at all.  When was the last time any CPU actually failed?  I cannot think of any that I know having failed since the 1980s.  That means that AMD's model of providing F/LOSS drivers for the most common GPU/iGPU uses shifts the long term support into the kernel, freeing up AMD's engineers to work on "the new" stuff.

---

### Post by Rick St. George on 2024-05-24
Thanks Fu for the Good  advice and comments. I purchased a 3yr Ext. Wrrnty from Amazon. If it goes bad, I may rebuild my system with an iGPU. 
Although, not sure what to do with MSI military hardened Mobo and AMD FX-8320 Fishera 8 core CPU, as can't get Ubuntu to run on it!

Problems with Nvidia 390 drivers (not supported) and VirtualBox which is showing Errors on Boot-up, and now blocked my VM Partition from mounting.
Have posted this issue under Virtualization [Here]("https://ubuntuforums.org/showthread.php?t=2497347"). 

Thank you for your time and consideration.

UPDATE: 

Received new GPU RX-580 w/8GB  -> Removed all Nvidia; installed GPU, Upon Boot-up did FRESH install of UbuntuStudio v22.04 (preserving /home in separate partition), After Re-Boot ... Installed AMDGPU-install; Ran AMDGPU-install; ReBoot and computer running Great for 3 Restarts. All 3 monitors working. Now working with QEMU to pull in Virtual Appliance (see link above). 

Thanks again for all replies and much needed help.

---

