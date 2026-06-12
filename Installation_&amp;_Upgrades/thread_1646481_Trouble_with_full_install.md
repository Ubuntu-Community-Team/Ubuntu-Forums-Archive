---
title: "Trouble with full install"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by Uthallan on 2010-12-15
Hello,

   I'm trying to install Ubuntu 10.10 for the first time, but I have run into several problems. First I find that my disk drive is a pile of excrement, so I am unable to install with a CD. Then i try to make a bootable USB and everything seems to go fine when I create it( I used the universal USB installer that is linked in the Ubuntu.com tutorial) but when I try and boot from it and begin the install it just sits at a screen with the word Ubuntu over some dots changing from white to red, I assume it's a loading bar but eventually the dots stop changing and nothing happens, I have left it for hours and still nothing.

   I have had success with a windows install(I'm using vista by the way) but I would like to just fully install Ubuntu and be rid of vista forever. Is there anything I can do?

---

### Post by oldfred on 2010-12-15
Welcome to the forums.

The designers in their infinite wisdom hid the necessary info you need and modified the graphics driver so it does not work without the info they hid. The little icons at the bottom when you first boot (only for a few seconds) the CD are to tell you to press a key, so then you can press F6.

Many users have to add a parameter to the CD boot and first boot after install because of video issues.

I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Uthallan on 2010-12-16
@oldfred

Thanks for the welcome, I apologize if im being a bit of a noob here but I don't really understand what your telling me at all. I put some comments I had in between **-(These)-** so you could see exactly where i was confused.


"Welcome to the forums.

The designers in their infinite wisdom hid the necessary info you need**-(What info exactly?)-**  and modified the graphics driver**-(How does my graphics driver come into play?)-** so it does not work without the info  they hid. The little icons at the bottom**-(Not sure what you mean here, the loading bar made of dots I described?)- **when you first boot (only for a  few seconds) the CD**-(I cant boot from a CD as a result of a damaged disc drive, sorry if i didn't make that clear)-** are to tell you to press a key, so then you can  press F6.

Many users have to add a parameter to the CD boot and first boot after install**-(Do you mean the windows install?)-** because of video issues.

I had to do this with my Nvidia 9600GT**-(For what reason? does this pertain to my problem? if so i don't know how.)-**
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install**-(I'm confused again, i can't install in the first place so how can i do any of this?)-**, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/...up-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0"

---

### Post by C.S.Cameron on 2010-12-16
I had the problem you describe trying to install Ubuntu on a computer with only 256MB RAM, this is not enough.

---

### Post by Uthallan on 2010-12-16
> **C.S.Cameron said:**
> I had the problem you describe trying to install Ubuntu on a computer with only 256MB RAM, this is not enough.

I have 2gb of RAM, and the flash drive i tried to use for the install was 32gb. I dont think space is the problem.

---

### Post by C.S.Cameron on 2010-12-16
You might try Startup Disk Creator from the Live USB or UNetbootin, sometimes one works while the others don't.

---

### Post by oldfred on 2010-12-16
The info you need is some instructions to add a parameter to the boot long before you even get to the moving dots stage.

The parameter is to modify how the system starts using the default video modes/driver. Many systems are not starting without a parameter.

With CD and I thought with Flash (I do not use standard config so I do not know for sure), is a quick icon at the bottom of the screen. On mine I could not even tell what it was until some explained it is a small stick figure and a keyboard, telling you to press a key if you have problems. If you press a key you get options one of which is F6 which lets you choose boot parameters. I gave my example with Nvidia since many have Nvidia, but also gave the other parameters most commonly used.

Once you do install, you still have to manually add the same parameter to boot the first time and how you boot is standard grub menu. I gave instructions on how to edit grub menu to add parameter. Then you can install drivers once booted and should not need parameters.

The other most common problem is a bad download of the ISO. Have you checked its md5sum?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

