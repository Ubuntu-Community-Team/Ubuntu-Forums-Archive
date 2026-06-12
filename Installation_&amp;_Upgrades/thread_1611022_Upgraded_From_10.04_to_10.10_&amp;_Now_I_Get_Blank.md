---
title: "Upgraded From 10.04 to 10.10 &amp; Now I Get Blank Screen"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by hayhursm on 2010-11-01
I upgraded from Ubuntu 10.04 to 10.10 on my Asus F3Ka laptop and if select Kernel 2.6.35-23-generic to boot with the screen will go blank (it appears to turn off but laptop remains on).  However, if I boot with Kernel 2.6.32-25-generic everything boots up just fine.  The problem appears to be with Kernel 2.6.35-23-generic, is there a fix for this?  Also, I am running Ubuntu with a dual boot of Windows XP if that is of any relevance.

---

### Post by oldfred on 2010-11-01
Often a video issue.
To see what video you have:
sudo lspci | grep VGA

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

(from Fedora)
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

---

### Post by hayhursm on 2010-11-02
> **oldfred said:**
> Often a video issue.
To see what video you have:
sudo lspci | grep VGA

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

(from Fedora)
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

Thank you for the reply.  My Asus laptop has an ATI Radeon card and the  "Radeon: radeon.modeset=0" setting seemed to allow me to progress a  little more.  I ended up downloading the ATI Driver for Linux from their  website and installing it from the command prompt.  I actually got the  Splash screen to appear for a few seconds and then it booted straight to  the command line.  When I typed "startx" I get a "Fatal server error:  no screens found"  I also got something that says: "Screen(s) found, but  none have a usable configuration."  Before Kernel 2.6.32-25-generic  would work and now it does not.  I'm really lost now, any suggestions?

---

### Post by ronparent on 2010-11-02
I ran into the same problem updating 10.04 to 10.10. I don't believe the problem is so much with the new kernel but rather with the fact that the older ati vid driver don't work on the new kernel. There were some twists and turns that I don't exactly remember now.

Basically what I had to do was to delete and purge the ati drivers in my old kernel. And then getting the old kernel to work with the default drivers. For me that was complicated by the fact the default driver didn't work at all with my twin monitors. Then booting into the new kernel with  the display tworking with the default driver. Then I used Sytem>Administratio>New Drivers to install the new ati drivers. The bottom line seems to be that the ati drivers installed to work with the 10.04 kernel has to be removed and purged before the new ati drivers that work with 10.10 are installed. It doesn't make good semse to me, but, that is what happened.

---

### Post by hayhursm on 2010-11-03
> **ronparent said:**
> I ran into the same problem updating 10.04 to 10.10. I don't believe the problem is so much with the new kernel but rather with the fact that the older ati vid driver don't work on the new kernel. There were some twists and turns that I don't exactly remember now.

Basically what I had to do was to delete and purge the ati drivers in my old kernel. And then getting the old kernel to work with the default drivers. For me that was complicated by the fact the default driver didn't work at all with my twin monitors. Then booting into the new kernel with  the display tworking with the default driver. Then I used Sytem>Administratio>New Drivers to install the new ati drivers. The bottom line seems to be that the ati drivers installed to work with the 10.04 kernel has to be removed and purged before the new ati drivers that work with 10.10 are installed. It doesn't make good semse to me, but, that is what happened.

How exactly did you remove the drivers?  I did a **[FONT=monospace]"[/FONT]sudo aptitude purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx**"taken from the ATI Linux Driver Wiki and no success.  What you said makes sense so maybe I'm overlooking something?

---

### Post by Mark Phelps on 2010-11-03
> **ronparent said:**
> I ran into the same problem updating 10.04 to 10.10. 

I ran into what looks to be the same black screen problem -- but that was with a clean install of 10.10 and using the open-source radeon drivers.

So, the problem is not limited to in-place upgrades and fglrx drivers.

I was told that reinstalling ubuntu-desktop fixes this -- but I haven't had a chance to try that yet.

---

### Post by ronparent on 2010-11-03
I do think that the fglrx drivers that worked for 10.04 do not update properly (if at all) in the upgrade to 10.10. The release of flgrx drivers that worked in 10.10 were late in the release cycle for that release and I had originally worked trough most of the 10.10 development cycle with no proprietary drivers. Once introduced to my developmental install the new drives worked fine. My initial intro to upgrading a 10.04 install was a black screen as was yours. So I basically concluded that I had to rid that install (10.04 kernel) of all signs of fglrx tha it was operating on and reinstalling in the 10.10 kernel.

I wasn't as thorough as you but I did essentially the same thing with 'sudo apt-get remove fglrx' and 'sudo apt-get purge fglrx' under the old kernel (10.04). As I said I ran into complications with a second monitor on-line and had to experiment to find which monitor to disconnect. The rest is murky. I may have had to bring up the new kernel with nomodeset. From there I was able to reinstall fglrx, configure it for the 1920x1200 monitor, and reattach the 2nd monitor. Because of a quirk in fglrx I had to use System>Preferences>Monitors to reconfigure my monitor resolutions under the new kernel (my setting don't hold using the ATI utility). Well, you get the idea. I don't think I needed any black magic but it wasn't completely straight forward. I'll post if I can recall any explicit detail I may have oerlooked.

---

### Post by hayhursm on 2010-11-03
> **ronparent said:**
> I do think that the fglrx drivers that worked for 10.04 do not update properly (if at all) in the upgrade to 10.10. The release of flgrx drivers that worked in 10.10 were late in the release cycle for that release and I had originally worked trough most of the 10.10 development cycle with no proprietary drivers. Once introduced to my developmental install the new drives worked fine. My initial intro to upgrading a 10.04 install was a black screen as was yours. So I basically concluded that I had to rid that install (10.04 kernel) of all signs of fglrx tha it was operating on and reinstalling in the 10.10 kernel.

I wasn't as thorough as you but I did essentially the same thing with 'sudo apt-get remove fglrx' and 'sudo apt-get purge fglrx' under the old kernel (10.04). As I said I ran into complications with a second monitor on-line and had to experiment to find which monitor to disconnect. The rest is murky. I may have had to bring up the new kernel with nomodeset. From there I was able to reinstall fglrx, configure it for the 1920x1200 monitor, and reattach the 2nd monitor. Because of a quirk in fglrx I had to use System>Preferences>Monitors to reconfigure my monitor resolutions under the new kernel (my setting don't hold using the ATI utility). Well, you get the idea. I don't think I needed any black magic but it wasn't completely straight forward. I'll post if I can recall any explicit detail I may have oerlooked.

> **Mark Phelps said:**
> I ran into what looks to be the same black screen problem -- but that was with a clean install of 10.10 and using the open-source radeon drivers.

So, the problem is not limited to in-place upgrades and fglrx drivers.

I was told that reinstalling ubuntu-desktop fixes this -- but I haven't had a chance to try that yet.


I'm in the same boat as Mark, I wiped out the HDD for a clean install, loaded the 10.10 .ISO on a freshly formatted USB stick, and to my dismay I still get the Black Screen of Death.  I get the BSOD regardless if I select "Try Ubuntu" or "Install Ubuntu".  This is very disappointing because I was really hoping to see some fixes in 10.10.  I guess I'll have to wait another six months and hope that this problem is corrected?  Should this be reported in Launchpad as a bug?

---

### Post by NCTinkerer on 2010-11-03
I am green as grass with Ubuntu but had same issue with black screen. Since I had no previous experience, I assumed that Ubuntu would not support the DVI video from my Matrox G550. I switched to the analog output and I am now operational. I was actually just now checking this forum to find out how to enable the DVI capability. Should I be able to use the DVI output of my video card? Thanks :)

---

### Post by hayhursm on 2010-11-03
> **NCTinkerer said:**
> I am green as grass with Ubuntu but had same issue with black screen. Since I had no previous experience, I assumed that Ubuntu would not support the DVI video from my Matrox G550. I switched to the analog output and I am now operational. I was actually just now checking this forum to find out how to enable the DVI capability. Should I be able to use the DVI output of my video card? Thanks :)

[COLOR=Black]Yes, you should be able to use the DVI output with Ubuntu...I currently have two functional DVI outputs on my Nvidia 250GTS that work great with Ubuntu Lucid.  I think the big problem exists with Maverick's kernel playing nice with graphics card's drivers.[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127478")[/COLOR]

---

### Post by Mark Phelps on 2010-11-03
OK folks, can't take credit for solving this ... but I was told to try the following:
> 
sudo apt-get install --reinstall ubuntu-desktop

And it ... WORKED!  I have my desktop back.

So, try booting into recovery mode and when you get to the command prompt, enter the command above,  Who knows, it might work for you, too!

---

### Post by hayhursm on 2010-11-04
> **Mark Phelps said:**
> OK folks, can't take credit for solving this ... but I was told to try the following:

And it ... WORKED!  I have my desktop back.

So, try booting into recovery mode and when you get to the command prompt, enter the command above,  Who knows, it might work for you, too!

It seems the only way I can get anything to happen is to highlight: **Ubuntu, with Linux 2.6.35-22-generic**, press **e**, delete **quiet splash** and enter: **radeon.modeset=0**.  All this does is take me to the command line (recovery mode always sends me to blank screen so it's of no use).  Keep in mind that this is a fresh install as I formatted the HDD, installed 10.04 (no drivers were installed), and then upgraded to 10.10 through Update-Manager.  Also, the **sudo apt-get install --reinstall ubuntu-desktop** did not work for me.  Any ideas?

---

### Post by hayhursm on 2010-11-04
I have submitted a bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/670992](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/670992)

---

