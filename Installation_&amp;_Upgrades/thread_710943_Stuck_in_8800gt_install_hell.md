---
title: "Stuck in 8800gt install hell"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by todd.ian on 2008-02-29
I'm trying to install ubuntu on an AMD system, A8N-E motherboard, 4200+ processor, 2gb ram, with a couple of hd's and an 8800GT. I found some instructions on a forum here, can't remember the link but here they are:


1). Install Ubuntu using the Alternate CD. When installed, make absolutely no changes at all to anything in Ubuntu, especially to do with the screen or graphics driver. This can kill the Xserver setup and you can loose the GUI.
( After completing the drivers installation I discovered that if you install the Nvidia drivers before you update a new installation it breaks the drivers and they no longer boot up. I had to re-install the drivers. It may be better to update the new installation before installing the drivers. This would include Automatix too I would assume. As well, updates to the kernel break the drivers installation it seems, and so have to re-install the drivers when-ever this happens. )

2). When Ubuntu starts, go to the Nvidia website and download the drivers.
[http://www.nvidia.com/object/linux_display_ia32_169.09.html](http://www.nvidia.com/object/linux_display_ia32_169.09.html)

Best to put this file in the root of your Home directory - easier to find later.
I also downloaded the X Config utility from the same page. I unzipped it, but did nothing more with it. This was also put in the Home directory with the drivers installation file. I have no idea if its actually needed, but have included it here as it was one of the things I did.

3). Use Synaptic to find and install the libc6-dev libraries. I could not install the Nvidia drivers without these.

4). Hit CRTL + ALT + F1 to go to command prompt.

5). Close down the Xserver to kill the GUI - "sudo /etc/init.d/gdm stop".

6). Verify the GUI has been shut down using CRTL + ALT + F7. If you see a blank black screen then the GUI has been successfully shut down. Use CRTL + ALT + F1 to return to the command prompt.

7). Log in as root user - "sudo -i". You need to be root user to install the Nvidia drivers.

8. Change directory to root - "cd /". I don't know why, but I had to do this to get to my home directory.

9). Change directory to where you have downloaded the Nvidia drivers install file eg "cd home/username"

10). Install the Nvidia drivers by typing - "sh NVIDIA-Linux-x86-169.09-pkg1.run"
The install program should then start. Just say Yes to everything, including at the end when it asks if you would like the installer to configure the Xserver for you to allow the Nvidia drivers to be loaded at bootup.

11). When the installation was completed, I then followed Orlon's advice to type in "sudo modprobe nvidia". This did not appear to actually do anything. At least not that I noticed.

12). Next, type "startx" to start up the GUI again. If the installation was successful, you should see a Nvidia logo appear as the GUI is starting.

13). Finally, reboot the PC, and hopefully everything should be fine.


Sadly, my computer won't recognize the alternate disc as a boot disc. Yes, I've changed the boot order in the BIOS but it just boots straight through to XP. I've had this problem before with windows boot discs and nobody's been able to give me any advice about it.

Otherwise, I've tried using the live CD and it won't even come close to installing Ubuntu. Either it hangs on "running boot scripts" and never gets to the GUI, or it hangs on Busybox when I boot the computer.

I've installed windows about 4 times on this computer and I've never had nearly this much trouble. Is Ubuntu always this hard??

---

### Post by Bad_Byte on 2008-02-29
I would dare to say that most of the time its smooth sailing but binary video drivers and wifi is still tricky.

Step 11 tells linux to load the nvida driver incase it haven't done so already.

If you add the word nosplash to the livecd boot option and take note where it stalls and (it will output lots of text during boot) and tell us at the forums where it hangs.

---

### Post by aparabola on 2008-03-02
I too have a 8800GT, and I am looking to install the driver on my Linux OS. On the other side, I have Vista. Sorry to hear of your troubles. For me, Fedora was giving me fits so i put off the Linux Fedora install after several failed attempts. I never really hit the forums hard, i just figured it shouldn't be so difficult to get an OS on my box. I was right, because last night I installed Ubuntu and i swear to bejesus that it was the most simplest PC task I have ever performed. I am using Ubuntu now while writing this (sorry don't mean to rub it in) The point I am making is that these forums are a gold mine in themselves along with select other Google related searches to yield information. Don't give up man. Think about the trail you have left. I am here, I need to install the 8800GT as well, so I am right behind. I need to know how the story ends man. Come back, and tell us you got Ubuntu installed on your rig!

---

