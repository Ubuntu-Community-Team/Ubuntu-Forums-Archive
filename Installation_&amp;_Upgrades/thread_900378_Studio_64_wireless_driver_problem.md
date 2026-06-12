---
title: "Studio 64 wireless driver problem"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-08-25
Ubuntu 64 Studio installed smoothly. No internet access on wireless network. Followed suggestions on installing Ndiswrapper to install drivers that I found after some searching. Cannot get Ndiswrapper to install. Synaptics asks for Ubuntu disk to be put in the drive. Disk is in but it tells me the volume cannot be mounted, but when going to Computer it is being read and can be accessed there. I am stuck! The Ndiswrapper package is not on the UbuntuStudio 64 disk so I use the Ubuntu 64 disk where I do find the files buried in a "pool" sub-directory. Is it the disk ID that Synaptics wants to see that is preventing the disk from being recognized using Synaptics? Both the Studio 64 and regular 64 disks were iso burns and otherwise work just fine. Should I install the Ubuntu 64 first then install Studio over that? I figure that the needed package file would install during over-all installation. I may be wrong!

How can I install the necessary files for Ndiswrapper from the CD to the computer so that it can be loaded from Synaptics and used? Where (which directory) would the package be placed on the computer for installation to work? Could I manually copy from CD to computer directory? I tried something similar but when accessing the files I am asked to insert Ubuntu CD. That takes us back to my first paragraph. It is a circle!

ADDED: I thought about looking at the "inf" file to see the path for the package. Seems that I was looking at one where I say the CD path give for each piece of the package. I do not know if that is being read from the package that I copied from the CD or not. If so, that would make sense with the need to read the CD. If that is what I find I may try to edit the inf to point to the actual directory where the files reside. Does that sound logical?

---

### Post by Thelasko on 2008-08-25
> Should I install the Ubuntu 64 first then install Studio over that?
I generally recommend that, but since you are this far I would leave it alone.

I would download ndiswrapper from [here]("http://packages.ubuntu.com/hardy/ndiswrapper-common"), and [here]("http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9"), and load it on a flash drive to move it over.  Plugging you machine in via a CAT5 until you get your wifi card working will really help you out.  You will be able to install software much faster.

---

### Post by 73ckn797 on 2008-08-25
I may have to install one over the other. The box is at the other end of the house and the CAT5 cable may be bad. I have that connected now but cannot get anything to work on it either. I pinged several router addresses. Some work some don't.

I assume the "loopback" setting, which seems to be the default, is the one the system recognized? I set it for Ethernet but it tells me it is not present.

I figure that if I install Ubuntu 8.04 64 bit first, then I will have the needed files available to install the driver.

I have downloaded the files directly from Ubuntu repository on one computer, copied to a flash drive, copied onto the other computer already.

The instructions that I have may not be correct because they are expecting the NDIS to be on the CD. My first posts addressed that issue.

If I have the needed 3 packages, downloaded from Ubuntu in the home directory on the computer, what commands will be needed to install?

I have been entering:

sudo apt-get install /home/documents/ndiswrapper-common_1.50-1ubuntu1_all.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 

Same results for all 3 packages.

Any suggestions?

---

### Post by Thelasko on 2008-08-25
> I assume the "loopback" setting, which seems to be the default, is the one the system recognized? I set it for Ethernet but it tells me it is not present.
Don't mess with "loopback" that's not what you wanted to setup.  I don't know what's wrong with your network, mine just worked.

> I figure that if I install Ubuntu 8.04 64 bit first, then I will have the needed files available to install the driver.
The CD doesn't have every package.  In fact, it has very few of them.  The repositories have more packages than that disk.  Therefore, reinstalling Ubuntu isn't likely to solve your problem.

> If I have the needed 3 packages, downloaded from Ubuntu in the home directory on the computer, what commands will be needed to install?
Just double click them.

Edit:
> I tried something similar but when accessing the files I am asked to insert Ubuntu CD.
Ah, I know your problem.  [This is the solution.]("https://help.ubuntu.com/community/Repositories/Ubuntu#Disable%20the%20CD-ROM%20Repository")

---

### Post by 73ckn797 on 2008-08-25
I will try that and let you know.

---

### Post by 73ckn797 on 2008-08-25
Partial success.

Ndiswrapper is installed. What would be the correct command to load the driver?

I have the original install CD and copied the contents to a new directory (per instructions I have, though not for this exact wifi card, which may be the problem). "/home/micah/WMP54G/Drivers/WMP54Gv4.1"

The card is actually WMP54G v4.5 according to the label on the card but the driver disk only has the Rt5400 and Rt61 driver directories.

In terminal I cd to the directory where the driver files are at.

The instructions I have states to enter,
"sudo ndiswrapper -i Rt61.inf" I also typed the path on other attempts.

It returns an unknown file or directory and also states not found in "/usr/sbin/ndiswrapper 1.9 line 219". Does that mean that the driver is not included in ndis? Is there something I must do to accomplish that? Or, should I look for another driver?

I have found some generic drivers available on the web. Should I try one of those? Do you have a suggestion?

---

### Post by 73ckn797 on 2008-08-25
When I installed Studio 64 bit Hardy, the on-board LAN was disabled, through BIOS and not connected to a cable. If I re-install with it on and connected will the cabled connection then work? I am sure that there is a command that would activate it but do not know what that would be.

---

### Post by 73ckn797 on 2008-08-25
I may have found the solution to my wireless issue within these forums. 
I will do the recommendations from the following post: 

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

I have already downloaded the driver file from the Ralink site from their Linux pages.

I just takes time to find the right answer after spending time figuring out the right questions!

---

### Post by Thelasko on 2008-08-26
> **73ckn797 said:**
> When I installed Studio 64 bit Hardy, the on-board LAN was disabled, through BIOS and not connected to a cable. If I re-install with it on and connected will the cabled connection then work? I am sure that there is a command that would activate it but do not know what that would be.

I'm sure there is a command too, but I always just restart my machine.  That usually does the trick.

---

### Post by 73ckn797 on 2008-08-26
I have restarted the system many times with the cable connected. I even used another cable. I am talking about a cable routed from my office in the basement, up the stairs, down the hall and into the room to the other computer. I have another cable more installed but ran the loose cable as a process of elimination step. I tried it with the wireless card removed, installed and turned off from within Studio settings trying to make the cabled connection work. Not wasted time but time spent discovering what does not work!!! OH WELL, remember Thomas Edison.

When I boot with the regular Ubuntu Hardy CD the wireless works. See my new post under hardware.

---

### Post by 73ckn797 on 2008-08-26
Finally got the on-board LAN to work. Must be one of those things where you have to walk away for a while to clear the mind, rest the computer, then attack the problem again.

---

### Post by falcon61102 on 2008-08-26
Are you still trying to get ndiswrapper to work?

Once you download the driver, make sure you extract the contents to a folder, either on your desktop or home folder is recommended because of the ease of access.  Once you've extracted the files to a folder, open a terminal and navigate to that folder using "cd".  That seems to work better than including the path name when doing the install.

---

### Post by 73ckn797 on 2008-08-26
After getting the wired connection working I have stopped pursuing the wireless solution for the time being. I will get back to that later. Once I get one issue resolved another surfaces. Now that I have been able to connect and get updates I find that the video card is the infamous ATI brand with it/s own set of problems. This is my son's computer. I have nVidia and no problems.

I have been now searching for how to get that working as designed.

---

### Post by falcon61102 on 2008-08-26
Got to love nVidia.  Had some problems with ATI way back in the day and have never used them since.

You having trouble installing the drivers or getting them to work correctly once installed?

---

### Post by 73ckn797 on 2008-08-26
I have not installed the recommended drivers to try to correct the issue. The card is running on the standard driver.

---

### Post by falcon61102 on 2008-08-26
One thing you may want to try is Envyng.  It will install the drivers for you.  You can find it in the Synaptic Package manager.

---

### Post by 73ckn797 on 2008-08-27
Will that get the best driver that would allow full graphics functioning?

---

### Post by falcon61102 on 2008-08-27
It will get install a thoroughly tested and commonly used driver.  It just takes a preset driver from the manufacture and installs it for you.  I use Envyng for my nvidia card and it works great.

---

### Post by 73ckn797 on 2008-08-27
Well the Envyng did not help at all. When restarting Studio will not load. It goes to a "not in range" display. I can run recovery and use the reconfigure x-server and system will boot but still have no extended graphic capability.

Might work well with nVidia but remember we are dealing with ATI.

The trek goes on to the land where all is right for ATI.

---

### Post by 73ckn797 on 2008-08-27
I will close this discussion for the time being. The cabled connection works so I will not do something that will foul that up. At least for the time being.

OPPS! INCORRECT FORUM DISCUSSION SUBJECT!

---

### Post by 73ckn797 on 2008-08-27
The previous "SOLVED" posting was incorrect.

---

### Post by Thelasko on 2008-08-27
> **73ckn797 said:**
> The previous "SOLVED" posting was incorrect.

But you can still access the internet with your wired connection, right?

---

### Post by 73ckn797 on 2008-08-27
> **Thelasko said:**
> But you can still access the internet with your wired connection, right?

Yes and flawlessly at that. Why keep using up my day?

---

