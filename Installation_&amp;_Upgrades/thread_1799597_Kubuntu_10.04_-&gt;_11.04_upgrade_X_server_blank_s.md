---
title: "Kubuntu 10.04 -&gt; 11.04 upgrade X server blank screen after tty switch"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by jingyen on 2011-07-07
This Kubuntu 11.04 upgrade has been a nightmare.  I had 10.04 (64bit) working fine on my Sony Vaio VPCZ with the NVIDIA 260.19.29 driver installed.  I made the mistake of upgrading to 11.04 through the graphical package manager (I think it was KPackageKit).

The short version of the problem is that I upgraded my NVIDIA driver to 275.09.07 to get X working semi-working again.  The problem now is that X starts up with a blank screen (the sound is working, and I can get into a console blind by pressing ALT+F2, typing "konsole", type "xrandr --auto > xrandroutput").  I switch to tty1, and the file is there.  Once I killall kdm and startx again, I can see the Xserver perfectly and all work well UNTIL I switch to tty[1-6] again.  Once I switch out of tty7 into any other ttys, X server will exhibit the blank screen problem again.  Has anyone else had this problem?  There is no relevant log output in /var/log/Xorg.0.log that hints at any problem in the driver.  I'm stumped.  Where else can I look to troublshoot this?  Does having a framebuffer text console have anything to do with this?  I did notice that after my 11.04 upgrade, I have a nice framebuffer in my ttys.

For my entire upgrade experience see below:

After boot, linux couldn't mount my swap partition.  The error at the time was The disk drive for /dev/mapper/isw_bjcfegideh_Volume05 is not ready yet or not present.  I ran "sudo blkid" and found that the partition name had been changed to /dev/mapper/isw_bjcfegideh_Volume0p5.  No problem - I changed the fstab to reflect the new naming mechanism for 4 of my other partitions and added the p prefix before the partition number.  Next boot, X crashed with the error "This server has a video driver ABI version of 10.0 that is not supported by this NVIDIA driver.  Please check [http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X
server with a supported driver ABI."  Upgraded NVIDIA driver to 275.09.07 and now X will boot with a blank screen until I killall kdm and startx via terminal in another tty.  X works fine now UNTIL I have to switch out of X into another tty.  Switching back to X now yields a blank screen.

---

### Post by jingyen on 2011-07-08
The framebuffer doesn't seem to be the culprit.  I killed it, and the problem still persists.  Any ideas / suggestions are welcomed.

---

### Post by wandalalakers on 2011-07-08
Maybe this will help.
[http://ubuntuforums.org/showthread.php?t=1618612](http://ubuntuforums.org/showthread.php?t=1618612)
I haven't been able to use the 27x drivers for a while.
The ksplash screen loads and the last icon freezes and I hear the startup sound but never get to the desktop.
For now, I'm not using 11.04.

---

### Post by MAFoElffen on 2011-07-08
> **jingyen said:**
> This Kubuntu 11.04 upgrade has been a nightmare.  I had 10.04 (64bit) working fine on my Sony Vaio VPCZ with the NVIDIA 260.19.29 driver installed.  I made the mistake of upgrading to 11.04 through the graphical package manager (I think it was KPackageKit).

The short version of the problem is that I upgraded my NVIDIA driver to 275.09.07 to get X working semi-working again.  The problem now is that X starts up with a blank screen (the sound is working, and I can get into a console blind by pressing ALT+F2, typing "konsole", type "xrandr --auto > xrandroutput").  I switch to tty1, and the file is there.  Once I killall kdm and startx again, I can see the Xserver perfectly and all work well UNTIL I switch to tty[1-6] again.  Once I switch out of tty7 into any other ttys, X server will exhibit the blank screen problem again.  Has anyone else had this problem?  There is no relevant log output in /var/log/Xorg.0.log that hints at any problem in the driver.  I'm stumped.  Where else can I look to troublshoot this?  Does having a framebuffer text console have anything to do with this?  I did notice that after my 11.04 upgrade, I have a nice framebuffer in my ttys.

For my entire upgrade experience see below:

After boot, linux couldn't mount my swap partition.  The error at the time was The disk drive for /dev/mapper/isw_bjcfegideh_Volume05 is not ready yet or not present.  I ran "sudo blkid" and found that the partition name had been changed to /dev/mapper/isw_bjcfegideh_Volume0p5.  No problem - I changed the fstab to reflect the new naming mechanism for 4 of my other partitions and added the p prefix before the partition number.  Next boot, X crashed with the error "This server has a video driver ABI version of 10.0 that is not supported by this NVIDIA driver.  Please check [http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X
server with a supported driver ABI."  Upgraded NVIDIA driver to 275.09.07 and now X will boot with a blank screen until I killall kdm and startx via terminal in another tty.  X works fine now UNTIL I have to switch out of X into another tty.  Switching back to X now yields a blank screen.
Is because your laptop has Nvidia Omni / switchable hybred graphics... where it has two video chipsets, a low and high graphics pair of chipsets that need an in-between driver to allow the graphics to swicth between then (such as bumblebee).  Some of these hybreds can use a bios setting option to switch the chipsets, some an apci call, some only that in-between driver.

Please go here to see if this applies to you:
[http://linux-hybrid-graphics.blogspot.com/2011/06/dell-xps-l702x-nvidia-optimus-linux.html](http://linux-hybrid-graphics.blogspot.com/2011/06/dell-xps-l702x-nvidia-optimus-linux.html)

---

### Post by jingyen on 2011-07-08
> **pcdoctor said:**
> Maybe this will help.
[http://ubuntuforums.org/showthread.php?t=1618612](http://ubuntuforums.org/showthread.php?t=1618612)
I haven't been able to use the 27x drivers for a while.
The ksplash screen loads and the last icon freezes and I hear the startup sound but never get to the desktop.
For now, I'm not using 11.04.

Thank you for the link.  I had already taken the steps when I originally installed 10.04 to get my NVIDIA working with this hybrid graphics setup.  Unfortunately, those steps have already been taken, and this doesn't resolve my problem.


> **MAFoElffen said:**
> Is because your laptop has Nvidia Omni / switchable hybred graphics... where it has two video chipsets, a low and high graphics pair of chipsets that need an in-between driver to allow the graphics to swicth between then (such as bumblebee).  Some of these hybreds can use a bios setting option to switch the chipsets, some an apci call, some only that in-between driver.

Please go here to see if this applies to you:
[http://linux-hybrid-graphics.blogspot.com/2011/06/dell-xps-l702x-nvidia-optimus-linux.html](http://linux-hybrid-graphics.blogspot.com/2011/06/dell-xps-l702x-nvidia-optimus-linux.html)

Thanks for the reply, but I had actually flashed my BIOS to support switching statically at boot time when I had originally installed 10.04 months ago.  That is the same solution as proposed in pcdoctor's link as well.  The VPCZ is pretty particular about that with its hybrid graphics, and that was the only way I could get it working.  I always keep the switch on performance mode to trigger the kernel to use the NVIDIA driver.

This set up worked flawlessly with 10.04 before.  And it works flawlessly with 11.04 after I kill X on first boot (before graphical login) and restart it.  It's when I switch to a different tty from getting a working X that kills the screen in tty7, but X still hums along.  If I play a track in Promoe, my xmms2 client, I can still hear it even though the screen is blank.  I can also open a console and blind type some commands to output to a file and check it from one of the other ttys to make sure it is there.  The display driver works fine until I switch terminals.

---

### Post by MAFoElffen on 2011-07-08
> **jingyen said:**
> Thank you for the link.  I had already taken the steps when I originally installed 10.04 to get my NVIDIA working with this hybrid graphics setup.  Unfortunately, those steps have already been taken, and this doesn't resolve my problem.

Thanks for the reply, but I had actually flashed my BIOS to support switching statically at boot time when I had originally installed 10.04 months ago.  That is the same solution as proposed in pcdoctor's link as well.  The VPCZ is pretty particular about that with its hybrid graphics, and that was the only way I could get it working.  I always keep the switch on performance mode to trigger the kernel to use the NVIDIA driver.

This set up worked flawlessly with 10.04 before.  And it works flawlessly with 11.04 after I kill X on first boot (before graphical login) and restart it.  It's when I switch to a different tty from getting a working X that kills the screen in tty7, but X still hums along.  If I play a track in Promoe, my xmms2 client, I can still hear it even though the screen is blank.  I can also open a console and blind type some commands to output to a file and check it from one of the other ttys to make sure it is there.  The display driver works fine until I switch terminals.
On the later... I have the same on Banshee, closing a window... without closng it from the actual menu (quit/close) and it plays somewhere off in limbo...  A known bug that just closing the window is not killing the process.

On the switched / hybred graphics... Yes, I wish there was a better way.  Intel/Nvidia and Intel/ATI is newly working and getting better with time (still in infancy in Linux support).  Nvidia is not supporting it in Linux. (Others are as opensource)  ATI is through Crysalis.  Nvidia/Nvidia hybreds and Sandy Bridge/Nvidia hybreds still seem unsupported so far, so owners of those are still stuck with the lower capabilies of the first of the 2 chipsets.  (As far as I know so far.)  

Since you can "switch"... did you update through NVdia's Installer or just install new manually.  If installed manually, did you "uninstall" your previous driver install before installing the new one?  This is something that NVidia recommends in their driver install instructions with their own drivers to ensure that there is no conflicts.  Their own nvidia-installer update function goes through those checks...

From NVidia's Install Instructions:
> FEATURES OF NVIDIA-INSTALLER  

o Uninstall: Driver installation will backup any conflicting files   and record what new files are installed on the system.  

You may run:  nvidia-installer --uninstall      
to uninstall the current driver; this will remove any files that   were installed on the system, and restore any backed up files. [COLOR=Magenta]  Installing new drivers implicitly uninstalls any previous drivers.  [/COLOR]

o Auto-Updating: 

If you run: nvidia-installer  --latest      
the utility will connect to NVIDIA's FTP site, and report the latest   driver version and the url to the latest driver file.      

If you run:      nvidia-installer  --update      the utility will connect to NVIDIA's FTP site, download the most recent   driver file, and install it.Even though the installer says it should remove any older files that may conflict, for some reason, with Natty, it hasn't always been true... Manually uninstalling seems to be a popular current work-around for manual nvidia install problems in natty.

Another thing is to ensure that you have current linux-header files for the kernel you are installing on... the nvidia-installer uses those header files during the install.  It also needs current updates on gcc and other packages (build-essential gcc-4.4 g++-4.4 libxi-dev libxmu-dev freeglut3-dev) for building the nvidia kernel module.

---

### Post by MAFoElffen on 2011-07-08
And then again.... I reread your 1st post.

Here's what I get on rereading that... and what happens in Natty itself (Even with the drivers working well.)

I am in Tty7.  I hit hotkeys to switch to tty 1-6 and it switches over... I switch back over to Tty 7 and there is a blank screen, after a wait it intializes the graphics mode (a little scrambled at first, then clears up). Sometime (for me) that black screen seems like forever.  (For some it is.)  Sometimes that scrambled screen doesn't clear up and I have to hotkey back and forth to get back to tty7.  It also happens a lot slower than previous versions of Ubuntu!!!

Is that what you are describing?

If so, that seems to be a Natty thing (started with), not just an nvdia thing... Also happens with Oneiric and they're working on it.

---

### Post by jingyen on 2011-07-08
> **MAFoElffen said:**
> And then again.... I reread your 1st post.

Here's what I get on rereading that... and what happens in Natty itself (Even with the drivers working well.)

I am in Tty7.  I hit hotkeys to switch to tty 1-6 and it switches over... I switch back over to Tty 7 and there is a blank screen, after a wait it intializes the graphics mode (a little scrambled at first, then clears up). Sometime (for me) that black screen seems like forever.  (For some it is.)  Sometimes that scrambled screen doesn't clear up and I have to hotkey back and forth to get back to tty7.  It also happens a lot slower than previous versions of Ubuntu!!!

Is that what you are describing?


Unfortunately not.  The issue is that when I go back to tty7, the blank screen never recovers.  The only way to get X back is to go to the other non-X ttys to "sudo killall kdm" and "startx" again.

---

