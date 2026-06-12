---
title: "Help! Fresh Lubuntu 16.04 install won't start"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by Ivna on 2016-04-26
Hello, I'm totally new to Ubuntu. I have an old netbook (Samsung N145  Plus) that was extremely slow on Windows 7 starter. I've decided to try  Ubuntu for the first time yesterday. I've followed Lubuntu's  instructions to the simple USB install, and did a fresh install  yesterday, the one that formats the disk before installing. Everything  went smootly on the installation, but after the reboot, it never booted.  The only phrase that it shows is:

"/dev/sda1: clean, 121563/920272 files, 701079/3680256 blocks"

If I hold shift, I get the Grub menu and I can boot in recovery mode.  I've tried all of the options there, although I couldn't start the  network to or update the packages on the package checker, but I've tried  the Grub update and file check with no success. If I resume the boot, I  can boot and login (I'm using this netbook to post here). I tried to  update the drivers, I get an Unknown Device that was disabled, I've  selected the proprietary driver for it, still the same message. I wonder  if it is the Graphics, since on this netbook the Graphics is inside the  processor? I've installed the SysInfo package and nothing seems out of  the norm. 
Since I'm pretty new to this, please post any instructions with  details... If you ask me to open the terminal at the recovery or  installation media please say how and from where, for example... 

Thank you,

Ivna

---

### Post by navarro2 on 2016-04-27
I am running into the same problem on a old Dell desktop. It probably has to do with those darned video drivers.

This problem sounds similar to the one here: 
[http://askubuntu.com/questions/383636/12-04-3-can-start-only-after-press-resume-in-rescue-mode-every-boot-proble/391608#391608](http://askubuntu.com/questions/383636/12-04-3-can-start-only-after-press-resume-in-rescue-mode-every-boot-proble/391608#391608)

Seems like one of the simpler solutions is to boot into recovery and use the "nomodeset" option.

This is completely ridiculous to have to do on a LTS that is supposed to be an entry for new users. When will the video driver nightmare for linux end?

---

### Post by Bucky Ball on 2016-04-27
@Ivna: Welcome. As suggested above, try the 'nomodeset' option in a recovery session. If you can't work out how, please post back. That is probably the *simplest* solution. 

@navarro2: Never had an issue, unless you consider the 'nomodeset' tweak on an older machine I had an issue, but then, have always been lucky enough to have hardware that is compatible with Ubuntu. ;)

Rather than lament Ubuntu's shortcomings when it comes to GPU, why not clear your mind and set your sights in the right direction: hardware manufacturers. What exactly do you expect Canonical or Ubuntu devs to do about GPUs that come with no Linux compatibility, no code and no drivers from the manufacturer? 

Moan at hardware manufacturers, not here. I encourage it. If you have hardware that doesn't work with Linux, let the creator of that hardware know you're not happy.

Rant complete. Did nomodeset work?

---

### Post by Drimux on 2016-04-27
I've got exactly the same problem here, on several old computers (with no GPU), especially Samsung NC10 and Acer Aspire One Happy.

Although Lubuntu 15.10 works like a charm, 16.04 doesn't want to boot stuck on 
```
/dev/sda1: clean, xxx/xxx files, xxx/xxx blocks
```

I tried to install Ubuntu MATE: no problem to boot!
What a pity for a LTS. :(

Edit: the *nomodeset* seems to work but (of course) resolution is bad.

---

### Post by navarro2 on 2016-04-27
Been with Ubuntu since 8.10, I have nothing but love for the OS and have had my fair share of frustration with the nVidia and hardware manufactures in general.

This release is the first time I've come to a dead halt immediately upon a fresh reboot because of a video card issue. Usually I get these issues after messing with the proprietary drivers; like others have said, 15.10 and other versions have been fine.

I hope this issue is resolved and put upstream soon.

---

### Post by kamiloxnumetal on 2016-04-27
Check this i created a bug report


[https://bugs.launchpad.net/bugs/1575460](https://bugs.launchpad.net/bugs/1575460)


it seems video drivers are not installed by default  (intel for me)

workaround is change to a terminal (CTRL+ALT+F1)  
and install drivers

xvideo-xorg-video-intel for me...

---

### Post by FakenMC on 2016-05-03
> **kamiloxnumetal said:**
> Check this i created a bug report


[https://bugs.launchpad.net/bugs/1575460](https://bugs.launchpad.net/bugs/1575460)


it seems video drivers are not installed by default  (intel for me)

workaround is change to a terminal (CTRL+ALT+F1)  
and install drivers

xvideo-xorg-video-intel for me...

This worked for me. However, the correct package is:

xserver-xorg-video-intel

Best regards

---

### Post by ghfm2 on 2016-05-03
I had exact same problem - fresh lubuntu 16.04 install today on an old compaq celeron machine, but after install completed I was left with the /dev/sda1: clean..... message when trying to boot.  Seems to be that the video drivers were not installed or wouldn't load, but the fix described above worked me: 
Basically,
-hold down shift while booting to access boot options menu, 
-boot in recovery mode, 
-open a terminal window (ctrl-alt-t), 
-type sudo apt get-update (enter password when prompted) 
-type sudo apt get-install xserver-xorg-video-intel
-reboot

I guess this will only work if you have an intel shared video card, but I suspect the process should be the same for other video chipsets - just download the appropriate drivers instead of the intel ones

cheers

---

### Post by roler2 on 2016-05-04
Oh geez. . .many many posts applicable to the same issue(s), both for NVidia and especially Intel. From my understanding, the Developers have known about these Kernel/Graphics issues since 14.04.2. Another issue that has developed is that the same Kernel/Graphics issues have worsened, especially with 16.04. I still don't understand why the default 3.13 Kernel was not utilized until a Kernel fix was established.

The above solution is a temporary one. Actually you are better off shutting down completely and then a cold restart rather than a reboot. You also do not need to do an update, just the Intel install. You will not get very good Graphics at all. Poor font rendering. Some Desktop freezes. Update problems as well. A few error messages (just uninstall apport). Sometimes Firefox freezes and web page scrolling is subject to freezes. Programs may freeze. I am also running Lubuntu and have a very old P4, however the OS is at least able to function somewhat as a secondary OS, not as primary.

---

### Post by EowynCarter on 2016-05-04
I see I'm not the only one feeling disheartened by theses issues. Was fixed,  then an update broke it again.... 
It used to work for crying out loud!

---

### Post by Locane on 2016-05-13
If you're only using Ubuntu in a CLI, **just push Alt + F1**.

---

### Post by Eventvwr on 2016-05-14
Same here. My first try of Lubuntu. Installing on a Sony Vaio VGN-TX2HP

I'm looking at the screen which says "/dev/sda1: clean,121493/............." and wondering how to get from there to a working system.
The only practical thing I understood from the posts previously was press Ctrl - Alt - F1 ... but that doesn't open a terminal for me. Trying to decide if googling how to install video drivers to a non-working system would get me going quicker than downloading and installing a different distro. I guess I should try them in parallel

> **Locane said:**
> If you're only using Ubuntu in a CLI, **just push Alt + F1**.
I do this but it changes back to the /dev/sda1 screen quicker than I can enter my password

I'm going through the thread again, thanks Ivna because this has got me logged in:

> **Ivna said:**
> 
[...]hold shift, I get the Grub menu and I can boot in recovery mode. [...]
 
[...]If I resume the boot, I  can boot and login [...]

And since this has been raised:

> **Bucky Ball said:**
> Rather than lament Ubuntu's shortcomings when it comes to GPU, why not clear your mind and set your sights in the right direction: hardware manufacturers. What exactly do you expect Canonical or Ubuntu devs to do about GPUs that come with no Linux compatibility, no code and no drivers from the manufacturer? 
[...]

I could be wrong, but this doesn't seem like an issue caused by hardware manufacturers. If it works when resuming from recovery mode then why not make that the default option if there is no better driver available?

Cheers
E

> **ghfm2 said:**
> I had exact same problem - fresh lubuntu 16.04 install today on an old compaq celeron machine, but after install completed I was left with the /dev/sda1: clean..... message when trying to boot.  Seems to be that the video drivers were not installed or wouldn't load, but the fix described above worked me: 
Basically,
-hold down shift while booting to access boot options menu, 
-boot in recovery mode, 
-open a terminal window (ctrl-alt-t), 
-type sudo apt get-update (enter password when prompted) 
-type sudo apt get-install xserver-xorg-video-intel
-reboot

I guess this will only work if you have an intel shared video card, but I suspect the process should be the same for other video chipsets - just download the appropriate drivers instead of the intel ones

cheers

Not sure why I missed this when reading the thread the first time, but this pretty much fixed the issue for me. Only thing is the hyphen in apt-get looks wrong. I suggest:

>  
-type sudo apt-get update (enter password when prompted) 
-type sudo apt-get install xserver-xorg-video-intel


Cheers
E

---

### Post by mörgæs on 2016-05-15
> **Eventvwr said:**
> 
I could be wrong, but this doesn't seem like an issue caused by hardware manufacturers. If it works when resuming from recovery mode then why not make that the default option if there is no better driver available?


Correct, Intel has always supported open source including Linux. The error is on the Lubuntu side: The Lubuntu developers didn't include a package containing essential Intel drivers for 16.04 and the testers didn't catch it. The other Buntus are fine.

The workarounds here in the thread are good (adding the missing packages) or acceptable (nomodeset gives a performance hit). Another option is described in the Old Hardware link in my signature (look for the text in red).

---

### Post by Xubuntist on 2016-05-27
Same for me ](*,)on a brand new Lubuntu 16.04 install on an old HP desktop Pentium 4 i386 dinosaur. The following worked for me to get out of the fsck loop:

[LIST]
[*]Hold down shift while booting to access boot options menu 
[*]Select recovery console 
[*]Enable networking 
[*]Select Administrator Root terminal

# sudo apt-get update*
# sudo apt-get install xserver-xorg-video-intel 
[/LIST]
 
[LIST]
[*]Select Continue Normal boot. 
[/LIST]
 * doesn't ask for password which is lucky because us-en keyboard is loaded, my install and pwd use azerty accent chars (rush off to check out character map on another pc!!!)

Now the system booted correctly into the desktop but a crash window informed me of obsolete dependencies (is that common for a LTR distro I downloaded only yesterday?)

Opened terminal and did:
#sudo apt-get update && sudo apt-get upgrade

Restarted and now Lubuntu starts without a hitch. Thank you to those who set me on the right path \\:D/

---

### Post by sudodus on 2016-05-27
There are alternatives to get Lubuntu 'directly' with **xserver-xorg-video-intel** for some old and middle-aged Intel graphics chips.

1. Install from a tarball with the One Button Installer

2. Install from a compressed image file with Lubuntu or a mini system (text only) with mkusb, and when it is running, install Lubuntu desktop or Lubuntu Core.

***32-bit:***

**Lubuntu_16.04_oem-intel.tar.xz **        # tarball in OEM mode, password: 123456, (up to date 2016-05-08)

[dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB.img.xz) (32 bits, BIOS mode)

See these links,

[New Lubuntu tarballs and compressed image files with 'xserver-xorg-video-intel' for Intel graphics](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13487384#post13487384)

***64-bit:***

**Lubuntu_16.04_oem-intl_amd64.tar.xz**    # tarball in OEM mode, password: 123456, (up to date 2016-05-14)

[dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB_amd64.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB_amd64.img.xz) (64 bits, BIOS mode)

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260)

-o-

The One Button Installer: [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

mkusb: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by vparasch on 2016-06-28
It's been 2 months since this thread, and the associated bug ([https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460)), was reported. 
Does it mean Lubuntu distribution is not well maintained? 

I'm new to linux. I'm just lucky I had access to a second computer to come to read the help here, after my laptop stopped during the lubuntu install.

---

### Post by sudodus on 2016-06-28
Welcome to the Ubuntu Forums :-)

It is easy enough to install the package xserver-xorg-video-intel in an installed system. The problem is the iso files. They are only released at fixed intervals. The next release will be near the end of July: Lubuntu 16.04.1 LTS, and we hope and expect this bug to be fixed in those iso files. Until then, we must live with the work-arounds for this bug.

-o-

By the way, I am working right now on an updated tarball for the 32-bit system. It will make it convenient to get a system that is completely up to date today (June 28, 2016). I intend to upload it soon, but the files that I linked to in my previous post are still useful.

***Edit:*** See these links

[One Button Installer, 'OBI'](http://ubuntuforums.org/showthread.php?t=2172971)
[Updated system to install [Ubuntu flavours of] Xenial alias 16.04 LTS](http://ubuntuforums.org/showthread.php?t=2172971&page=3&p=13510660#post13510660)

---

### Post by Bucky Ball on 2016-06-28
@vparasch: Welcome. If you need further help with Lubuntu you would be better advised to improve your chances by posting a new thread outlining your issues rather than resurrecting someone else's. Good luck with it.

---

### Post by elpak on 2016-06-30
is MATE working smoothly than Lubuntu?

---

### Post by sudodus on 2016-06-30
Lubuntu has the lightest foot-print. It means that it works smoothest in computers with low RAM and with weak CPU and GPU. But with middle-aged computers, both flavours, Lubuntu and Ubuntu MATE, and also Xubuntu, work very well. Try them live and settle with the flavour you like the best.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by angelo16 on 2016-07-08
Just my 5 cents...

Yesterday I decided to update my lubuntu 15.10 and guess what did happen ? Stuck for over 3 hours.... Then after give up I went to another computer and came here... oh ok, I am not alone !!! Let´s download the file released here... ok, downloaded and for some reason I was not so sure if the 7.8Gb in the filename was correct or a joke... but it is ok. lets go ahead...

Damn it..... it is a 680 mb download, something should be wrong with the filename and Lubuntu does fit on 1GB ... let´s go.....for sure it is a mistake....

Oh...oh...
It is a DVD-DL image ! ok.... I gave up.... 

Let´s try Ubuntu Mate.....

Yes... Ubuntu Mate installed without a problem. 


It is a pity that Lubuntu has this problem, because I learned to love this Ubuntu flavor.

---

### Post by mörgæs on 2016-07-09
If you have a working Mate installed you can add the Lubuntu packages using the command ```
sudo apt-get install lubuntu-desktop
``` This way you will have two desktop environments to choose from at boot time.

---

### Post by sudodus on 2016-07-09
> **angelo16 said:**
> Just my 5 cents...

Yesterday I decided to update my lubuntu 15.10 and guess what did happen ? Stuck for over 3 hours.... Then after give up I went to another computer and came here... oh ok, I am not alone !!! Let´s download the file released here... ok, downloaded and for some reason I was not so sure if the 7.8Gb in the filename was correct or a joke... but it is ok. lets go ahead...

Damn it..... it is a 680 mb download, something should be wrong with the filename and Lubuntu does fit on 1GB ... let´s go.....for sure it is a mistake....

No it is not a joke. You are referring to links from [post #15](http://ubuntuforums.org/showthread.php?t=2322111&p=13495771#post13495771). These links refer to compressed image files of installed systems. They contain ***portable installed systems***, not iso files with an installer. The compressed image is smaller than 1 GB, but during installation they are extracted to installed systems that use 7.8 GB on the target drive. The reason for 7.8 GB is that the system should fit in 8 GB pendrives, and some of them are 'undersized', slightly smaller than 8 GB.
> 
Oh...oh...
It is a DVD-DL image ! ok.... I gave up.... 

Let´s try Ubuntu Mate.....

Yes... Ubuntu Mate installed without a problem. 

It is a pity that Lubuntu has this problem, because I learned to love this Ubuntu flavor.

Congratulations :KS to a working installation. If you are happy with Ubuntu MATE, continue to use it, or maybe add the Lubuntu desktop environment as suggested by *mörgæs*, and you can switch between them by selecting 'session' at the log in screen :-)

-o-

But if you are curious, and if you have a free USB pendrive or another drive (HDD, SSD, SD card ...) of at least 8 GB, you can use [mkusb](https://help.ubuntu.com/community/mkusb) and install a system from the downloaded compressed image file (a file with extension **.img.xz**). If the drive is larger than 8 GB, it is easy to move the swap partition and grow (alias expand) the root partition afterwards with ***gparted***.

---

### Post by fredriley on 2016-07-16
As I've had exactly this problem when trying to install Lubuntu 16.04 LTS to an old machine of a friend's (Intel Centrino, which shows how old it is), I've read this thread in detail but sadly with some frustration. A major problem with all the apt-get instructions is that, if there's no networking, it naturally fails. So I try to install networking from the Grub recovery options, and it stops dead at "Reached target Swap". There was no prompt for networking during the installation, and of course as the boot fails as the /dev/sda: etc stage there's on option to install it then. 

So I'm two hours in to what should have been a wash-n-go installation (I've put Ubuntu on other more recent machines painlessly), and now I'll have to redo the installation and hope for the best, and if that fails then physically throw the machine away unless someone can suggest another Linux distro which would a) work, and b) have a GUI friendly to naive users like my friend.

Whilst I can see the sense of the earlier rant about hardware vendors, this has been a continual problem with Linux going back well over a decade. I recommend to my friends, when their Windoze machines come to the end of their Windoze lives (my friend's has eXtra Pathetic which Microsh1te no longer supports), that they install Linux to save throwing good hardware away. If they're going to run into problems like this, which even I as an experienced Unix hand am struggling with, they're just not going to bother. If the installation isn't wash-n-go then they're not going to go into Grub or a terminal window and type abstruse Unix commands, and I don't blame them. And that's my rant over with ...

Fred

The video driver works, but the commands should be prefixed with apt-get.

As a quick update, I finally managed to get the GUI loading from recovery options by choosing "resume normal boot", then I was able to configure networking and run the apt-get commands for update and the intel driver. So, after 3.5 hours and much restarting, faffing with grub, Net searching, and command-line fiddling, I've finally managed to get Ubuntu on to the old machine which has saved it from the tip. However, a naive user who doesn't know Unix from a Twix would have given up a long time ago, so it would be really helpful were the next Lubuntu i386 version to incorporate the required video drivers. I know, I know, video drivers are the root of all evil (second only to printer drivers), but users rightly expect wash-n-go these days, and I really want to encourage people, for environmental reasons if nowt else, to extend the lives of their old tin boxes.

---

### Post by sudodus on 2016-07-16
Welcome to the Ubuntu Forums *fredriley* :-)

Lubuntu and the other community flavours of Ubuntu (in other words all flavours except standard Ubuntu) are 100% developed and tested by volunteers. Please help us make them better, for example by testing the daily iso files before a new version is released.

Visit the iso testing tracker at

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

and help reporting bugs at

[https://launchpad.net/](https://launchpad.net/)

---

### Post by mörgæs on 2016-07-17
Hi Fredriley, I understand that you are disappointed with Lubuntu 16.04. It used to (and should) be a matter of 20 minutes without googling to install Lubuntu, but this is what happens when a very small group of people develop and test the release. It's a matter of hands and eyes.
 
We all hope that 16.04.1 will be fixed but if you want an easy solution now you could consider Bodhi Linux or another lightweight distro.

---

### Post by gregostrike on 2016-12-30
Hello !
This post might help those who still encounter this problem..

I encountered the same problem and  have to say I was getting crazy because I just installed the distro and configured everything before I ran an "apt-get dist-upgrade" .
I guess something went wrong while installing the upgrade. 

So at the boot, I switched on GRUB to "advanced options --> Recovery mode" to load the failsafe config.
Then I ran an "apt-get install -f" and an "apt-get update" and finally an "apt-get dist-upgrade".

It solved the problem for me so it is likely that there was a problem during the previous installation.

Regards, 
Grégoire

---

### Post by Bob_Baker_Jr. on 2017-10-25
Just wondering:

Why is it that Lubuntu is capable of properly utilizing the display when installing/trying Lubuntu, but once installed, suddenly has no way to display the Desktop Manager? I mean, clearly there was a working driver of sorts within the installation media, but it doesn't carry over?

I first installed Lubuntu on an old Dell Latitude D-610 a couple days ago, but it wasn't connected to the internet for updates during installation. I'm going to reinstall now with internet connected and get the updates to see if this bypasses the problem initially. If it still doesn't work, then I suppose I'll just have to install them manually after it reboots.

EDIT: To clarify, I installed Lubuntu 16.04.3 LTS, not just 16.04... You'd think that this issue might have been resolved by this time...

UPDATE: After freshly reinstalling Lubuntu 16.04.3 LTS and having the updates be installed simultaneously (also included third-party software choices as well), it seems to make no difference. Going manual.

---

### Post by sudodus on 2017-10-26
We can ask why, but get no answer. Instead we can ask how, and find a solution or at least a work-around.

Try with the boot option **nomodeset**, and after that install a proprietary graphics driver.

See this link

[Boot options](https://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

If still problems, you might try with 16.04.1 LTS with the xenial kernel (linux kernel series 4.4). It might work better with your computer's hardware. See this link,

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

---

### Post by mörgæs on 2017-10-26
I happen to be running a D610 now. The command ```
sudo lshw -C video
``` yields 

```
*-display               
       description: VGA compatible controller
       product: RV370/M22 [Mobility Radeon X300]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:26 memory:d0000000-d7ffffff ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfd00000-dfd1ffff
```

And yours?

Please post the results in CODE tags.

---

