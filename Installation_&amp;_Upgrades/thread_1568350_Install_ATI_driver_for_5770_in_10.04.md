---
title: "Install ATI driver for 5770 in 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by RCXtest on 2010-09-05
Does anyone know how to install the video driver for a ATI HD5770 video card in 10.04?

It was working, some recent update screwed it up, now I cannot reinstall it.

What do you have to delete in order to fully get rid of the remnants of the old driver?

What packages have to be installed before or after though Synaptic?

Are you supposed to install it by downloading the driver from ATI and SHing it?

Or are you supposed to go though System->Hardware Drivers?

Thanks

---

### Post by Cypress421 on 2010-09-05
This site has the info you need:
 
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
 
The idea is to only use the built in drivers.

---

### Post by RCXtest on 2010-09-05
Ok, I had seen that and wanted to run the ATI driver, as I had going before this happened.

But I will work though this page and see if I can get my display working properly again.

Thanks.

---

### Post by needastick on 2010-09-05
Have you by any chance recently upgraded to 10.04? I'm asking as I too have just been having trouble with the 5700 drivers, a little worse than yours I think(later post). Most of my issues seemed to stem from the updated repositories which were duplicated in my 64bit set up and caused conflicts. It eventually partially installed when I removed them.

---

### Post by RCXtest on 2010-09-05
I upgraded at least a month ago. Had no problems until I rebooted Friday. I rarely reboot. Some recent update screwed up the ATI driver.

Now I cannot install ANY video driver, ATI or open source Radeon.

---

### Post by RCXtest on 2010-09-05
> **Cypress421 said:**
> This site has the info you need:
 
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
 
The idea is to only use the built in drivers.


Well I went through the instructions for uninstalling and loading the proprietary driver and no go. Only low res mode available.

When I run 'fglrxinfo' is gives segment fault error.

I'll try the instructions on the other page for the RadeonHD driver and see if it installs.

---

### Post by RCXtest on 2010-09-05
Nope, no driver will load and allow me to run in a normal resolution.

Any options other than pretending this is Windows and reinstalling? Can anyone tell me how to install the ATI driver for 5770 card in 10.04?

---

### Post by SeePU on 2010-09-06
Follow very carefully these pages:

[http://www.phoronix.com/forums/showthread.php?t=25866]("http://www.phoronix.com/forums/showthread.php?t=25866")

[http://mariusbalaban.net/2010/08/installing-ati-catalyst-display-driver-10-8/]("http://mariusbalaban.net/2010/08/installing-ati-catalyst-display-driver-10-8/")

These are discussions, notes and instructions for installing the Catalyst 10.8 driver.  I don't know how well the card will perform after that driver as I don't have one of the Evergreen cards.

However, that is what I found after a google search.  

I would try following those pages and see if you can install that driver.  The 10.7 driver would be similar but not sure if it's on the AMD/ATI page.  Make sure you have the downloaded ATI/AMD Catalyst 10.8 driver and give it a try?

---

### Post by aowdnmp on 2010-09-06
i have the same video card..download the latest driver from ati website, install it as root, then run:

*sudo aticonfig --initial -f to configure xorg*

reboot

---

### Post by RCXtest on 2010-09-06
> **SeePU said:**
> Follow very carefully these pages:

[http://www.phoronix.com/forums/showthread.php?t=25866](http://www.phoronix.com/forums/showthread.php?t=25866)

[http://mariusbalaban.net/2010/08/installing-ati-catalyst-display-driver-10-8/](http://mariusbalaban.net/2010/08/installing-ati-catalyst-display-driver-10-8/)

These are discussions, notes and instructions for installing the Catalyst 10.8 driver.  I don't know how well the card will perform after that driver as I don't have one of the Evergreen cards.

However, that is what I found after a google search.  

I would try following those pages and see if you can install that driver.  The 10.7 driver would be similar but not sure if it's on the AMD/ATI page.  Make sure you have the downloaded ATI/AMD Catalyst 10.8 driver and give it a try?



I read though it and it is the same instructions as [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)  which I have tried without any luck.

Thanks for replying anyway.

---

### Post by RCXtest on 2010-09-06
> **aowdnmp said:**
> i have the same video card..download the latest driver from ati website, install it as root, then run:

*sudo aticonfig --initial -f to configure xorg*

reboot


How do you install the driver?

Run the 'ati-driver-installer-10-8-x86.x86_64.run' file that you download from ATI website?

I have done that 3 or 4 times, 2 different downloads. It goes though the install, and when I run '[I]sudo aticonfig --initial -f' it says 

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

[/I]Then what?????

It does not DO anything, I can still only boot into safe mode.

The problem is, I do not know how to install the driver.

I can download it and run it, I can load packages though Synaptic, I can load Jockey and try to 'activate, it.

But I do know HOW to install the driver. Nothing DOES anything.

After running the download from ATI, and then running '*sudo aticonfig --initial -f',* I can still only boot into safemode. I cannot change the monitor resolution though SYSTEM->PREFERENCES->MONITORS as I get

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

If I click YES I get

"There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

---

### Post by SeePU on 2010-09-06
> **RCXtest said:**
> I read though it and it is the same instructions as [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)  which I have tried without any luck.

Thanks for replying anyway.I know but I am aware that the Ubuntu documentation on that page is NOT up to date.  I wish the Ubuntu forum admins or whoever presents that info would UPDATE their 'community documentation' pages.  It's so often that those kind of pages are outdated or inaccurate.

The open source drivers for your card, the HD 5000 series aka Evergreen cards are not ready yet.  They should be, considering it's been practically a year since their release.  But, ATI won't invest in the resources to support the cards.  Imho, they are not putting enough resources into A) supporting the open source drivers leaving only a few people to do it and B) supporting the binary driver which lacks features also and is plagued with issues - it's a shame when ATI has such good hardware but provides drivers not up to par compared to the Nvidia drivers of equivalent Nvidia cards.

Anyway, check these pages:
[http://www.x.org/wiki/radeonhd:feature]("http://www.x.org/wiki/radeonhd:feature")
[http://www.x.org/wiki/RadeonFeature]("http://www.x.org/wiki/RadeonFeature")

As you can see, the radeonhd driver is not ready for the Evergreen cards and probably won't be any time soon.  The radeon driver might be one day.  However, it should, in theory, work out of the box but it's not in a 'functional' state either.  The 3D part of the driver isn't ready.  Not sure how 2D will really work with it but the page implies 2D should work?

Anyway, that's why I gave you the two previous links outlining setup with the Catalyst FGLRX driver.  I recommend you try that for now.

---

### Post by Tracy177 on 2010-09-06
that are the right steps
 
1 download catalyst for your card from amd check up if you got the right one
 
2 after you downloaded it run it as an administrator
 
3 window will pop up click auto next next and everything will be installed in few sec
 
4 reboot ubuntu 10.04 if it will boot in low resolution reinstall your driver
 
5 reboot if again in low resolution reinstall again
 
 
thats how it worked on my laptop ati hd4850 i had to reinstall it few times to get it working
 
to check up if catalyst was installed and driver is working type in terminal fglrxinfo
 
also you will be able using aticonfig to change many things in your card also see gpu load and gpu temp 
 
good luck
 
and there is no need to reinstall or remove any drivers before u install catalyst

---

### Post by SeePU on 2010-09-06
> **RCXtest said:**
> I read though it and it is the same instructions as [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)  which I have tried without any luck.

Thanks for replying anyway.Btw, how do you figure it's the same as the two 'how to' links I gave you?  Those links describe the fglrx binary driver install and the community help page of the RadeonHD is an open source driver install method.  

Those are totally DIFFERENT drivers and a totally different driver design.  One is binary and closed source and the other is open source so there's a lot more integration with code, that kind of thing.

You want to do two things:

1) use the downloaded AMD/ATI Linux driver from the website.
2) use the two links I gave you and if you still need guidance, google 'catalyst fglrx driver' + Ubuntu 10.04 and get the LATEST links - use a Google search for the latest hits.  The instructions should be most up to date and applicable to the current problem.

---

### Post by SeePU on 2010-09-06
Make sure the latest 'fglrx-installer' package in your Ubuntu 10.04 system is AT THE LATEST VERSION 2:8.762-0ubuntu0sarvatt~lucid.

[http://www.ubuntuupdates.org/packages/show/202833](http://www.ubuntuupdates.org/packages/show/202833)

[http://www.phoronix.com/forums/showthread.php?t=25677](http://www.phoronix.com/forums/showthread.php?t=25677)

What the other guy is saying should work as well.  Well, I'd put 'work' with an asterisk or disclaimer... ;)

---

### Post by aowdnmp on 2010-09-06
> **RCXtest said:**
> 
How do you install the driver?
Run the 'ati-driver-installer-10-8-x86.x86_64.run' file that you download from ATI website?




[LIST]
[*]sudo sh ati-driver-installer-10-8-x86.x86_64.run     //start the installer
[/LIST]


[LIST]
[*]after that execute: sudo aticonfig --initial -f     //reconfigure xorg with the driver just installed
[/LIST]


[LIST]
[*]reboot
[/LIST]
 
that works for me.

---

### Post by RCXtest on 2010-09-06
> **SeePU said:**
> Btw, how do you figure it's the same as the two 'how to' links I gave you?  Those links describe the fglrx binary driver install and the community help page of the RadeonHD is an open source driver install method.  




There is a link on that page to another page on how to install Catalyst 10.8 driver. Instructions are the same as the phoronix post.

By 'fglrx binary driver' do you mean the ATI driver?

---

### Post by RCXtest on 2010-09-06
> **SeePU said:**
> Make sure the latest 'fglrx-installer' package in your Ubuntu 10.04 system is AT THE LATEST VERSION 2:8.762-0ubuntu0sarvatt~lucid.

[http://www.ubuntuupdates.org/packages/show/202833](http://www.ubuntuupdates.org/packages/show/202833)

[http://www.phoronix.com/forums/showthread.php?t=25677](http://www.phoronix.com/forums/showthread.php?t=25677)

What the other guy is saying should work as well.  Well, I'd put 'work' with an asterisk or disclaimer... ;)


Do I get the 'fglrx-installer' through Synaptic Package manager? When I search for it it comes up with one choice, just 

"fglrx 2:8.723.10ubuntu4  Video driver for ATI graphics accelerators"

How do I get the one you are referring to?

---

### Post by SeePU on 2010-09-07
> **RCXtest said:**
> Do I get the 'fglrx-installer' through Synaptic Package manager? When I search for it it comes up with one choice, just 

"fglrx 2:8.723.10ubuntu4  Video driver for ATI graphics accelerators"

How do I get the one you are referring to?
Follow these links to install this package:
fglrx-installer (2:8.762-0ubuntu0sarvatt~lucid)

[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=lucid](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=lucid)

[http://www.ubuntuupdates.org/packages/show/202833](http://www.ubuntuupdates.org/packages/show/202833)

To install this PPA:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo aptitude update
sudo aptitude install <package name>

EDIT:  so, for e.g., sudo aptitude install fglrx-installer

Maybe it'll give output back that an older one is installed and do you want to replace it?  Answer yes if that happens.  I'm just guessing... I have no idea if that is what happens. :)

I think you need that PPA to get the most up to date package.  Make sure that Xorg/XServer is at 1.8.  

That should give you the latest Catalyst fglrx driver aka ATI binary driver.  That installer might update Xorg/XServer to 1.8xxx (xxx are other numbers) but I'm not sure.  I don't have a HD 5xxx card so I can't try this out with you.  It should work if done as stated on those pages.  I don't know how well the drivers will function, though, as there's mixed reports about the 10.8 drivers.  However, the suggestion is that there's bug fixes so I'd try the latest.

---

### Post by RCXtest on 2010-09-08
andrew@office-desktop:~$ sudo aptitude install fglrx-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "fglrx-installer"
Couldn't find any package whose name or description matched "fglrx-installer"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


So that did not work. But...

I see now that the fglrx in Synaptic is now at version '2:8.762-0ubuntu0sarvatt~lucid'.

I can install the 6 packages that are in the fglrx-installer package that way... I guess.

Then I can try the ATI install script again to install the driver??? Or try to activate though HARDWARE DRIVERS?????

Who knows at this point.

---

### Post by RCXtest on 2010-09-08
[B]andrew@office-desktop:~/Downloads$ sudo aptitude install fglrx-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "fglrx-installer"
Couldn't find any package whose name or description matched "fglrx-installer"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

andrew@office-desktop:~/Downloads$ [/B] 


So that gives an error. But....

Now I see in Synaptic that the fglrx package is at 2:8.762-0ubuntu0sarvatt~lucid.

Sooooo... I can install the 6 packages thru Synaptic. So I did.

Still cannot activate the driver, gives me same error....

So, run the install script:

[B]
andrew@office-desktop:~/Downloads$ sudo sh ati-driver-installer-10-8-x86.x86_64.run
Created directory fglrx-install.2XTBj8
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.762........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.5
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.2XTBj8
andrew@office-desktop:~/Downloads$ [/B]


And that gives an error. Says to see log:

[B]
Creating symlink /var/lib/dkms/fglrx/8.762/source ->
                 /usr/src/fglrx-8.762

DKMS: add Completed.[/B] [B]
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.31-16-generic package.
[Error] Kernel Module : Failed to build fglrx-8.762 with DKMS
[Error] Kernel Module : Removing fglrx-8.762 from DKMS

------------------------------[/B] [B]
Deleting module version: 8.762
completely from the DKMS tree.
------------------------------
Done.[/B]

---

### Post by RCXtest on 2010-09-08
BTW, I installed Windows 7 at same time as Ubuntu about a year ago. Have had no problem with Win7 as of yet.

---

### Post by RCXtest on 2010-09-08
SeePU, thanks for your help trying to get this fixed.

Undecided whether I reinstall 9.10, reinstall 10.04, or format partition ntfs and forget Ubuntu.

---

### Post by SeePU on 2010-09-08
Sorry, like I said I can't say to know how to install as I don't have a card to test.  I just googled and read a few pages I thought might be helpful.

I suggest you go to the Phoronix forum, create an account and post that you're trying to install the latest Catalyst driver for your Ubuntu 10.04 install. 

Provide as much info as you can including kernel version (run command 'uname -r' in terminal console), X.org and XServer version (you can check Synaptic and search for xorg and xserver), the Catalyst version you downloaded, 10.8, and what you've done so far.

There are some very knowledgeable and helpful people in the Forum who have experience with the ATI driver install process.  

I think ATI has a problem on their hands as their Linux install method seems even more problematic than with Nvidia.  I've only installed Nvidia drivers and although they are a PITA, too, I can still say that I eventually succeeded and I installed Nvidia drivers in more than one distro!

Anyway, I highly recommend you post there and/or look around there before giving up and just leaving for Windows.   I wouldn't give up until they're installed correctly.   I would only give up if I was dissatisfied with the functionality of the drivers.

---

### Post by RCXtest on 2010-09-09
Well, I finally got it working.

See this thread for details:

[http://ubuntuforums.org/showthread.php?t=1567158](http://ubuntuforums.org/showthread.php?t=1567158)

Thanks to all who posted help.

Especially SeePU. Your posts kept me working on the problem and not just giving up. And ultimately pointed me to the solution.

Thanks for all YOUR time searching and reading, trying to solve MY problem!

---

