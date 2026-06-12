---
title: "Can't install ubuntu"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by gswartz on 2012-11-01
I have win7 and have tried all 3 methods for installing ubuntu but can't get it to work.

1. I used the windows installer and after rebooting and selecting the ubuntu OS it doesn't load but instead just shows a bunch of multi colored pixels on the screen.

2. DVD ISO - I get the first screen with the icon in the bottom of the orange center and then it goes to a blinking cursor (waited over a half hour with no progress).

3. USB ISO - This gets the farthest of all... but it stops at [ 4.599834] hub 1-1:1.0 >6 ports detected

Can anyone suggest how I can get ubuntu successfully installed? I'm running this on an ASUS G75VW-BBK5 and the 64 bit version of ubuntu 12.10.  Thanks.

---

### Post by offgridguy on 2012-11-01
You could take a look here.

[http://www.ubuntugeek.com/the-extrem...ng-ubuntu.html]("http://www.ubuntugeek.com/the-extremely-simple-guide-to-installing-ubuntu.html")

---

### Post by oldfred on 2012-11-02
What video card/chip? Often a video issue. 

I have nVidia and have to use nomodeset on all liveCD or USB boots and first boot after install until I install the proprietary driver.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
See post #19 by Bogan on nVidia drivers from nVidia.
[http://ubuntuforums.org/showthread.php?t=2075318](http://ubuntuforums.org/showthread.php?t=2075318)

Also with 12.10 there has been an issue with proprietary drivers and a missing Linux header. If you will be installing proprietary drivers make sure header is installed first.

---

### Post by gswartz on 2012-11-02
offgridguy, I gave that a try also and upon the requested reboot it just boots right into windows instead of ubuntu.

oldfred, thanks I'll give that a try.  it's an nvidia geforce gtx 660m

---

### Post by gswartz on 2012-11-02
So the nomodeset did the trick.  However once it finished installing it asked me to reboot which I did.  Instead of getting the dual boot manager to select windows or ubuntu it just booted directly to windows.  Shouldn't it have given me OS boot options?

---

### Post by gswartz on 2012-11-02
I came across this site - [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/) and tried the easybcd.  After doing that I do get the dual boot option but selecting Ubuntu 12.10 gives the the attached error message.  A friend suggested that grub isn't installed.  Does that sound right and if so, how do I do that?  I thought it was all part of the original installation.

---

### Post by oldfred on 2012-11-02
A few have used EasyBCD, generally we prefer grub. Where did you install grub2's boot loader. It seems you left the Windows boot loader in the MBR of the drive you boot from in BIOS. I think EasyBCD requires grub to be installed to a partition which is not recommended by grub.

If you want Easy:
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you want to install grub2's boot loader run this so we can see what is where:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by gswartz on 2012-11-03
I don't know where it was installed.  I just went through the installer and I didn't see a spot to specify that.  However during the installation I did see that it quickly showed something about "installing grub".  

In easybcd I have different options than what I've seen in other tutorials.  When I select grub2 it has a dropdown with the partitions but I have no idea which one to select (see attached screenshot).  If I go with Automatically Locate and Load and then try to boot to ubuntu it gives me the previous error message/screen I posted.  So I'm wondering if it's not correctly automatically finding it and I need to specify one of the partitions.

Am I supposed to manually install grub after the installation completes (even though the installation progress reported it was installing grub)?  I tried using the intall cd (is that what's considered a LiveCD?) and doing the sudo bash grub but no luck.

---

### Post by gswartz on 2012-11-03
I've done some experimenting with the cd and tried this.  After setting my bios to boot from cd I put the install cd in which brought up screen 1 attachment.  I hit F6 and turned on nomodeset and then selected the Boot from first hard disk option.

That takes me to screen 2 attachment and I selected the Ubuntu with options.  This takes me to screen 3 attachment and I select Ubuntu with linux generic.  It starts to load (screen 4) but then it's like the nomodeset had no effect because now I get screen 5 with the pixelation.

Why does this have to be so darn difficult to install?

---

### Post by oldfred on 2012-11-03
I do not know EasyBCD.

But I think you still need nomodeset. With my system I have to have grub menu, press e for edit on boot entry and on linux line replace quiet splash with nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

