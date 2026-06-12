---
title: "Video not recognized - running in basic mode"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2014-03-20
I tried to replace my XP installation with Ubuntu.  At first, I tried the 'run on CD' mode and everything worked just fine.  I was able to view my attached discs and all that.  There were NO video problems either.

When I left the CD in and rebooted, I chose to completely replace my XP with Ubuntu and the installation progressed.  There were no warning messages or the like and when instructed I removed the CD and rebooted.  After an (apparently) normal startup, it took a couple of minutes before a box appeared telling me that my video was unrecognized and I would have to run in basic mode.  My mouse was gone, but hitting 'Enter' apparently worked.  The next screen had four radio buttons on it.  But, with no mouse, I was unable to check any of the buttons at all.  The top one remained illuminated though, so I hit the 'Enter' key again.  Nothing happened.  My keyboard was unresponsive to anything at all including Ctrl-Alt-Del.  I had to hold down the power switch to reboot.

Every time I rebooted, I got the same sequence of events.  With the CD back in the drive, I was able to navigate through the 'run on CD' options easily, but still cannot install or run Ubuntu.

Without opening up the computer I couldn't tell you what motherboard I have.  The video is the on-board video and I *think *it is possibly Trio-based.  Is there some command I can enter into a terminal (under 'run from CD') that will give me what Ubuntu thinks is my configuration?

I am using the Ubuntu 12.04 (32-bit) CD version of installer.

Any ideas?

Bill

---

### Post by ajgreeny on 2014-03-20
As this is an XP machine I imagine it is fairly old and not likely to be able to run Ubuntu with unity very effectively.  You might do better using Xubuntu, and may find that it will give you a much better graphic output.

Do you have any idea at all of what the hardware is, eg the cpu, ram and graphic card in the machine?  If you honestly have no idea, boot to your current ubuntu install and once at the login screen hit Ctrl+Alt+F1 to get to a command line interface where you can login with your username and password, the latter of which will not show on screen but will still work.

Once logged in run **sudo apt-get update** and then **sudo apt-get upgrade** which might even solve your problems and let you login to the GUI.
So having updated, use Ctrl+Alt+F7 to get to the GUI login screen and see what happens; you may be lucky.

It would really help to see what hardware you have, even a model number and any clues from case stickers etc etc, but if that is not possible and the GUI is still not working you could go back to the command line interface again with Ctrl+Alt+F1 and from there run **sudo lshw | less** which will allow you, hopefully, to scroll the output of the command up and down using the cursor keys and thus find what your graphic card and other hardware really is.

---

### Post by grahammechanical on 2014-03-20
May I make a couple of suggestions? When we install Ubuntu we can tick to install third party software. Among other things that option will install a proprietary video driver. And the proprietary video driver might be what is causing the problem.

When Ubuntu is the only operating system on the hard disk then we do not see a boot menu (Grub) but it is there. So,

1) Hold down shift when the machine is booting.
2) When the Grub boot menu appears select Recovery Mode
3) At the Recovery menu select Resume

That will load Ubuntu without using the proprietary video driver. If you get to a working desktop then you can use the Additional Drivers utility to install/activate another video driver. The open source video driver is called Nouveau. You may also see three or four proprietary video drivers on offer. Experiment. It is Nouveau that is used when we run the Ubuntu Try session.

Oh, by the way, that fail safe mode that you had difficulty with does not work for me either. I consider it to be broken.

Regards.

---

### Post by WB0HYQ on 2014-03-20
@**graham**[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")mechanical:  I didn't check the box for 3rd party software.  In fact, I didn't check anything for the initial install.

@ajgreeny:  I've printed out your response and will attempt what you've outlined.  I have another video card (the one that was originally in the machine) and it is a NVIDIA GeForce 7600GS with 512Mb onboard RAM.  I took it out when I changed monitors because my current monitor was connected to my KVM and was used with four other computers.  So I relegated the computer down to the basement and an older LED monitor.  But that is neither here nor there.  I'll give your steps a try and report back.  It might not be until much later, however.  Maybe tomorrow in the morning.

Thanks for the responses.

Bill

---

### Post by WB0HYQ on 2014-03-21
Well, here are the results, and they aren't very good:

motherboard is a VIA Tech KM400-8235
BIOS is Phoenix, but dated 2003 (very old)
CPU is Athlon XP2800 @ 2.3gHZ (Socket A)

The results of the lshw command shows "display UNCLAIMED", but it is a VIA Tech, VGA compatible, KM400/KN400/P4M800, and [S3 UniChrome] and is listed as compatible pm agp agt2.0 vga_controller bus_master cap_list.

When I boot off the HD, I get the "purple" screen with the 4 marching dots and Ubuntu but then it clears and the monitor displays "Check video cable" and that's it.  I can't do a thing more.

If I run off the CD, everything works perfectly but once I try the HD, it goes away and dies.

Bill

---

### Post by WB0HYQ on 2014-03-21
An update to my last update.

After hacking around for a couple of hours, I am now running off the HD perfectly.  I had a few false starts such as the screen going blank a couple of times, but I eventually managed to insert the NVIDIA card I mentioned previously and get it running at a decent resolution.  All updates have been completed and the system seems to be in tip-top shape.

My thanks to ajgreeny for pointing me in the right direction.  Once I determined just what I was dealing with hardware-wise, it was then a matter of finding the right drivers and installed them.  I can even print from this computer to my network printer (something I couldn't do under XP for some reason).

Bill

---

