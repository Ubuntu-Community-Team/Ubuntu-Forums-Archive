---
title: "Issues with 11.04 Install"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by UnderPar on 2011-07-15
After cleaning up my son's Vista desktop and backing it up, I installed 11.04 alongside Vista.  

**Issue #1:**

Using the [Ubuntu Requirements Guide]("https://help.ubuntu.com/community/Installation/SystemRequirements"), which says a minimum of 5GB is needed, I went ahead and allocated 15GB, to be safe and allow for future growth.  But when it boots, I get this message:

[INDENT]This Computer has only 244.6 MB of disk space remaining
[/INDENT]
Ubuntu confirms that the installation took up 13+GB of space.  Why is this, and how do I correct it?  I would be fine with deleting the partition and starting over, but do not want to damage his Vista installation.

I don't understand why these space requirements aren't explained better or even consistent between different official Ubuntu sources.  [Here's one]("https://help.ubuntu.com/11.04/installation-guide/i386/memory-disk-requirements.html") for 11.04 that specifies that *"You must have at least 44MB of memory and 500MB of hard disk space to perform a normal installation."*  Now, 'normal installation' implies to me that everything is installed, so I don't get it.


**Issue #2:**

When I turn on the computer or reboot, I get this floating box:

[INDENT]Monitor Is Working
92.5khz 58hz
Out Of Scan Range
Change PC Setting
[/INDENT]
This does not disappear until it has booted Ubuntu, so I do not get any menu to choose between Ubuntu and Vista.  Why is this and what's the fix?


**Issue #3:**

When I plug in his USB Wireless device, the device does not light up, there is no popup box in Ubuntu, and the device does not show up in the Wireless Settings box.  How do I get Ubuntu to see this device (or any newly plugged in device) so that it can look for the appropriate driver?


Thank you for any help you can offer!

---

### Post by dFlyer on 2011-07-15
Is this a wubi install?

---

### Post by rickytikki on 2011-07-15
Couple of questions. 1. how did you install ubuntu within vista or did you use the bootloader option. 2. how much hard drive space does your son have and what percent is free. 3. have you tried the updating the grub2 loader sudo update-grub. 4. can you start windows in safemode and reinstall the mbr (caution as this will delete the grub loader.)

---

### Post by rickytikki on 2011-07-15
do you have to wait atleast ten seconds with this . 
Monitor Is Working
92.5khz 58hz
Out Of Scan Range
Change PC Setting
it may be because the grub resolution doesnt match up with the pc screen so the screen technically isnt working. I think this is the prob. next ime you start up the pc when it gets past the bios screen hit the down button 4 time and hit enter to see if you boot into windows.

---

### Post by UnderPar on 2011-07-15
> **dFlyer said:**
> Is this a wubi install?
No, sir.  I installed alongside Vista, as I stated in my first sentence.  :)

---

### Post by UnderPar on 2011-07-15
> **rickytikki said:**
> Couple of questions. 1. how did you install ubuntu within vista or did you use the bootloader option. 2. how much hard drive space does your son have and what percent is free. 3. have you tried the updating the grub2 loader sudo update-grub. 4. can you start windows in safemode and reinstall the mbr (caution as this will delete the grub loader.)


#1 - no.

#2 - he had around 90 GB of free space. ([eMachines ET1161-05]("http://emachines.com/products/products.html?prod=ET1161-05") - 160 GB hard drive, Vista taking around 40GB, and a hidden partition for re-installation)

#3 - I'm sorry - I don't speak Linux....yet!  ;)

---

### Post by UnderPar on 2011-07-15
> **rickytikki said:**
> do you have to wait atleast ten seconds with this . 
Monitor Is Working
92.5khz 58hz
Out Of Scan Range
Change PC Setting
it may be because the grub resolution doesnt match up with the pc screen so the screen technically isnt working. I think this is the prob. **next ime you start up the pc when it gets past the bios screen hit the down button 4 time and hit enter to see if you boot into windows.**


Just did that, and apparently that gets you into the eMachines Recovery Management (hidden partition), which btw has a ghosted-out 'recover' option, leaving only the exit option.


Edit to add:  I tried 5 'downs' and it did a check disk, then tried to reboot, so I did 5 'downs again, and Vista has loaded.  I will leave it at the login screen until I get home.

---

### Post by UnderPar on 2011-07-15
I have to leave for work very soon, so I will check this thread for more replies when I get home.

Thank you for your help!  My son will be very upset if I've screwed up his computer (he's only 10).

---

### Post by rickytikki on 2011-07-15
your fine you wont mess up his computer now when the grub loader loads it loads somethin like this
Ubunut linux
ubuntu linux recovery
Windows vista 
emachine recovery recovery 

You must find which one is the right option for windows or you must set the right resolution to your screen so you can see teh grub loader
 
To set the desired resolution in /etc/default/grub
Change the value of GRUB_GFXMODE= (Example: GRUB_GFXMODE=800x600)
If unsure of what resolutions are available to GRUB 2 they can be displayed by typing vbeinfo in the GRUB 2 command line. The command line is accessed by typing "c" when the main GRUB 2 menu screen is displayed.

---

### Post by rickytikki on 2011-07-15
try this link [http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

---

### Post by UnderPar on 2011-07-16
> **rickytikki said:**
> your fine you wont mess up his computer now when the grub loader loads it loads somethin like this
Ubunut linux
ubuntu linux recovery
Windows vista 
emachine recovery recovery 

I *wish *I got that screen, but I'm not.  It stays on that monitor warning until it briefly goes to the BIOS splash page, then to a black screen with 'Boot CD' for a second, then it proceeds to boot Ubuntu.  No menu. (There is no CD in the drive)

> You must find which one is the right option for windows or **you must set the right resolution to your screen** so you can see teh grub loaderBut that can't be done on a 17" CRT monitor, AFAIK.  Do I set it in Ubuntu, then reboot?  It works fine in Windows - it's an eMachine monitor that came with the computer.
 
> To set the desired resolution in /etc/default/grub
Change the value of GRUB_GFXMODE= (Example: GRUB_GFXMODE=800x600)
If unsure of what resolutions are available to GRUB 2 they can be displayed by typing vbeinfo in the GRUB 2 command line. The command line is accessed by typing "c" when the main GRUB 2 menu screen is displayed.This is currently way over my head.  I'm just not that familiar with Ubuntu/Linux nomenclature.  I get what you are saying, but I just have no clue where to start to follow those instructions.  I'm a newby.

What's with the 13GB install size, anyway?

Can I delete the Ubuntu partition, through [Windows]("http://download.cnet.com/1770-20_4-0.html?query=partition+software&platformSelect=Windows&tag=srch&searchtype=downloads&filterName=platform%3DWindows&filter=platform%3DWindows") or Ubuntu and start over?

---

### Post by UnderPar on 2011-07-16
Can I delete the Ubuntu partition, through [Windows]("http://download.cnet.com/1770-20_4-0.html?query=partition+software&platformSelect=Windows&tag=srch&searchtype=downloads&filterName=platform%3DWindows&filter=platform%3DWindows") or Ubuntu and start over?

---

### Post by dino99 on 2011-07-16
standard install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by UnderPar on 2011-07-16
> **dino99 said:**
> standard install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)


Thanks for the reply, but I'm not sure what you are trying to tell me.  I do not understand the Linux-speak, but I clicked the link.  Are you saying to use that partition program to....what?  Resize the Ubuntu partition to make it larger?  To delete it so I can start over?

Since I want to keep the Vista side intact, wouldn't it make more sense to delete the Ubuntu partition from within Windows?


I'm still hoping someone can tackle the fact that:


[LIST]
[*]I'm not getting an OS menu at startup.
[*]Why the Wireless USB Adapter is totally ignored when it's plugged in.
[*]Why the install took up 13GB, when Ubuntu states that only 5GB is required.
[/LIST]

In any event, I have about 6 hours until my son returns from vacation, so I would love to just get his machine back to an easy Vista boot, and figure out the Ubuntu stuff in the coming week.  Getting the OS menu to show up would at least solve that.

---

### Post by dino99 on 2011-07-16
the link above is for the "needs" & the "howto".

Always tweak partitions when they are not used, always; so boot on livecd (like partedmagic) to do it.

If you want/need to resize the windoz partitions, use its tools (defrag first then shrink)

---

### Post by UnderPar on 2011-07-16
> **dino99 said:**
> the link above is for the "needs" & the "howto".

Always tweak partitions when they are not used, always; so boot on livecd (like partedmagic) to do it.

If you want/need to resize the windoz partitions, use its tools (defrag first then shrink)
Yes.  The priority right now is not resizing the partition.  I have plenty of free drive space and can fix that later.

The priority is getting a boot menu so that my son can get into Vista and play his Minecraft and Flyff and all his Windows games.

---

### Post by bcbc on 2011-07-16
A standard install takes about 2.6GB (in my experience). So no idea why you have 13GB used.

What are the full specs of the machine... model number, graphics card etc. If nothing else the graphics card type will probably help.

Note that Grub (Ubuntu's bootloader) does a lousy job distinguishing between windows recovery and the actual windows. you can normally tell by checking which partition has the boot flag set. And then you can customize grub so that it names it appropriately. e.g. there is something call grub customizer: [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by bcbc on 2011-07-16
PS check your disk space usage... by running the "disk usage analyzer" (otherwise known as baobab). It's best to run it as the root (superuser) - so hit the Windows key and enter "gksu baobab", then enter your password and let it run.

This will give you a good idea where those extra GB are sitting. Report back on what you find.

---

### Post by UnderPar on 2011-07-16
> **bcbc said:**
> A standard install takes about 2.6GB (in my experience). So no idea why you have 13GB used.

What are the full specs of the machine... model number, graphics card etc. If nothing else the graphics card type will probably help.

Note that Grub (Ubuntu's bootloader) does a lousy job distinguishing between windows recovery and the actual windows. you can normally tell by checking which partition has the boot flag set. And then you can customize grub so that it names it appropriately. e.g. there is something call grub customizer: [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

> **bcbc said:**
> PS check your disk space usage... by running the "disk usage analyzer" (otherwise known as baobab). It's best to run it as the root (superuser) - so hit the Windows key and enter "gksu baobab", then enter your password and let it run.

This will give you a good idea where those extra GB are sitting. Report back on what you find.


Thank you for taking the time.

I listed the model in [post #6]("http://ubuntuforums.org/showpost.php?p=11051744&postcount=6").  It's an [eMachines ET1161-05]("http://emachines.com/products/products.html?prod=ET1161-05") which the website says contains an NVIDIA® GeForce® 6150SE integrated graphics. Up to 128MB of shared video memory.

I just hooked up a 25" HDTV to it, and no longer get the floating monitor warning, so that's good.


As for the install size, etc., it's best that I deal with that later.  **Right now, I am most concerned with getting an OS menu to show up, so that he can get into Vista.**

---

### Post by bcbc on 2011-07-16
> **UnderPar said:**
> Thank you for taking the time.

I listed the model in [post #6]("http://ubuntuforums.org/showpost.php?p=11051744&postcount=6").  It's an [eMachines ET1161-05]("http://emachines.com/products/products.html?prod=ET1161-05") which the website says contains an NVIDIA® GeForce® 6150SE integrated graphics. Up to 128MB of shared video memory.

I just hooked up a 25" HDTV to it, and no longer get the floating monitor warning, so that's good.


As for the install size, etc., it's best that I deal with that later.  **Right now, I am most concerned with getting an OS menu to show up, so that he can get into Vista.**

If you just want to 'make it look like it was before' - then you can restore the Windows bootloader. Then it will boot straight into Windows as before. (You'll need to reinstall grub later if you want to boot Ubuntu).

To do this insert a windows dvd and boot to a repair prompt and run: bootrec /fixmbr

---

### Post by bcbc on 2011-07-16
Not sure whether you've gone with the windows bootloader... but what I've tried is to set the GRUB_GFXMODE to text. On my setup this removed the 'graphical' grub menu and replaced it with the low resolution text.

To do this:
Go to a terminal (CTRL+ALT+t) or hit Windows key and enter "terminal".
Edit the /etc/default/grub file as root:
```
gksu gedit /etc/default/grub
```
Enter your password when prompted:
Change the line starting GRUB_GFXMODE= to
```
GRUB_GFXMODE=text
```
Save and exit. Still in terminal run:
```
sudo update-grub
``` to regenerate the grub menu. Then reboot to try it:
```
sudo reboot
```

---

### Post by UnderPar on 2011-07-16
> **bcbc said:**
> Not sure whether you've gone with the windows bootloader... but what I've tried is to set the GRUB_GFXMODE to text. On my setup this removed the 'graphical' grub menu and replaced it with the low resolution text.

To do this:
Go to a terminal (CTRL+ALT+t) or hit Windows key and enter "terminal".
Edit the /etc/default/grub file as root:
```
gksu gedit /etc/default/grub
```
Enter your password when prompted:
Change the line starting GRUB_GFXMODE= to
```
GRUB_GFXMODE=text
```
Save and exit. Still in terminal run:
```
sudo update-grub
``` to regenerate the grub menu. Then reboot to try it:
```
sudo reboot
```
I am assuming that when you say Grub Menu, you are talking about the menu at first boot that lets you decide whether you want to boot into Ubuntu or Window.

Yes - that is what is missing.  Nobody has been able to tell me why this is missing.  I switched my 15 year old daughter's computer 4 years ago to a dual-boot WinXP/Ubuntu (Jackalope?) and never had any problems with the boot menu, the wireless USB, or monitor.  It went so smoothly, I figured that 4 years of progress would make it even more trouble-free, but no.  Now, the only time she boots into Windows is to sync her iPod to iTunes.

I will attempt to figure out your instructions, and try them.  Thanks.

---

