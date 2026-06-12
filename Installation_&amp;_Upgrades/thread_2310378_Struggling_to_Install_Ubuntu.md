---
title: "Struggling to Install Ubuntu"
date: 2016-01-18
forum: Installation &amp; Upgrades
---

### Post by Michael_Galindo on 2016-01-18
Hello, all. I'm another newb here struggling to install Ubuntu. I finally decided to ask for help.

I'm using the standard ISO for 14.04.3 LTS (desktop, 32-bit, from ubuntu.com/download/desktop) on this system:
Mobo: BIOSTAR G31D-M7,
CPU: Intel Core 2 Duo CPU E4500 2.2Ghz,
GPU: NVIDIA GeForce GT 720

Is there any fundamental reason Ubuntu won't work with my system? Should I give up?


To sum up my agonizing history:
Failure 1: I tried to a liveUSB, but I got stuck at the login screen (tried: Ubuntu/[blank], ubuntu/[blank], ubuntu/ubuntu, ubuntu/password, etc...)
In the end, I had to try another route.

Failure 2: So, I re-downloaded the ISO and burned a DVD. Success! I got into the installer and everything worked beautifully. :-)
I partitioned the drive with a primary ext4 and 2 swap spaces, ~4GB each, and installed.
Install finished. I restarted the computer, and I got nothing but a message from a BIOS-Flasher Utility telling me it found no valid BIOS.

Failure 3: I started over, booted up the DVD, re-partitioned the drive and re-installed, and re-started.
At first, it was working! The computer started booting linux from the drive. But, the graphics were unusable. I had half the screen flickering with the UI "squished" into the bottom of the screen, although the mouse traversed the whole screen and I could never be quite sure where a click would land... I tried updating the graphics driver from the terminal and the system froze.
After rebooting, I was dropped into a black screen. Switching to the terminal showed a single, blinking underscore which did not respond to keystrokes.
All subsequent reboots showed the same problem, even after adding "nomodeset" to the kernel commands.

Attempt 4: I have booted up the DVD, re-partitioned the drive, and the installer is currently running.
Am I doing something horribly wrong?
Should I give up?

Thanks in advance for any advice or help. I'd really like this to work, but I'll accept defeat if someone knows that my system doesn't support Ubuntu.

Edit: Specifically, I expect the same graphics problems. The graphics work great with the installer (DVD). Is there any way to make the installed version use the same graphics settings as the installer, at least initially? (I'm much more familiar with GUIs than with command lines.)

---

### Post by grahammechanical on 2016-01-18
> Is there any way to make the installed version use the same graphics settings as the installer?

Yes. Do not tick the box "Install third party software" Ticking that box will bring in some free but proprietary video and audio codecs and a proprietary video driver. If we do not tick that box we get the open source video driver that is used during the Ubuntu live session.

We can install the audio and video codecs later by installing Ubuntu Restricted Extras from the Software Centre. We can change/activate video drivers from System Settings>Software & Updates>Additional Drivers tab. We need to be connected to the internet & to allow time for the utility to find the drivers.

> I tried to a liveUSB, but I got stuck at the login screen

What login screen? The live session should not have a login screen. After we install during which we set a user name and password then when we start/load Ubuntu we get to a login screen where we put in our password.

> I partitioned the drive with a primary ext4 and 2 swap spaces, ~4GB each, and installed.

Why 2 swap partitions? Ubuntu only needs one. And why not use the Erase disk and install Ubuntu option and let the installer do all the work with partitions.

> I restarted the computer, and I got nothing but a message from a BIOS-Flasher Utility telling me it found no valid BIOS.


Restarting the computer after installing Ubuntu does not enter the BIOS set up utility. Did you enter the BIOS set up utility and select an option to flash the BIOS?

> Am I doing something horribly wrong?

I think that you are doing things that you do not need to do. If Ubuntu is to be the only OS on this machine then use the Erase disk and install Ubuntu option. Otherwise, please explain what other OS are on the machine.

Regards

---

### Post by Michael_Galindo on 2016-01-18
Thank you! If this install fails, I will not check that box next time.

LiveUSB / login screen:
I know there shouldn't be a login screen. That's all I could gather from similar questions around the web. Nevertheless, there it was.

2 Swaps:
I used 2 swap partitions because some tutorial said to. I've read so much I probably couldn't find it again.

Bios Flasher:
No, I definitely did not select a BIOS flasher utility; I know how to navigate the BIOS. I did plenty of research and could find no reasonable explanation for the flasher's sudden and repeated appearance, so I re-installed.

OS on the Machine:
There is only 1 OS on this USB drive to which I am installing, although there is an HDD in the machine with Windows 10 / a lot of data on it.
I did not use the Erase disk feature for fear of accidentally erasing my Windows installation.

However, I am not necessarily dual booting. Both the USB drive and the HDD have independent boot loaders, and I just use the BIOS' boot menu to point it at one drive or the other.
If Linux works I will begin migrating everything over to it and see how the programs respond / how it affects my workflow. (I could not test these things from the live version, unless the liveUSB had worked.)

However, the install is almost finished. I will update soon.

The installation has finished beautifully! :-) I did everything exactly as in "Failure 3", but this time it worked perfectly.

For some mysterious reason, it defaulted to the Nouveau driver even though that "3rd party software" box was checked; that must be why the GUI is usable.
So, now I have a GUI, but: no acceleration, and only 1 monitor. (I need at least 3 for my work). (Edit: Also, the installer could manage 3 monitors using Nouveau. What's up with that? It's the same driver now in the install, but Ubuntu only detects 1.)

I am switching to nvidia-352 now; so I might accidentally ruin my beautiful installation. Still, I need a graphics card. My hopes are high at this point!

Well, that solved everything. Apparently, 4th time's a charm.
I did nothing differently. But, the Nouveau driver let me use the GUI, and from there I switched to the proprietary nvidia driver, then restarted lightdm from the terminal and all is well. I now have 3 monitors and 3d acceleration. I still can't get the VGA monitor to its native resolution, but I'm researching it.

Thanks for your help identifying the driver issue; I was really close to giving up.

---

