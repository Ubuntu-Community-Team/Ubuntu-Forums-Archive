---
title: "black screen and grub issues"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by rangedenemy on 2014-01-11
I've been trying to dual boot ubuntu 13.10 on my laptop with windows 8. I have found this tutorial: [https://coderwall.com/p/ydbldg](https://coderwall.com/p/ydbldg) to solve the issue I have been having with a black screen on installation after the grub page. I can get to the grub editor by hitting e, but once there I seem to be incapable of exiting and booting using either f10 or ctrl-c. Has anyone else had similar issues?

---

### Post by tfrue on 2014-01-12
Yes, a lot of people on these forums have.

Did you do the boot-repair part? Try that because that's what I was going to suggest you do first.

---

### Post by rangedenemy on 2014-01-12
I have tried that yes, however whenever I do so I receive an error telling me that sudo is not a valid command. If I remove sudo I get a command that add-apt-repository is not valid, and if I get rid of that there's really no point anyway

---

### Post by ubfan1 on 2014-01-12
Did you try Ctrl-x instead of the ctrl-c to boot the edited grub commands?

---

### Post by rangedenemy on 2014-01-12
I've gotten the original issue now, turns out my f keys are all multifunction, which I really should have realized earlier. Now however I am having trouble installing the boot repair, as the terminal in grub refuses to recognize basic commands as valid.

---

### Post by Bashing-om on 2014-01-12
rangedenemy; Hi !

Insure that your keyboard is properly configured :
[http://www.howtoforge.com/changing-language-and-keyboard-layout-on-various-linux-distributions](http://www.howtoforge.com/changing-language-and-keyboard-layout-on-various-linux-distributions)
If problems continue, we will look at authorization and permissions for you as the "user".

What I think
[INDENT][INDENT]and my little bit to help
[/INDENT][/INDENT]

---

### Post by tfrue on 2014-01-12
While reading over the link you posted again, it's terrible. For one, you would want to see the Window's partition when you are installing Ubuntu, and I don't know why she edited the boot script. You may need to re-install grub,

It's possible that you installed grub on the BIOS/MBR partition rather than the UEFI/GPT partition that Win 8 uses, which is bad. You can live boot [LinuxSecureRemix]("https://help.ubuntu.com/community/LinuxSecureRemix") and have boot-repair available without downloading it.

Also, when you live boot, type:```

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
``` 
to see if you booted BIOS or UEFI which will help us troubleshoot your problems.

Thanks,
Chris

---

### Post by rangedenemy on 2014-01-12
so I tried doing a live boot from there, but experienced the same issue as before, essentially once I leave grub the screen just goes black and stays that way. I managed to get through that issue with the instructions posted above, but now I can't boot without getting to a black screen again.

---

### Post by Bashing-om on 2014-01-12
rangedenemy; Progress ?

Can you now edit the grub boot parameter ?
If you are using Nvidia or ATI graphics cards, perhaps "nomodeset" boot parameter (or other) may help;
See:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

A black screen is often a graphics driver issue.

[INDENT][INDENT]where there are solutions there are no problems 
[/INDENT][/INDENT]

---

### Post by rangedenemy on 2014-01-12
I've got an i7 core with intel 4400 graphics card. I tried to modify the parameters the same way I did the first time, to get ubuntu to install. Using the parameters from the tutorial I managed to boot into a live boot version, which seemed to work just fine. However when I tried to get to boot-repair from the terminal there the repository wasn't found. Do I need internet access to get to boot repair? Because there do not seem to be wifi drivers for my laptop atm, and I do not have an ethernet port

---

### Post by Bashing-om on 2014-01-12
rangedenemy; Well ;

Yeah, in order to obtain "boot-repair" one has to use the internet. The tool is not available by default.
Many times drivers for wifi must be installed after the installation is completed. To get those drivers without the internet is a real pain - and beyond my paygrade - but, can be done [ d/l the driver on another computer, transfer the driver to usb thumb drive, copy to the install, and then one may install the driver]

However, even to do that one must be able to boot the system.
What procedure are you applying now to attempt to boot the installed system ?

[INDENT][INDENT]try'n to help
[/INDENT][/INDENT]

---

### Post by rangedenemy on 2014-01-12
I really appreciate the help. Right now I am sort of at a stuck point. My overall goal is to get the boot repair tool, as the instructions I followed to get this far have that as the next step. I've figured out that I can do that through a live boot. However it seems the only wifi drivers I have available are for 12.04, so I think I'm going to have to downgrade at the moment. So ideally once that is done I can transfer over the wifi drivers and get everything running for real. In the meantime I have a perfectly good installation of windows, so I have no urgent need for ubuntu, I just prefer it's environment for work.

---

### Post by Bashing-om on 2014-01-12
rangedenemy; True,

One can download and install boot-repair from the live boot, there is a huge thread on it use here on the forum.

Holler back at us, as you have the need. Like I said, getting WIFI up and working without 'net connection is a real bear, but can be done.

[INDENT][INDENT]best wishes
[/INDENT][/INDENT]

---

### Post by tfrue on 2014-01-12
Yes, you need internet connection when doing "*sudo apt-get install*" commands. And that sucks, I didn't know computers were made without them...So are you able to hop onto a different computer with internet, download LinuxRescueRemix and use [unetbootin]("http://unetbootin.sourceforge.net/") to install the .iso to USB or CD? The LinuxRescueRemix comes with boot-repair installed so no internet connection would be required on the laptop but you would need to post the URL.

---

