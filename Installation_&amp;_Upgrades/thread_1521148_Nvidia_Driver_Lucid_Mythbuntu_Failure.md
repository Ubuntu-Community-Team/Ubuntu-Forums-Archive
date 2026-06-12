---
title: "Nvidia Driver Lucid Mythbuntu Failure"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by ep42 on 2010-06-30
Edit:  Mods, Please, with all humility and suplication, please redirect my post if I've placed it the wrong forum.
 
This noob had mythbuntu/xbmc running for 4 months with vdpau and all the same hardware. I killed it with an update and thought it'd all be easier To build it the 2nd time -- wrong!
 
Fresh install of mythbuntu lucid off cd
Asus p5g43t-m pro
nvidia gforce 9500 gt
 
what I tried so far...
Different drivers with the hardware app thingee.
Multiple times -- Purge nvidia, purge nouveau, blacklist list of other video stuff with extra line after, stop gnome, manual install various drivers - 195.xxxxx or Synaptic install various drivers. 
Tried updates, adding avenard and daily build repos.
Everything in combinations.
Outcome remains consistant. Lo res error start, can't load nvidia driver, selected but not in use, xorg.conf needs editing.
I'm getting the same error messages as the common nvidia help posts describe but the solutions aren't working for me.
 
4 days of this, 3 installs plus a shot at Mint, and no progress. I'm pretty frustrated. I'd consider returning to karmic if I didn't think the updates would pork the nvidia driver all over again.
Last install of 9.10 there was a required edit of vmalloc=256M and a shut off of cx18. That's been fixed in lucid? What else ccould it be? 
 
I wish I didn't have to ask y'all for help, but I'm stumped and fried.

---

### Post by oldfred on 2010-06-30
I have Nvidia 9600gt

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Additional settings if needed:
Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

---

### Post by ep42 on 2010-06-30
Thanks!  I can't wait to try it out!

---

### Post by ep42 on 2010-07-12
I started down Oldfred's instructions and got a little lost (noob).  But it caused me to recall that in Karmic I set up my card while using the non-nvidia onboard video.  I tried that out and still had no luck.

Success finally, after a bunch of things, but I think the key for me was the last item ( vmalloc=256MB ) that I had to do to set up Karmic!

But here's everything, just in case (superstitious noob):
[INDENT] I booted with monitor attached to non nvidia onboard video 
and nvidia card uninstalled.

I enabled x-swat ppa and updated (this brings in the 256 drivers as '185')

I followed 1 through 4 of http:// filthypants.blogspot.com/2010/06/nvidia-25635-driver-on-unbuntu-1004.html -- similar to many other threads in this forum, but all in one place.  After many attempts, I altered in slightly.

1. sudo aptitude install linux-headers- $(uname -r) build-essential  nvidia-settings

2.  sudo nano /etc/modprobe.d/blacklist.conf
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist rivatv
(I left out blacklist nvidiafb, but put it back in later.
ctrl x, save

3. sudo apt-get remove --purge nvidia-*

4. sudo reboot

then here -- [http://ubuntuforums.org/showthread.php?t=1521669&page=3](http://ubuntuforums.org/showthread.php?t=1521669&page=3)  quoted[INDENT]  Re: Newest kernel release 2.6.32-23 breaks nVidia drivers
"I have a new solution.

I think he have a problem with compilation official nvidia driver with  this new kernel or with dkms.

I use this method and it's works !!

In first time boot to the kernel 2.6.32-23.
Make :
Code:

sudo apt-get install -f

to check your package and repair their.

remove and install the hearders :
Code:

sudo apt-get install --reinstall linux-headers-2.6.32-23-generic

purge and install nvidia drivers for this kernel :
Code:

sudo apt-get purge nvidia-*
sudo apt-get autoclean
sudo apt-get install nvidia-glx-185  
(I later re-purged nvidia and installed nvidia-current instead)

use nvidia-glx-185 if you use this nvidia driver version 195.36.24
(I later re-purged nvidia and installed nvidia-current instead for driver 256)

reboot and enjoy it !! "
[/INDENT]Getting good resolution sometimes after restarting X, but still not able to adjust using nvidia settings -- getting 2 errors:
[INDENT] in nvidia settings -- "you do not appear to be using the nvidia  x-driver. 
please edit your x confi file (just run 'nvidia'xconfig' as root), 
and restart the x server" -- If I cannot adjust overscan then I can't use my mythbox on my sony CRT -- very important feature for me to be able to reduce overscan with this widget.

and in hardware drivers ap -- "this driver is activated but not 
currently in use"
[/INDENT]I hit strl-alt-F1 to go out to main terminal, run sudo gdm-stop
to stop x, and ran nvidia-config.  Nvidia config made a file.  Then I  booted again to low res.

After many bouts of  reinstallation I added nvidiafb to the Blacklist, then turned
off X, did sudo nano  /etc/default/grub , 
then changed "quiet  spash" to "vmalloc=256MB" -- thank you to mfraser -- I remember now  using this remedy on Karmic.  this was ubuntuforums thread  14661508  titled ubuntu 10.04 and nvidia cards, page 13. 

[/INDENT]

---

