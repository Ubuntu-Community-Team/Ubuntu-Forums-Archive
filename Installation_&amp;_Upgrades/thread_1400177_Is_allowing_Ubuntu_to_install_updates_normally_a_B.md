---
title: "Is allowing Ubuntu to install updates normally a BIG mistake?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Pelgar on 2010-02-06
Is allowing Ubuntu to install updates normally a BIG mistake?

To start I want to point out that I'm pretty new to Ubuntu and Linux. 
I booted Ubuntu 9.10 this morning and had an Update window pop up. Silly me, not knowing any better, told it to go ahead and update my computer. The update took a good while, once it was done it wanted to reboot, I told it OK. The shutdown was normal but booting failed. It filled the monitor with garbage characters and just sit there blinking at me. After a good while I gave up and hit the hardware reset button. The boot went a little better this time but not much, no garbage on screen but a pop up telling me I didn't have graphics drivers or they were corrupt or something along those lines; wish I had written down the exact text but I didn't! I had several choices, boot in low graphics mode, edit this file, edit another file. I took a look at the files but even if I had a clue about what to change I didn't see any way to save changes. I finally booted in low graphics mode and reinstalled my nvidia drivers. It took me about three days to figure out how to install the drivers to start with and only about half a day to reinstall so I guess I'm making some progress.

On to the next problem. I wanted to look at a file on a Windows box and went to Places, Network, Windows Network, MSHOME, selected the Windows computer and was presented with "Unable to mount location, failed to retrieve share list from server". I was able to browse the Windows Network fine before this mornings update. I'm a pretty paient guy so I searched the Ubuntu Forums and found [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) a tutorial by dmizer entitled "Howto: Fix Windows share browsing issues" it seems to be a very good How To, thank you very much dmizer! I followed his steps to solving Problem 2 which seemed the most appropriate for my needs. The last step was to reboot the computer.
I went to close Firefox and was presented with "You are about to close two tabs" instead of the normal "Do you want Firefox to save your tabs for the next time it starts?"!
After finally giving up on getting Firefox to remember my current pages, I reset the computer but still cannot access computers on the Windows Network. 

If the answer to my question, "Is allowing Ubuntu to install updates normally a BIG mistake"
is yes. I vote that Update Manager be renamed to "Auto Self Destruct"!

I have no idea what else I'm going to find. I decided to post this right after I noticed the
change in Firefox.

---

### Post by 2hot6ft2 on 2010-02-06
Normally is safe to update but you can always just close it and wait a few days for any bugs to become evident and fixes made. See the threads on the 2.6.31-19 kernel update which is causing some problems (which is probably what happened to you). Since it required a reboot like you said it did.

I just deselected the kernel updates and updated the rest on this pc earlier.

As for firefox. If there is another window, the download box or an update box and you close it without closing the window, the download box or the update box first it wont ask to "close and save" it will just ask if you want to "close all tabs"

---

### Post by darkod on 2010-02-06
I don't know exactly what happened, but I understand the frustration. Because you said you're new to linux, just to remind you that linux keeps more than one kernel in the boot menu for situations like these. If you dual boot, you are presented with grub menu at start. Instead of letting the default, most recent kernel load, just select an earlier one that worked fine.
If you have only ubuntu, you don't get this menu. But you can make it show by hitting Esc (I think, I always confuse them with Shift, because one is for 9.04 and the other for 9.10) just before ubuntu starts loading. So sometime between BIOS and before ubuntu starts loading. Once it shows the menu, again select earlier kernel to boot.

Once in ubuntu you can even remove the most recent kernel.

---

### Post by lfaraone on 2010-02-06
> **Pelgar said:**
> Is allowing Ubuntu to install updates normally a BIG mistake?

Depends. Updates can fix a variety of problems that range in severity from crashes to UI glitches. 

You have to think: "am I going to evaluate every update before applying it?". If the answer to that question is "no", you might as well have them applied automatically. Personally, I do that for all my workstations. 

On the other hand, if you manage a large Ubuntu deployment in a corporate enviornment, it makes sense to introduce as little change as possible.


> **Pelgar said:**
> 
I went to close Firefox and was presented with "You are about to close two tabs" instead of the normal "Do you want Firefox to save your tabs for the next time it starts?"!
After finally giving up on getting Firefox to remember my current pages, [...]


Can't help you with your Windows problem, bug [http://teck.in/firefox-save-tabs-on-exit.html](http://teck.in/firefox-save-tabs-on-exit.html) has the fix for your tabs issue. This wasn't caused by an update.

---

### Post by Pelgar on 2010-02-06
Too Hot, thanks for the prompt reply and Firefox info, I didn't know that.  I don't think there was a Firefox dialog open when I went to close it but that problem has cleared itself up now!
I'm guessing that Kernel updates are somewhat similar to new DOS versions back in the days before Windows, yes I'm an old goat. I learned my lesson on that one when I upgraded to DOS 4 as soon as it came out. It totally wiped my hard drive out, as it did for a lot of people. My rule of thumb on new operating systems or versions, since then, has been to let them stabilize for at least a year before installing. That is the reason there is not and has not been a Vista box here, heard a lot more bad about than good!
I will remember to uncheck new kernel updates in the future, thank you!

darkod, I am not dual booting but I do have a grub menu at boot. I have two hard drives in my Linux box and have Ubuntu installed on both of them. I use one just for testing out new things I feel may screw up the system. I have a new thing to add to that list now!!!
I had no idea that I could boot into the old kernel though, thank you very much. I may even see if I can roll back to the previous kernel but will play with this one a while yet. It is good to know it can be done.

lfaraone, I currently only have one Ubuntu box but I'm liking it better all the time, most of the time at least. Thanks for the link to the Firefox bug fix, it's odd that I have never ran across it until after this mornings update. 
I will be a bit more cautious with updates in the future.

Thanks you all!!!

---

### Post by Pelgar on 2010-02-06
> just to remind you that linux keeps more than one kernel in the boot menu for situations like these. If you dual boot, you are presented with grub menu at start. Instead of letting the default, most recent kernel load, just select an earlier one that worked fine.

darkod, if you are still around a little clarification would really be helpful. I've never paid much attention to those kernels in the grub menu before, honestly didn't even know they were kernels, I am slowly getting there. It appears that today's upgrade was not my first kernel update. I have 2.6.31.14-generic, 2.6.31.17-generic and 2.6.31.19-generic in the grub menu. I have tried them all and was a bit surprised. The only one that does not pop up an error on boot is the latest! The error is "Failed to load the NVIDIA kernel module! The error has gone in 2.6.31.19 since I reinstalled the Nvidia drivers.
I can only access my Windows network when I boot in 2.6.31.19 now too. I finally fixed the network problem there by implementing step 3 in dmizer's Network Tutor.

I would really like to know if you or anyone else for that matter, thinks that my Nvidia and Network problems starting today were simply coincidence or did the kernel update do this?
I'm really scratching my head now and I don't have enough hair left that I can afford to scratch any off!

---

### Post by foresthill on 2010-02-07
Your problem stems from the fact that you installed third party video drivers that were designed to work only with your previous kernel. If you had not installed these, the kernel update would not likely caused you any problems, at least with respect to your display. 

If you're going to use Nvidia's drivers, be cautious with kernel updates and familiarize yourself with booting up without a GUI and know what to do if this happens again. It gets easier each time you deal with it and while it seems like a big deal for a new user, it's really not that hard to fix once you've done it a few times.

And if you don't want to have to deal with it again, just stick with the stock Ubuntu drivers and kernel updates won't cause these kind of problems.

---

### Post by malspa on 2010-02-07
I don't let Ubuntu install my updates.  I get rid of all that automatic stuff and I go to Synaptic and update what and when I want to.  I've seen a few too many horror stories about Ubuntu updates messing things up.

---

### Post by Pelgar on 2010-02-07
2hot6ft2 said:
> See the threads on the 2.6.31-19 kernel update which is causing some problems (which is probably what happened to you)I would really like to see these threads! Unfortunately I have not figured out how to find them. A search for 2.6.31-19 brings up zero results. Even using Yahoo with 2.6.31-19 site:ubuntuforums.org brings up nothing! Forcing an exact string search, "2.6.31-19 kernel update" site:ubuntuforums.org, still brings up zero results. I'm now at a total loss on this!

ifaraone said:
> Depends. Updates can fix a variety of problems that range in severity from crashes to UI glitches. I'm betting there is some way to find out what these updates are about. Maybe even get some clues as to what they are fixing or even what they are about to do to my computer. If anyone could point me to where this information can be obtained I'd be most grateful.

ifaraone said:
> You have to think: "am I going to evaluate every update before applying it?". If the answer to that question is "no", you might as well have them applied automatically. Personally, I do that for all my workstations.Before yesterdays fiasco I would have probably agreed with you. I will be looking updates over very carefully from now on. To be honest I'm leaning more toward turning updates completely off. 

ifaraone said:
> Can't help you with your Windows problem, bug [http://teck.in/firefox-save-tabs-on-exit.html](http://teck.in/firefox-save-tabs-on-exit.html) has the fix for your tabs issue. This wasn't caused by an update. That site is just telling you how to get Firefox to display the options dialog again if you have checked the "Don't ask me again" box. I have not checked that button, I really like to be asked about keeping tabs when Firefox closes. Sometimes I want them back, sometimes not.

foresthill said:
> Your problem stems from the fact that you installed third party video drivers that were designed to work only with your previous kernel.I spent a couple of hours trying to confirm this at [http://www.nvidia.com]("http://www.nvidia.com/"), where I downloaded my drivers. Please don't get me wrong, I'm not disputing your word but I simply cannot find anything that even implies the drivers are kernel specific! Reinstalling the exact same drivers fixed the problem! I didn't download new ones for the new kernel. This statement is very confusing to me. 

foresthill said:
> And if you don't want to have to deal with it again, just stick with the stock Ubuntu drivers and kernel updates won't cause these kind of problems. I have spent several hours trying to find out how to do just that. I originally installed the Nvidia drivers because I was having problems getting Video out through the S-Video output. Now that I have that working with the Nvidia proprietary drivers I'd really like to go back and see if I could make it happen with the stock drivers. I have no idea how to get them back and have had no luck finding out how.

malspa said:
> I don't let Ubuntu install my updates. I get rid of all that automatic stuff and I go to Synaptic and update what and when I want to. I've seen a few too many horror stories about Ubuntu updates messing things up.I'm really leaning towards a similar approach. If/when I find out how to make some informed decisions.

All of your responses are greatly appreciated.

---

### Post by darkod on 2010-02-07
I'm not that experienced with drivers and in fact ubuntu, but here is my humble opinion:
The drivers you used would never be kernel specific. But just the fact they are from "outside ubuntu" makes it impossible for a kernel update to include them in the newer kernel too. So after you install them again all is good, but until you do, they're not there and not working.
Drivers that are within ubuntu would have no problems being in the updated kernel too.
That's my logic if it makes any sense. :)

Having said that, I actually had to compile and install a driver for mu usb wi-fi adaptor myself, to make it work at max speed. And with all kernel updates since, I never had to reinstall them again. But this might be because the drivers were not available as a ready file, I actually had to compile them myself, hence they would be within ubuntu and kernel update will just keep using them correctly.
Again, this is my understanding which might not be true at all.

---

### Post by P.Forest on 2010-02-07
[FONT=Microsoft Sans Serif]Freeware is alwalys going to be  problematic. [/FONT][FONT=Microsoft Sans Serif]Never look a gift horse in the mouth!

I'm back on XP :mad: because of several problems I've had with both 9.04 **AND** 9.10 (but have everything standard swithched off, & use better freeware). [/FONT][FONT=Microsoft Sans Serif]I allowed Ubuntu to upgrade to 9.10  online, & got an infected 'Krippled Kitten', which sent me back to  XP! ](*,)! I recently got the ISO & burned a proper disc, but still had tomany  problems with 9.10.
[/FONT][FONT=Microsoft Sans Serif]
Nonetheless, I shall persevere towards liberation, whether that be through UNIX, Linux, Plan 9, or 'VX37.285 Gamma'!

Meanwhile I have (Windows) update turned off for a simple reason: my machine is working well, & I keep it clean, use a pro-antivirus & a free firewall, etc., & routinely clear my history & registry to prevent infection.

[B]1: Is your system doing what you want?

2: Is it functioning OK?

3: Does it still make you coffee?
[/B]
If your answer to all 3 questions is yes, then don't upgrade unnecesarily - just because 'they say so' doesn't make it valid. If your answer to question 3 no, then install some fresh beans! :D

Also download a free handbook or two (there are a few available) & learn a little aboot the 'operator's system'. I use 'operator's system' because that's what Ubuntu is. Freeware operators, rather than abject consumers, have to be responsible for our own machines.

Keep the faith, find the freedom!



[/FONT]

---

### Post by Pelgar on 2010-02-07
darkod, Thank you, your explanation was very helpful and made perfect sense to me. I actually don't think reinstalling my video drivers after a kernel update will be a big deal in the future. I would still like to go back and try the stock drivers, if I don't figure out how to do that I will start a new post about it.

P.Forest, You bring up some good points but I'm far from ready or even considering dumping Ubuntu. I do agree about the Windows updates, far to many and to often! 
I also agree that a person should do there homework on an OS before asking a lot of questions. I feel that I have done that, I've read a couple of Linux books from cover to cover, been all over the Ubuntu wiki. It just seem that for every baby step forward I end up taking two or three giant steps backward.
I agree with the gift horse statement too. But if a newbie has to spend years studying an OS before he can even get started something is very very wrong! I saw very early on that I was going to have to get familiar with the Command Line. There is about a 99.99% chance that any help you get will be in the form of a Terminal Command. I located and read [http://en.flossmanuals.net/gnulinux](http://en.flossmanuals.net/gnulinux) which was very helpful. I've also downloaded and studied linux_starter_pack.pdf, God I hate PDF files, and have a good many books bookmarked.
I normally do my homework before asking a question. This "BIG Mistake" question was an exception. I started this post out of pure frustration. I would really like to get started writing software. I finally got to the point, day before yesterday, that I felt I was ready to give it a go. I installed CodeBlocks and built a couple quick test apps and life was good. I was really anxious to get neck deep into learning my way around CodeBlocks yesterday monring. Instead I made the mistake of saying "Yes" when I should have said "No". Been babysitting what appears to be a very finicky OS ever since.

---

### Post by foresthill on 2010-02-07
If you could provide me with a link to the Nvidia drivers you downloaded, I can tell you if they are kernel specific or not. Usually you can tell just by looking at the file name. If there is a kernel version at the end (e.g. 2.6.31-19) then they were designed to work only with the 2.6.31-19 kernel. Sometimes they will still work with other kernels, but you can't count on it.

This is a very common problem. There are dozens of other threads on this same topic arising from this same kernel update.

You could always just back up your files and do a reinstall. That takes all of about 30-45 minutes, and is probably what i would do if I was in your position. Also, where did you get the instructions on how to install the drivers? There should also be instructions on how to uninstall them.

EDIT:  Did you use the Nvidia installer, by any chance, to install your drivers? Because if you used that method, all you have to do is run that a second time and it will build a driver for your specific kernel.

---

### Post by Pelgar on 2010-02-07
Hi foresthill, thanks for the followup. The driver version is 96.43.14 and I downloaded it from [http://www.nvidia.com/object/linux_display_ia32_96.43.14.html](http://www.nvidia.com/object/linux_display_ia32_96.43.14.html).  I sort of bastardized the instructions at [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) to fit my card, an old Geforce4 MX-4000. I could not find any instructions for my old card, what little info I could find was pretty old. It seems that Nvidia still supports the card, even for Linux but if Ubuntu even knows it exist they have it hidden behind some cutie name that doesn't make finding it at all easy.
A clue as to how to backup then reinstall without losing my configs, installed apps, desktop customizations...  would be great. I reinstalled once since starting with Ubuntu, the install took 30 - 45 min., yes but getting back to where I was took days.

I am posting the steps I took to install my video drivers below. This is rather odd too. The first time I did this, before the reinstall, about three four weeks ago, Nvidia had a list of drivers to choose from, with 96.43.14 being the latest and listed as in beta. When I reinstalled I went back to Nvidia and 96.43.14 is the only one they list. I originally installed the 96.43.13 drive but since they had taken 14 out of beta I went ahead and went with it the second time. Just thought I point that out.


Install GeForce4_MX-4000 nVidia drivers:

Open a terminal Main Ubuntu Menu: Applications/Accessories/Terminal

Code:
    cd /

Reset Xorg back to Failsafe Defaults
Before doing anything, it's time to say goodbye to nvidia for the moment and bring back the original Xorg configuration. 
This is done by running:
Code:
    sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
    sudo dpkg-reconfigure -phigh xserver-xorg

Next, we need to be ensured that we have all build-essential programs and our current kernel headers.
Code:
    sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)

Ubuntu and Hardware Drivers
If you run Ubuntu and have an NViDIA card, you more than likely used the 'Hardware Drivers' utility to install them. This can lead to conflicts later down the line, as New drivers/Old drivers will cause API conflicts that will prevent X from starting.
So you are required to uninstall/remove any nvidia modules and references before beginning.
Code:
    sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings

Next, it is a good idea to check to ensure that dpkg shows that there are no extraneous packages left installed on your system.
Code:
    dpkg -l | grep nvidia

If that outputs something, then these package needs removing. Use this aptitude command below to remove/purge them.
Code:
    sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')

Note: In some terminal emulators (hint: xterm) I have been informed that the above doesn't work. If this is the case, run the following instead:
Code:
    sudo aptitude purge $(aptitude search -F%p '~c nvidia' '~i nvidia')

As an optional step, for some people who may find a conflict during installation, removing the xorg-nv drivers beforehand appears to work for them.
Code:
    sudo apt-get --purge remove xserver-xorg-video-nv

Note: following does not seem to apply, file does not exist
    Another optional step, is to disable the nv and nvidia_new drivers from loading too, for those who have     further problems.
    Code:
        gksudo gedit /etc/default/linux-restricted-modules-common

    And on the line that says DISABLED_MODULES="" change it to
    Code:
        DISABLED_MODULES="nv nvidia_new"

Downloading the Drivers

If you are on 32bit Ubuntu, run:
Code:
    wget [ftp://download.nvidia.com/XFree86/Linux-x86/96.43.14/NVIDIA-Linux-x86-96.43.14-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/96.43.14/NVIDIA-Linux-x86-96.43.14-pkg1.run) -O NVIDIA-    Linux-96.43.14.pkg1.run

Now, move the installer to the /usr/src folder and make a link to the file.
Code:
    sudo install NVIDIA-Linux-96.43.14.pkg1.run /usr/src
    sudo ln -fs /usr/src/NVIDIA-Linux-96.43.14.pkg1.run /usr/src/nvidia-driver

Kill X
Now, it's time to stop X and the gdm (or kdm for Kubuntu Users)
This requires that you logout and switch to another tty console ( Ctrl+Alt+F1 ).

Login to the shell, and kill gdm:
Code:
    sudo /etc/init.d/gdm stop

In some rare instances, stopping gdm won't stop Xorg, due to the Xsession being busy with whatever error has occurred (Ubuntu goes into Low Resolution mode, X failed to start, etc).
In these instances, it is required that you run a kill of Xorg before you can continue with the installation of the driver.
Code:
    sudo killall Xorg

Installing NViDIA
****
When asked, double check to ensure you select 'NO' when the NViDIA installer asks to reconfigure the xorg.conf file.
We don't want to change the xorg.conf file just yet, at least not until we are back in X.
****
Afterwards, its time to install the drivers.
Read When asked note above, then:
Code:
       sudo sh /usr/src/nvidia-driver

Note: Once reinstalled, nvidia driver text:
    Installation of the NVIDIA Accelerated Graphis Driver for Linux-x86(version: 96.43.14) is now complete.  
    Please udate your XF86Config or xorg.conf file as appropriate; see the file
    /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details

Once finished, it is now time to reboot:
Code:
    sudo reboot

Before you Initiate the Driver
Now, since NViDIA didn't reconfigure the xorg.conf file, you will boot into the VESA drivers. To setup the xorg.conf file for nvidia, login, open a terminal, and run:
Code:
    sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
    sudo nvidia-xconfig

Note: I did not have a splash screen but if you do:
And if you have had a successful transition, and everything works. The first thing you may notice is a nice new NViDIA splash logo that you probably want to be removed too. If you get this, just run the following:
Code:    
    sudo sed -i '/Section\s*.Screen./a\    Option         "NoLogo" "True"' /etc/X11/xorg.conf

---

### Post by foresthill on 2010-02-07
Looks like you did use the installer. Which is good, because it should be able to build a new driver for your new kernel, provided that the kernel source and other stuff needed to run the installer also matches the new kernel.

It's been a while since i messsed with Nvidia drivers, but IIRC the uninstall command was as follows:

[PHP]nvidia-installer uninstall[/PHP]

This should take just a couple seconds. Then just repeat the procedure you used to install the driver originally and it should build you a driver for your new kernel, provided that all the dependencies are there.

---

### Post by Pelgar on 2010-02-07
foresthill, I had to change your code slightly to get the driver uninstalled. Just thought I'd point it out in case someone else comes along someday with one of these old cards.

```
sudo nvidia-installer --uninstall
```Using uninstall without the -- returned unknown command error, then it would not run without sudo, said it had to be at root. It is now uninstalled, thank you!

Since getting it uninstalled I've been poking around in Synaptic Package Manager and searched for nvidia.  There is a dev pack, kernel-source pack, modaliases pack and a binary pack for the nvidia 96.43.13.
I have no idea what the difference between a dev and source pack may be. The modaliases pack says it ID's your hardware. My guess is that I would install the binary to install the 96.43.13 driver but a confirmation of this would be great.
All of these packs say they are supported by Canonical, whatever that is, until April of 2011. I assume this means the drivers are supported?

---

### Post by foresthill on 2010-02-07
I believe the binary is a driver that is matched to your kernel, that's supplied by Canonical. There should be a X11 file and a G01 file that comprise the driver.

The Synaptics Package Manager should figure out what the dependencies are and install them along with the binary. And once you install this driver, I would assume that future kernel updates would include a new Nvidia driver that matches the new kernel, that is if Synaptics is doing its job properly.

Good thing you installed the old driver first, you don't want multiple drivers installed on top of each other.  

Some people like using the installer, it's sort of the "old fashioned way" of updating your Nvidia driver. I used to use it, but now I just let the package manager figure out the correct driver and hope it doesn't screw up. Call me lazy, but that's how i do it these days.

---

### Post by Pelgar on 2010-02-07
foresthill, Thanks once again, it worked! I selected the binary in Synaptic, then let it install all the dependencies and I have Nvidia drivers once again!
It took me a while to find the driver GUI. When I had the packs from Nvidia installed I went to the GUI via Applications/System Tools/Nvidia Settings. I finally found it after the Synaptic install under System/Preferences/Display which brings up an error dialog with a button that will bring up my Nvidia Setup GUI. Seems a bit of a round about way of getting there but heck it works. Great!!!
I guess we'll see what happens next time the kernel is updated!
Hey, I really appreciate the help.

---

### Post by foresthill on 2010-02-07
I don't think I was really all that much help. If you went through all the steps to get that installer to work, then you must know something.

BTW, there is a quick terminal command that will get you straight to the Nvidia applet:

nvidia-settings

---

### Post by Pelgar on 2010-02-08
foresthill, you were a lot more help than you think and I really appreciate it. Most of those steps were from ibuclaw's excellent How To on installing Nvidia 185.18 drivers at [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) I simply modified his code to install the 96.43.14 drivers.  The terminal command, nvidia-settings, works great, thanks again.
Now I just need to figure how how to create a link to it where I want it.

---

### Post by P.Forest on 2010-02-08
Many thanks Pelgar for the linx, which led to many more treasures!

---

### Post by wojox on 2010-02-08
> **Pelgar said:**
> foresthill, you were a lot more help than you think and I really appreciate it. Most of those steps were from ibuclaw's excellent How To on installing Nvidia 185.18 drivers at [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) I simply modified his code to install the 96.43.14 drivers.  The terminal command, nvidia-settings, works great, thanks again.
Now I just need to figure how how to create a link to it where I want it.

Pelgar scroll down to " Keep in sync with kernel updates ". This will keep your drivers from borking up on kernel updates. I used that same HowTo.

---

### Post by achandler on 2010-02-08
Although not fully related, I recently upgraded to the latest kernel (19) and my Ubuntu install won't load due to the SATA drivers not loading I believe, I am dumped to BusyBox with the error "ALERT! /dev/sbd1 does not exist".

I've tried booting to the kernal version 14 and 17, both receive the same error.  Having loaded off a LiveCD the Ubuntu filesystem is all there and working.  I have never needed to add any none generic drivers to the installation to get the SATA drives to work, please not the drives are two 500gb in RAID.

Anyone got any ideas as to how I can solve the problem?

---

### Post by foresthill on 2010-02-08
The bios on my notebook has an option to change the hard drive mode from SATA to PATA, I believe. You might go into your bios and look for something like that.

Can you boot into recovery mode, or not at all?

---

### Post by Pelgar on 2010-02-08
P.Forest said:
> Many thanks Pelgar for the linx, which led to many more treasures!You're very welcome P.Forest! Glad the links were helpful.

wojox said:
> Pelgar scroll down to " Keep in sync with kernel updates ". This will keep your drivers from borking up on kernel updates. I used that same HowTo.Wow, I remember looking that over when I originally installed my drivers but had forgotten about it. I didn't implement it at the time because it was pretty old, 2008, and sdennie the author of "**HOWTO: Automatically update manually installed NVidia drivers after kernel updates"** at [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) said "(Note: This has only been tested on 8.04 and may not work or be needed in later versions). So I decided to wait and see if it was needed. I guess it is!!!

achandler said:
> Although not fully related, I recently upgraded to the latest kernel (19) and my Ubuntu install won't load due to the SATA drivers not loadingI really wish I could help you but about the only thing I can think of is try booting from that Live CD and see if it still sees your drives.
Don't get me wrong, you're welcome in this post but you will probably get a lot more help if you start a new post.

---

### Post by achandler on 2010-02-09
I've solved my problem after a few hours reading up on the changes the latest kernel has made.  One of them was to change the grub2 loader from looking for a UUID to /sbd1/ etc which in my case meant it refused to find the HDDs and load.  I fixed the problem using a Live CD and mounting the drive correcting the grub setup.

---

### Post by Pelgar on 2010-02-09
achandler, glad you worked it out. Where did you find the info on kernel changes?

---

### Post by achandler on 2010-02-10
After spending a few hours seraching my problem, I was taken to the official bug board and there was a link there.  Im sorry I cannot help you anymore then that but I have been to so many forums etc over the last few days that I cannot remember the correct one.

---

### Post by Pelgar on 2010-02-10
achandler, no problem I'll probably stumble across it someday like you did.

Just as I started to reply to this message Update Manager popped itself up on my desk top again. I'm not sure if I want to allow it to do its thing or not!!!

---

